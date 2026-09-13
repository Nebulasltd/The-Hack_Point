# Fraud-Detection Signal vs. Adversary-Controlled Features

## The core question

A fraud/risk-scoring model can have excellent offline metrics (AUC, precision/recall) and still be a weak control in production, if too much of its predictive power comes from features the adversary can directly set or fake. The question that actually determines robustness isn't "how accurate is the model" — it's:

> **How much of the model's detection signal comes from features an adversary can control, versus features they can't observe or can't fake?**

A fraudster doesn't need to defeat the model mathematically. If the model leans heavily on controllable inputs, the fraudster just needs to move those specific values into the "looks legitimate" region while their underlying intent stays fraudulent — no adversarial-ML expertise required, just trial and error against the production system (or a few purchased "carding" guides). This is a well-documented real-world attack pattern in banking/payments fraud detection research, not a theoretical concern — see References below.

## Feature taxonomy: controllable → constrained → non-controllable

Classify every feature in the model along a spectrum of how directly an adversary can set its value:

| Class | Definition | Typical examples (card-not-present / online banking fraud) |
|---|---|---|
| **Fully controllable** | The attacker directly supplies this value, or it's a direct, unconstrained function of what they supply | Transaction amount, timestamp/time-of-day, stated billing name/address on the form, free-text fields |
| **Constrained/semi-controllable** | The attacker can influence this, but with cost, friction, or limits (infrastructure needed, has to match other stolen data, degrades with effort) | Device fingerprint (spoofable with anti-detect browsers/emulators, but takes tooling), IP/ASN/geolocation (changeable via VPN/proxy/residential proxy, but each hop costs money and can itself become a signal), recipient account/IBAN (constrained by needing a money-mule account that matches), browser/OS headers |
| **Non-controllable** | Computed server-side from data the attacker cannot see or cannot retroactively alter, or reflects ground truth outside their reach | Aggregated historical behavior for the account (avg. transaction size over 90 days, typical time-of-day pattern), velocity features computed from the account's own true past transactions, cross-account/cross-device graph features (shared device or IP with accounts already flagged fraudulent), internal risk scores from other systems, tenure/account age, behavioral biometrics (keystroke/mouse dynamics, hard to replicate consistently) |

This is the same distinction used in the banking-fraud adversarial ML literature under the label **"editable vs. non-editable features"** (Carminati et al., *Evasion Attacks against Banking Fraud Detection Systems*, USENIX RAID 2020) — that paper found that of the raw transaction fields, only **amount and timestamp** were fully attacker-controllable in their studied system, while IBAN/recipient, IP/ASN, and session ID were constrained by infrastructure the attacker had to actually acquire, and aggregated behavioral features were effectively out of reach entirely.

## Why "constrained" isn't "safe"

Don't treat semi-controllable features as equivalent to non-controllable ones. An attacker with budget and motivation routinely defeats device-fingerprint and IP-based signals at scale (anti-detect browsers, residential proxy networks, SIM farms). Rank features within the constrained tier by **real-world cost to the attacker to manipulate at scale**, not just theoretical mutability — a feature that costs $0.01/attempt to spoof via a commodity proxy service is functionally closer to "controllable" than to "non-controllable," regardless of which bucket it looks like it belongs in on paper.

## How to actually measure the split

Don't stop at classifying features qualitatively — quantify how much of the model's power each class contributes.

### 1. Feature importance decomposition

Run permutation importance or SHAP values on the trained model, then sum the importance scores by controllability class instead of just ranking individual features.

```python
import shap

explainer = shap.TreeExplainer(model)  # or the appropriate explainer for your model type
shap_values = explainer.shap_values(X_test)

# feature_class: dict mapping feature name -> "controllable" | "constrained" | "non_controllable"
import numpy as np
importance_by_feature = np.abs(shap_values).mean(axis=0)
class_totals = {}
for feat, imp in zip(X_test.columns, importance_by_feature):
    cls = feature_class[feat]
    class_totals[cls] = class_totals.get(cls, 0) + imp

total = sum(class_totals.values())
for cls, imp in class_totals.items():
    print(f"{cls}: {imp/total:.1%} of total feature importance")
```

Report this split to whoever owns model risk — "62% of this model's decision signal comes from fully or semi-controllable features" is a finding, in the same sense a pentest finding is a finding, and belongs in a model risk assessment.

### 2. Ablation study (ground-truth check)

Feature importance can be misleading (correlated features split credit). The more decisive test: train a variant of the model using **only the non-controllable features**, and compare its performance to the full model.

- If the non-controllable-only model retains most of the AUC/PR-AUC of the full model → the model's real strength is robust and doesn't depend on features an adversary can move.
- If performance collapses without the controllable features → the model's apparent accuracy is largely an artifact of features that will stop working the moment attackers realize what's being scored (or already know, if the scoring logic has ever leaked, been reverse-engineered by probing, or is inferable from declined-transaction feedback).

### 3. Evasion simulation (adversarial evaluation)

Take a set of known-fraudulent, correctly-caught transactions from your test set. For each, simulate an adversary who can freely alter only the controllable and constrained features within realistic bounds — plausible amount ranges, any timestamp, a spoofed but plausible device fingerprint, a proxy-sourced IP in a "normal" geography — while leaving the non-controllable features (computed from actual account history) unchanged. Re-score each simulated case and measure the **evasion rate**: what fraction now fall below the decision threshold.

```
evasion_rate = (# originally-flagged cases that evade after realistic perturbation) / (# originally-flagged cases)
```

A high evasion rate under only-realistic, only-attacker-controllable perturbation is the clearest possible demonstration that the model is over-reliant on the wrong feature class — more convincing to stakeholders than an importance chart, because it's a direct proof-of-concept.

### 4. Production monitoring

Track score sensitivity to controllable-feature changes on an ongoing basis, not just at model-build time:

- Run synthetic/canary transactions that vary only controllable features and watch how much the score swings — a large swing from a small, cheap-to-fake change is a live warning sign, not just a historical one.
- Monitor for **distributional drift specifically in controllable features** among transactions near the decision threshold — fraudsters adapting to the current model will show up here first, often before overall fraud-loss metrics move.

## Mitigation strategies

- **Shift feature engineering toward the non-controllable end of the spectrum.** Prioritize aggregated historical behavior (this account's own transaction pattern over time), velocity computed server-side from ground truth, and graph/network features (device, IP, or payee shared with other known-fraud accounts) that the attacker has no visibility into and no way to directly set.
- **Make "controllable" features harder to control cheaply**, rather than only harder to control perfectly — e.g., score device-fingerprint *stability/consistency for this account over time* rather than the raw fingerprint value alone; a spoofed fingerprint is easy to generate once but hard to make look consistent with the account's genuine history.
- **Adversarial training** — augment training data with plausible adversarial perturbations of the controllable/constrained features (informed by the evasion simulation above) so the model is explicitly trained not to be fooled by the cheap moves an attacker will actually try.
- **Layer server-side velocity/rule checks alongside the ML score** — rules operating on ground-truth, non-editable aggregates (e.g., "more than N transactions from this account in the past hour") provide a control that doesn't depend on the ML model's feature weighting at all, and fails differently than the model does (defense in depth).
- **Treat the model like any other security control and red-team it periodically** — see [`../ai-security/README.md`](README.md) for general AI/ML attack tooling; apply the evasion-simulation methodology above on a recurring cadence as new fraud patterns and attacker tooling emerge, not just once at model launch.
- **Restrict what an attacker can learn about the scoring logic** — minimize information leakage through decline reasons, response timing, or granular error messages that could let an attacker infer which features (and which values) are driving their score, since that information turns "constrained" features into effectively "controllable" ones once discovered.

## Worked example: classifying a typical e-commerce fraud model's features

| Feature | Class | Notes |
|---|---|---|
| Transaction amount | Controllable | Attacker sets this directly |
| Time of day / day of week | Controllable | Attacker chooses when to transact |
| Billing address entered on form | Controllable | Free text, attacker-supplied |
| Card BIN / issuing bank | Constrained | Fixed once a specific stolen card is chosen, but attacker chooses which card to use |
| Device fingerprint | Constrained | Spoofable with anti-detect browser tooling, but takes effort/cost per attempt |
| IP address / ASN / geolocation | Constrained | Changeable via VPN/proxy, each hop has a cost and can itself be flagged |
| Email domain age / reputation | Constrained | Attacker can register a new email cheaply, but a fresh-domain signal is itself informative |
| Shipping address match to billing | Constrained | Attacker can enter a matching fake shipping address, but real fraud often needs a different drop address |
| Account age (if account-based) | Non-controllable | Reflects genuine history, can't be retroactively created |
| Avg. transaction size, this account, trailing 90 days | Non-controllable | Computed server-side from real history |
| Velocity: transactions from this account in past 1h/24h | Non-controllable | Ground truth, not attacker-visible or settable |
| Device/IP shared with accounts already flagged fraudulent (graph feature) | Non-controllable | Attacker has no visibility into the graph |
| Keystroke/mouse dynamics (behavioral biometrics) | Non-controllable (high cost to fake) | Technically emulatable, but expensive and imperfect at scale |

In this example, if a model's top SHAP features turn out to be dominated by amount, time-of-day, and device fingerprint — with the account-history and graph features barely contributing — that's a strong, specific, defensible model-risk finding, and the ablation/evasion tests above are how you prove it rather than just asserting it.

## References

- Carminati, M. et al., ["Evasion Attacks against Banking Fraud Detection Systems"](https://www.usenix.org/system/files/raid20-carminati.pdf), USENIX RAID 2020 — the primary source for the editable/non-editable feature framework and the finding that amount and timestamp are typically the only fully attacker-controllable raw transaction fields.
- ["Adversarial Learning in Real-World Fraud Detection: Challenges and Perspectives"](https://arxiv.org/abs/2307.01390), arXiv 2307.01390 — survey confirming this remains an open research area, with a similar controllable/non-controllable framing applied to aggregated behavioral features.
- [MITRE ATLAS](https://atlas.mitre.org/) — for cataloging this and related ML attack techniques using a shared taxonomy when writing up findings.
- [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — "Input Manipulation Attack" (ML01) covers this attack class at a general level.

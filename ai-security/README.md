# AI / ML Security

"Dealing with AI" from a security standpoint splits into two directions, and this module covers both:

1. **AI as a target** — attacking and red-teaming AI/ML systems (prompt injection, jailbreaking, model extraction, adversarial examples, data poisoning). Relevant when an engagement's scope includes an AI-powered feature or an LLM-backed application.
2. **AI as a defensive control** — building ML systems (like a fraud-detection model) that hold up against an adversary who knows the model exists and is actively trying to evade it. This is the less-discussed side, and the one most directly relevant to a fintech/SACCOS context: a fraud model is a security control, and like any control it needs to be assessed for how easily an adversary can defeat it.

## Deep dive: feature-controllability robustness in fraud detection

[`fraud-detection-feature-robustness.md`](fraud-detection-feature-robustness.md) — a full breakdown of a specific, high-value question for any fraud/risk-scoring model: **how much of the model's detection signal comes from features an adversary can directly control, versus features they can't see or fake?** A model that scores well in backtesting but derives most of its power from easily-spoofed inputs (transaction amount, timestamp, a device fingerprint an attacker can emulate) is far weaker in production than one leaning on aggregated, historical, or graph-based features the attacker has no visibility into. Covers the feature taxonomy, how to actually measure the split (ablation studies, importance decomposition, evasion simulation), and mitigation strategies.

## Attacking / red-teaming AI systems

- [MITRE ATLAS](https://atlas.mitre.org/) — adversary tactics/techniques knowledge base for AI systems, the ATT&CK-equivalent for ML.
- [OWASP Top 10 for LLM Applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/) — prompt injection, insecure output handling, training data poisoning, model theft, and more, for LLM-backed apps.
- [OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/) — the equivalent list for traditional ML systems (input manipulation, data poisoning, model inversion, membership inference, model theft).
- [garak](https://github.com/leondz/garak) — LLM vulnerability scanner; probes for prompt injection, jailbreaks, data leakage, hallucination, and more.
- [PyRIT](https://github.com/Azure/PyRIT) (Microsoft) — Python Risk Identification Tool for generative AI red teaming.
- [Counterfit](https://github.com/Azure/counterfit) (Microsoft) — automation layer for assessing the security of ML models, covering both traditional ML and generative AI attack techniques.
- [Adversarial Robustness Toolbox (ART)](https://github.com/Trusted-AI/adversarial-robustness-toolbox) — IBM's library for evasion, poisoning, extraction, and inference attacks/defenses across ML frameworks.
- [CleverHans](https://github.com/cleverhans-lab/cleverhans) / [Foolbox](https://github.com/bethgelab/foolbox) — adversarial example generation libraries, mainly for image/tabular model evasion research.

## Core concepts (attacking AI)

- **Prompt injection** — malicious instructions embedded in content an LLM processes (a document, a web page, a tool result) that override or subvert the system's intended behavior. Direct (user types it) vs. indirect (it arrives via retrieved/fetched content).
- **Jailbreaking** — techniques to bypass an LLM's safety/alignment training to elicit disallowed output.
- **Model extraction/stealing** — querying a model repeatedly to reconstruct a functionally equivalent copy, or to reverse-engineer training data/architecture.
- **Membership inference** — determining whether a specific record was part of a model's training data (a privacy attack).
- **Data poisoning** — corrupting training data so the resulting model behaves incorrectly (backdoors) or is generally degraded.
- **Evasion attacks** — crafting input at inference time (adversarial examples) that causes misclassification without touching training data — this is the attack class most relevant to the fraud-detection deep dive above: a fraudster performing manual evasion by tuning the features they control is doing an evasion attack, just without needing gradients/white-box access.

## Key exam/engagement tips

- Not every AI security question is about LLMs — a classic fraud/credit-risk/anti-abuse ML model is just as much an attack surface, and it's the one most likely to show up in a fintech engagement.
- When assessing an ML-based control, ask "what does the adversary need to change, and can they actually change it?" before trusting an accuracy/AUC number in isolation — see the deep dive for the full methodology.

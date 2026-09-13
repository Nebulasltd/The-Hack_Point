# Secure AI Development Checklist

A phase-by-phase checklist for designing or reviewing a system that builds on AI — an LLM app, a RAG pipeline, an agent, or a traditional ML model. Pair with [`attack-techniques.md`](attack-techniques.md) (what you're defending against) and [`detection-and-defense.md`](detection-and-defense.md) (the full rationale behind each item). Not exhaustive, and not a compliance artifact by itself — use it to structure a design review or a pre-deployment assessment.

## Design phase

- [ ] Threat-modeled the system against this module's attack categories (or MITRE ATLAS directly) *before* building, not after — identified which of §1–14 in `attack-techniques.md` actually apply to this system's architecture.
- [ ] Decided, explicitly, what data sources the model/agent will have access to, and what the *most* sensitive thing reachable through it is — assume any of that data can eventually be surfaced to any user who can reach the model.
- [ ] For agents: defined the minimum tool set the task requires, with each tool scoped to a specific narrow action rather than broad account/API access (attack-techniques §4).
- [ ] Identified every action the system can take that has a real-world side effect (send, delete, pay, modify a permission, execute code) and classified which require human confirmation.
- [ ] Decided where instructions (system prompt) are architecturally separated from data the model processes (retrieved content, user uploads, tool output).

## Data phase

- [ ] Identified every source that feeds training data, fine-tuning data, or a RAG index, and classified each by whether an external party can influence its content (attack-techniques §6, §7).
- [ ] Established access control *at the retrieval/data layer* for any multi-tenant or permission-scoped system — not "the prompt tells it not to share this."
- [ ] Set up integrity checks / versioning / hashing for training and fine-tuning datasets.
- [ ] Confirmed no raw secrets, credentials, or unredacted PII are present in any dataset, document store, or system prompt used by the system.
- [ ] For sensitive/regulated training data: assessed membership-inference and model-inversion exposure (attack-techniques §9), not just "is the raw data stored securely."

## Model phase

- [ ] Verified provenance of any pretrained/third-party model or checkpoint used; scanned or avoided unsafe deserialization formats (attack-techniques §12).
- [ ] Ran red-team testing against the model/pipeline (garak, PyRIT, ART, or manual technique-by-technique testing against `attack-techniques.md`) before deployment, not only after an incident.
- [ ] For ML systems used as a security/risk control (fraud, abuse, credit): assessed how much detection signal comes from adversary-controllable features — see [`../ai-security/fraud-detection-feature-robustness.md`](../ai-security/fraud-detection-feature-robustness.md) for the full methodology.
- [ ] Documented the model in a model/system card: intended use, known limitations, training data provenance, evaluation results.
- [ ] Established a rollback path to a known-good prior model version.

## Integration / application phase

- [ ] All model output that reaches a browser, database, shell, or deserializer is validated/encoded exactly like any other untrusted input (attack-techniques §3).
- [ ] Actions the model/agent can trigger are constrained to a validated schema (structured output / typed function calls) rather than parsed from free text.
- [ ] Input and output guardrails in place: injection/jailbreak screening, PII/secrets redaction, content filtering.
- [ ] Rate limiting and quota enforcement configured per user/key, tuned against expected legitimate usage (attack-techniques §11).
- [ ] Verified the system prompt contains no secrets or access-control logic that would matter if leaked (attack-techniques §5).
- [ ] Any code-execution tool available to the system runs sandboxed, with no access to production credentials or systems.

## Deployment phase

- [ ] Logging covers prompts, retrieved context, tool calls, and outputs — sufficient to reconstruct what the model actually saw during an incident investigation.
- [ ] Canary tokens or equivalent placed where extraction/leakage would be a high-impact event.
- [ ] AI-system alerts are wired into the existing SOC/SIEM/incident-response pipeline, not a disconnected parallel stack.
- [ ] IR runbook updated to cover this system: how to revoke/rotate the tool credentials it uses, how to roll back its model version, how to identify and purge poisoned stored context (conversation history, RAG documents).

## Ongoing / monitoring phase

- [ ] Behavioral drift monitoring in place for the deployed model's output distribution and key metrics.
- [ ] Retrieval patterns (for RAG) periodically audited for signs of index poisoning.
- [ ] Query patterns periodically reviewed for signs of systematic extraction/probing.
- [ ] Dependencies (including ML-specific packages) covered by ongoing SCA/dependency scanning; package names verified against the real registry before adoption when originally suggested by an AI coding assistant (attack-techniques §14).
- [ ] Re-run red-team testing on a cadence (not just at initial launch) and after any material change to the model, prompt, tools, or data sources.

## For AI-assisted development specifically (even when the shipped product has no AI at runtime)

- [ ] Code suggested by an AI assistant is reviewed with the same scrutiny as code from a junior contributor, not accepted on the basis of fluency/confidence alone.
- [ ] Any new package name introduced via an AI suggestion is verified against the actual public registry before install.
- [ ] No secrets or credentials are pasted into AI coding-assistant prompts/context where retention or logging policy is unclear.

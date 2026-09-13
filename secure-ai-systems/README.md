# Secure AI Systems — Detecting & Protecting Systems Built With AI

A defender/builder-focused module: how to secure a system that has AI baked into it — an LLM-backed app, a RAG pipeline, an autonomous agent, a traditional ML model, or a product whose code was itself AI-generated. Companion to [`ai-security/`](../ai-security/README.md), which is written from the attacker's/red-teamer's side (offensive tooling, adversarial ML theory). This module is written from the builder's side: **you know these systems can be attacked — here's how to detect that it's happening and design so it matters less when it does.**

## Scope: what counts as an "AI-built system" here

- **LLM-integrated applications** — chatbots, copilots, and any app where an LLM sits in the request path (including RAG: retrieval-augmented generation over your own documents/data).
- **Agentic systems** — LLMs given tools/function-calling, the ability to browse, execute code, call APIs, or take multi-step autonomous action.
- **Traditional ML systems** — classifiers, scoring/ranking models, anomaly detectors (fraud, credit risk, content moderation) — narrower attack surface than LLM apps but no less critical when the model *is* the security control.
- **AI-assisted development** — code generated or substantially shaped by an AI coding assistant, which carries its own distinct risk class (see Attack Techniques §14).
- **The supporting infrastructure** — model weights, fine-tuning/training pipelines, vector stores, prompt/context stores, and the MLOps tooling that moves data and models through that pipeline.

## Module contents

- [`attack-techniques.md`](attack-techniques.md) — how each of the above actually gets attacked: mechanism, real-world example, and impact, organized by category (prompt injection, insecure output handling, excessive agency, poisoning, extraction, privacy attacks, evasion, DoS, supply chain, AI-generated-code risk).
- [`detection-and-defense.md`](detection-and-defense.md) — the protection playbook: architectural controls, input/output guardrails, monitoring and detection signals, secure MLOps practices, governance frameworks, and what's different about incident response when the compromised component is a model or an agent.
- [`secure-development-checklist.md`](secure-development-checklist.md) — a phase-by-phase (design → data → model → integration → deployment → monitoring) checklist to run an AI-integrated system build or review against.

## Why a separate module from `ai-security/`

`ai-security/` covers red-teaming AI systems as an engagement activity and a deep dive on fraud-model robustness — useful when you're the one attacking or assessing someone else's model. This module is the inverse: you're building or operating the system, and the question isn't "how do I break this" but "what do I need in place so that when someone tries, I notice, and it doesn't matter as much." The two are meant to be read together — attack-techniques.md here is deliberately more implementation-focused (specific to LLM apps, agents, and RAG) than the more research/red-team-oriented "Core concepts" list in the AI/ML Security module.

## Standards and frameworks referenced throughout

- **[OWASP Top 10 for LLM Applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/)** — the primary risk taxonomy for LLM-integrated apps; both other files in this module map directly onto it.
- **[OWASP Machine Learning Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/)** — the equivalent for traditional ML systems.
- **[OWASP Agentic AI — Threats and Mitigations](https://genai.owasp.org/)** — emerging guidance specific to autonomous/multi-step agents (tool misuse, goal hijacking, multi-agent collusion).
- **[MITRE ATLAS](https://atlas.mitre.org/)** — adversary tactics/techniques for AI systems, the ATT&CK-equivalent for ML; useful for structuring detection engineering the same way ATT&CK structures it for traditional IT.
- **[NIST AI Risk Management Framework (AI RMF 1.0)](https://www.nist.gov/itl/ai-risk-management-framework)** — Govern / Map / Measure / Manage: the standard structure for an organizational AI risk program, referenced in `detection-and-defense.md`.
- **[NIST AI 100-2e2025: Adversarial Machine Learning](https://csrc.nist.gov/pubs/ai/100/2/e2025/final)** — taxonomy and terminology for evasion, poisoning, privacy, and abuse attacks; the closest thing to an authoritative glossary for this module's attack-techniques file.
- **[ISO/IEC 42001](https://www.iso.org/standard/81230.html)** — management-system standard for AI, the AI-specific analogue to ISO 27001.
- **[Google Secure AI Framework (SAIF)](https://safety.google/cybersecurity-advancements/saif/)** — vendor framework covering the same ground (secure-by-default AI infrastructure, detection, automation) from a practitioner angle.

## Notes

Track your own architecture reviews, model-risk assessments, or AI-system incident write-ups in [`notes/secure-ai-systems/`](../notes/secure-ai-systems/).

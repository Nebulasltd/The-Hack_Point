# Detecting and Defending AI-Built Systems

The protection playbook, organized so each section maps back onto the attack categories in [`attack-techniques.md`](attack-techniques.md). Read those two files together — this file is deliberately structured around "what do I put in place" rather than repeating the attack mechanics.

## 1. Architecture-level controls (the highest-leverage layer)

These reduce *impact* even when an attack technique succeeds — the most important category, because prompt injection specifically has no complete technical fix, so the system has to be designed to fail safely.

- **Least-privilege tool scoping for agents** — the direct mitigation for Excessive Agency (attack-techniques §4). Don't give an agent one broad "email account access" credential; give it narrow, purpose-built tools ("draft a reply, do not send," "read this thread only," "propose a calendar event"). Scope each tool's permissions to exactly what the task needs, not what might be convenient later.
- **Segregate instructions from data** — architecturally separate the system prompt/instructions channel from untrusted content the model processes (retrieved documents, tool outputs, user-uploaded files). Some model APIs now support structural separation (distinct system/tool/user roles enforced at the API level); where available, use it rather than concatenating everything into one prompt string. This doesn't eliminate indirect prompt injection but narrows the attack surface.
- **Human-in-the-loop for high-risk actions** — any agent action with real-world side effects above a defined risk threshold (sending an email/message externally, making a payment, deleting data, changing a permission, executing code against production) requires explicit human confirmation, not just a "the model decided to" audit log after the fact.
- **Sandbox code execution** — if an agent can execute code (a "code interpreter" tool, or the ability to run shell commands), run it in an isolated, resource-limited, network-restricted sandbox with no access to secrets or production systems, full stop.
- **Output encoding and validation before downstream use** — treat LLM output exactly like any other untrusted user input before it reaches a browser, a database, a shell, or a deserializer: HTML-encode before rendering, use parameterized queries, validate against a strict output schema (see Structured output below) rather than free text wherever the output feeds a system that takes action.
- **Enforce access control at the data layer, not the prompt layer** — for RAG/multi-tenant systems, apply authorization filters *before* retrieval (query the vector store with the user's actual permission scope), never rely on instructing the model "don't share Tenant B's data" as the control.
- **Structured output / function-calling schemas** — constrain model output to a validated schema (JSON schema, typed function-call arguments) wherever the output drives an action, rather than parsing free text. This makes injected instructions far less likely to translate into an unintended tool call.

## 2. Input/output guardrails

- **Prompt-injection and jailbreak classifiers** — a lightweight model or rules layer that screens inbound user/retrieved content for known injection patterns before it reaches the primary model, and screens outbound responses before they're returned or acted on. Not a complete defense (evasion of classifiers is itself an active research area), but raises attacker cost and catches unsophisticated attempts.
- **Content filtering** — both directions: block disallowed categories in input (jailbreak attempts, policy-violating requests) and in output (PII leakage, secrets, disallowed content the model was tricked into producing).
- **PII/secrets redaction** — automatic scanning of model output (and of context assembled for RAG/prompts) for patterns matching credentials, API keys, government ID formats, card numbers, before the response leaves the system or before a document enters the index.
- **Rate limiting and quota enforcement** — the direct mitigation for Unbounded Consumption (attack-techniques §11): per-user and per-API-key limits on request volume, token generation length, and context size, tuned to legitimate usage patterns.
- **System prompts should not contain secrets** — treat this as a hard rule, not a guideline, given how routinely system prompts leak (attack-techniques §5). Any credential or business-logic decision an attacker could exploit by reading the prompt belongs in actual access-controlled backend logic, not in text handed to the model.

## 3. Monitoring and detection signals

- **Full logging of prompts, retrieved context, tool calls, and outputs** — you cannot investigate a suspected prompt-injection incident after the fact without the actual context the model saw at the time; log it (with appropriate retention/privacy handling) the same way you'd log requests to any other security-relevant service.
- **Anomaly detection on query patterns** — unusually systematic, high-volume, or structured querying is a signal for model-extraction attempts (attack-techniques §8) or automated jailbreak/injection probing, the same way port-scan-shaped traffic is a signal in traditional network monitoring.
- **Canary tokens / honeytokens** — plant unique, traceable strings in system prompts or documents that should never legitimately be returned to a user; a canary appearing in output is a strong signal of a successful extraction or leakage attempt (extends the well-established honeytoken pattern from traditional DLP/IR into the AI context).
- **Behavioral drift monitoring for deployed models** — track a model's output distribution, confidence calibration, and key performance metrics over time in production, not just at initial evaluation; a sudden shift can indicate data drift, an emerging attack pattern (e.g., coordinated evasion against a fraud model), or a poisoned update.
- **Retrieval monitoring for RAG systems** — log and periodically audit what gets retrieved for which queries; unexpected documents surfacing for unrelated queries is a signal of index poisoning (attack-techniques §7).
- **Tie AI-system alerts into existing SOC/SIEM workflows** — don't build a parallel, disconnected monitoring stack; an AI-system security event (e.g., a blocked injection attempt, an anomalous extraction pattern) should reach the same detection/response pipeline as any other application security alert.

## 4. Secure MLOps and supply chain

- **Model and dataset provenance** — know where every model checkpoint and training/fine-tuning dataset came from; treat a downloaded pretrained model with the same supply-chain scrutiny as a third-party software dependency, not as inert data.
- **Safe deserialization** — prefer [safetensors](https://github.com/huggingface/safetensors) or equivalent formats that cannot execute code on load over pickle-based checkpoints (`.pkl`, and unrestricted `.pt`); if pickle-based formats must be used, only load them from sources you fully trust and control, and scan them.
- **Dependency scanning for the ML stack specifically** — standard SCA/dependency-scanning tooling should cover Python ML packages the same as any other dependency; also verify package names against the actual published registry before installing anything an AI coding assistant suggested (mitigates attack-techniques §14's dependency hallucination risk).
- **Dataset integrity checks and versioning** — hash and version training/fine-tuning datasets; if a dataset is sourced from anywhere attacker-reachable (scraped web content, public forums, user-submitted data), review or filter it before it's used for training, and be able to answer "which dataset version produced this model" during an incident.
- **Red-team before deployment, not just after** — run the attack techniques in this module's companion file (or use `ai-security/`'s tooling — garak, PyRIT, ART, MITRE ATLAS-structured testing) against a system before it ships, as a release gate, not only in response to an incident.
- **Model cards / system cards** — document each deployed model's intended use, known limitations, training data provenance, and evaluation results; this is both a governance artifact (see below) and a practical incident-response aid (you need to already know what the model is *supposed* to do to recognize when it isn't).

## 5. Governance frameworks (how this fits into an organizational program)

- **[NIST AI RMF](https://www.nist.gov/itl/ai-risk-management-framework)** — structures an AI risk program around four functions: **Govern** (policy, accountability, culture), **Map** (identify context and risks for a specific AI system — essentially the threat-modeling step this module's attack-techniques file feeds into), **Measure** (analyze and track risks, including the detection signals above), **Manage** (respond to and prioritize identified risks). Useful as the organizing structure for turning this module into an actual program rather than a one-off checklist.
- **[ISO/IEC 42001](https://www.iso.org/standard/81230.html)** — the certifiable management-system standard for AI, analogous to how ISO 27001 formalizes an information-security management system; relevant if the organization needs to demonstrate a formal AI governance program to clients, regulators, or auditors.
- **[Google SAIF](https://safety.google/cybersecurity-advancements/saif/)** — a practitioner-oriented framework covering secure-by-default AI infrastructure, extending detection/response to AI-specific threats, and automating defenses; a useful cross-check against the controls above from a large-scale operator's perspective.
- **Map every deployed AI system against [MITRE ATLAS](https://atlas.mitre.org/)** the way a mature SOC maps its detection coverage against ATT&CK — identify which tactics/techniques you have monitoring/mitigation for and which are gaps, rather than treating "AI security" as one undifferentiated risk.

## 6. Incident response — what's different for AI systems

- **Capture the full context, not just the final output** — an IR investigation into a suspected prompt-injection or jailbreak incident needs the actual retrieved documents, tool calls, and intermediate reasoning/context the model had access to at the time, not just the user-visible response; this only works if the logging in §3 was already in place before the incident.
- **Have a rollback path for models, not just code** — be able to revert to a known-good model version/checkpoint the same way you'd roll back a bad code deploy; this requires the versioning discipline in §4 to already exist.
- **Revoke and rotate tool credentials, not just user accounts** — if an agent's tool access was abused via prompt injection, the compromised principal is the *tool credential/API key the agent used*, which may be a service account with no obvious link to the specific user session that triggered the abuse; IR playbooks need to account for this indirection.
- **Distinguish a model behaving as designed-but-exploited from a model that is actually compromised** (e.g., via data poisoning of a fine-tune) — the response differs: the former needs better guardrails/scoping around an otherwise-fine model, the latter needs the model itself pulled and re-derived from a known-clean checkpoint and dataset.
- **Assume indirect injection payloads may persist in stored context** — a RAG document, a conversation history, or a memory store that retains an injected instruction can re-trigger the same attack on future, unrelated sessions until the poisoned content is actually located and removed, not just blocked at the point it was first observed.

---

Continue to [`secure-development-checklist.md`](secure-development-checklist.md) for a practical, phase-by-phase checklist that applies the controls above to a specific build or review.

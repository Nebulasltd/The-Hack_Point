# Domain 1: Security and Risk Management (16%)

The foundation domain — governance, law, ethics, and risk. Heaviest-weighted domain on the exam; expect broad conceptual coverage rather than deep technical detail.

## 1.1 CIA Triad and security concepts

- **Confidentiality** — preventing unauthorized disclosure of information. Controls: encryption, access control, classification.
- **Integrity** — preventing unauthorized modification; ensuring data is accurate and trustworthy. Controls: hashing, digital signatures, change control, input validation.
- **Availability** — ensuring authorized users have timely, reliable access. Controls: redundancy, fault tolerance, DR/BC planning, patching (paradoxically, patching trades short-term availability for long-term availability/integrity).
- Extended models add **Authenticity**, **Non-repudiation** (can't deny having performed an action — supported by digital signatures, logging), and **Accountability** (actions traceable to a specific subject).
- **AAA framework**: Authentication, Authorization, Accounting (sometimes Auditing).

## 1.2 Security governance

- **Alignment with business strategy** — security exists to enable the business, not obstruct it. Security program goals must map to organizational objectives.
- **Organizational structures**: centralized vs. decentralized security functions; security steering committees.
- **Due care** (the standard of "prudent person" doing what's reasonable to prevent harm) vs. **due diligence** (the ongoing research/investigation before acting — "doing the homework"). Failing either creates legal liability.
- **Third-party governance**: vendor risk management, SLAs, right-to-audit clauses, on-site assessments.
- **Documentation hierarchy**:
  - **Policy** — high-level, mandatory, board/exec-approved statement of intent.
  - **Standard** — mandatory, specific requirements supporting a policy (e.g., "AES-256 for data at rest").
  - **Procedure** — mandatory, step-by-step instructions.
  - **Guideline** — discretionary, recommended best practice.
  - **Baseline** — a defined minimum level of security (e.g., a hardened OS image).

## 1.3 Compliance and legal/regulatory

- **Types of law**: criminal (society vs. individual, imprisonment possible), civil/tort (compensates the injured party), administrative/regulatory (agency-enforced, e.g., fines).
- **Intellectual property**: copyright (expression of an idea), patent (an invention, time-limited monopoly), trademark (brand identifiers), trade secret (protected as long as kept secret — e.g., Coca-Cola formula).
- **Privacy regulations**: GDPR (EU — data subject rights, breach notification within 72 hours, extraterritorial reach), CCPA/CPRA (California), sector laws like HIPAA (US healthcare), GLBA (US financial).
- **Transborder data flow** issues — data sovereignty, adequacy decisions, standard contractual clauses.
- **Import/export controls**, cybercrime laws (Computer Fraud and Abuse Act in the US, Computer Misuse Act in the UK).

## 1.4 Professional ethics

- **(ISC)² Code of Ethics canons** (in priority order):
  1. Protect society, the commonwealth, and the infrastructure.
  2. Act honorably, honestly, justly, responsibly, and legally.
  3. Provide diligent and competent service to principals.
  4. Advance and protect the profession.
- Organizational codes of ethics (e.g., a corporate code of conduct) supplement but don't override the (ISC)² canons for certified professionals.

## 1.5 Business Continuity (BCP) — planning phase

*(Full DR/operational execution lives in Domain 7 — this domain covers the planning/requirements side.)*

- **BCP project scope and planning**: business organization analysis, resource requirements, legal/regulatory requirements.
- **Business Impact Analysis (BIA)**: identifies critical business functions and quantifies impact of disruption.
  - **MTD (Maximum Tolerable Downtime)** — longest a function can be down before causing unacceptable harm.
  - **RTO (Recovery Time Objective)** — target time to restore a function; must be ≤ MTD.
  - **RPO (Recovery Point Objective)** — maximum acceptable data loss, measured in time (drives backup frequency).
  - **WRT (Work Recovery Time)** — time to restore data/verify function after systems are back, part of MTD.

## 1.6 Risk management

- **Risk = Threat × Vulnerability** (conceptually; a threat needs a vulnerability to create risk).
- **Risk assessment approaches**:
  - **Quantitative** — assigns monetary values.
    - **AV** (Asset Value)
    - **EF** (Exposure Factor) — % of asset value lost in a single incident
    - **SLE** (Single Loss Expectancy) = AV × EF
    - **ARO** (Annualized Rate of Occurrence) — expected frequency per year
    - **ALE** (Annualized Loss Expectancy) = SLE × ARO
    - Compare ALE before/after a control to justify its cost (control cost should be < ALE reduction).
  - **Qualitative** — uses scales/judgment (e.g., High/Medium/Low), faster but subjective; Delphi technique for group consensus.
- **Risk response options**: **mitigate** (reduce likelihood/impact via controls), **transfer** (insurance, outsourcing), **accept** (formally, with sign-off, when cost of control exceeds risk), **avoid** (eliminate the activity), **reject/ignore** (not a valid formal option — indicates poor governance).
- **Control types by function**: preventive, detective, corrective, deterrent, recovery, compensating.
- **Control types by nature**: administrative (policy, training), technical/logical (firewalls, encryption), physical (fences, guards).
- **Risk frameworks**: NIST RMF (Risk Management Framework), ISO 31000, COSO ERM.
- **Threat modeling**: STRIDE (Spoofing, Tampering, Repudiation, Information disclosure, Denial of service, Elevation of privilege), DREAD, attack trees, reduction analysis (decomposing the system).
- **Supply chain risk management**: vendor assessments, hardware/software provenance, SBOM (Software Bill of Materials).

## 1.7 Security awareness, training, and education

- **Awareness** — what (recognize phishing); **Training** — how (use MFA correctly); **Education** — why (understand underlying principles, typically for security professionals).
- Program should be role-based and reinforced (phishing simulations, refreshers), measured for effectiveness.

## 1.8 Personnel security

- Candidate screening (background checks), employment agreements (NDAs), onboarding/offboarding procedures, **separation of duties**, **least privilege**, **job rotation**, **mandatory vacation** (surfaces fraud — someone else must cover the role).

## Key exam tips

- Domain 1 questions often present a scenario and ask "what should you do FIRST" — usually the answer is a governance/planning step (assess risk, consult policy) rather than a technical fix.
- Know the ALE formula cold; expect at least one calculation question.
- Distinguish due care (acting) from due diligence (researching before acting) — a very common trick question.

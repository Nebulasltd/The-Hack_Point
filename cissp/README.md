# CISSP — Certified Information Systems Security Professional

Issuing body: [(ISC)²](https://www.isc2.org/). A management/architecture-level security certification (contrasted with hands-on offensive certs like OSCP) covering governance, risk, architecture, and operations across the full security program.

## Who it's for / requirements

- A minimum of **5 years cumulative, paid work experience** in two or more of the 8 domains below (one year waived with a relevant 4-year degree or an approved credential from the (ISC)² list).
- Candidates without the required experience can pass the exam and earn the **Associate of (ISC)²** designation, then convert to full CISSP once experience is documented (6-year window).
- Requires adherence to the (ISC)² Code of Ethics and endorsement by an existing (ISC)² certified professional.

## Exam format

| | |
|---|---|
| Format | Computerized Adaptive Testing (CAT) in English; linear (CBT) in other languages |
| Length | 100–150 questions, 3 hours |
| Question types | Multiple choice + "advanced innovative" items (drag-and-drop, hotspot) |
| Passing score | 700 / 1000 |
| Domains tested | 8 (below) |

CAT means the exam adapts difficulty to your performance in real time — there's no fixed question count, and question order/difficulty isn't uniform across candidates. Finishing at the 100-question minimum is not itself a signal of pass or fail.

## The 8 domains (weights effective April 2024)

| # | Domain | Weight |
|---|---|---|
| 1 | Security and Risk Management | 16% |
| 2 | Asset Security | 10% |
| 3 | Security Architecture and Engineering | 13% |
| 4 | Communication and Network Security | 13% |
| 5 | Identity and Access Management (IAM) | 13% |
| 6 | Security Assessment and Testing | 12% |
| 7 | Security Operations | 13% |
| 8 | Software Development Security | 10% |

### 1. Security and Risk Management (16%)
CIA triad and security governance principles; compliance and legal/regulatory requirements (GDPR, data breach notification laws); professional ethics ((ISC)² Code of Ethics); security policy, standards, procedures, guidelines; business continuity requirements; personnel security policies; risk management concepts (threat modeling, risk assessment/analysis, quantitative vs. qualitative); security awareness/training; supply chain risk management.

### 2. Asset Security (10%)
Information/asset classification and ownership; privacy protection (data owners, custodians, processors); asset retention; data security controls (data states: at rest, in transit, in use); data handling requirements (marking, labeling, storage).

### 3. Security Architecture and Engineering (13%)
Secure design principles; security models (Bell-LaPadula, Biba, Clark-Wilson); evaluation criteria (Common Criteria, TCSEC); security capabilities of information systems (memory protection, TPM); vulnerabilities in web-based/mobile/embedded/IoT/cloud systems; cryptography (symmetric/asymmetric, hashing, PKI, cryptanalysis); site/facility physical security design.

### 4. Communication and Network Security (13%)
Secure network architecture design (OSI/TCP-IP models, IP networking, converged protocols); secure network components (firewalls, IDS/IPS, endpoint security); secure communication channels (VoIP, multimedia collaboration, remote access, data communications); network attack prevention/mitigation.

### 5. Identity and Access Management — IAM (13%)
Physical/logical access control to assets; identification and authentication (single/multi-factor, biometrics); identity as a service (federated identity, SSO, IDaaS); third-party identity services; authorization mechanisms (RBAC, ABAC, MAC, DAC); identity/access provisioning lifecycle (account review, deprovisioning).

### 6. Security Assessment and Testing (12%)
Assessment/audit strategies; security control testing (vulnerability assessment, penetration testing, log reviews, synthetic transactions, code review/testing); test output analysis and reporting; internal/third-party/regulatory audits.

### 7. Security Operations (13%)
Investigations support and requirements (evidence collection, digital forensics); logging/monitoring (SIEM, egress monitoring, UEBA); resource provisioning; foundational security operations concepts (need-to-know, separation of duties, job rotation); incident management (detection, response, mitigation, reporting, recovery, remediation, lessons learned); disaster recovery and business continuity; physical security.

### 8. Software Development Security (10%)
Security in the Software Development Life Cycle (SDLC); security controls in development environments; software security effectiveness assessment; acquired software security impact; secure coding guidelines/standards (OWASP Top 10, CWE); DevSecOps concepts.

## Study resources

**Official / primary**
- [(ISC)² CISSP Official Study Guide](https://www.wiley.com/en-us/CISSP) (Sybex; Mike Chapple, James Michael Stewart, Darril Gibson) — the standard text most candidates work through cover to cover
- [(ISC)² CISSP Official Practice Tests](https://www.wiley.com/en-us/CISSP) (Sybex) — question bank aligned to the study guide
- [(ISC)² CISSP Exam Outline](https://www.isc2.org/certifications/cissp/cissp-certification-exam-outline) — the authoritative domain/weight reference, always check this for the current version
- [(ISC)² Official Training](https://www.isc2.org/training) — instructor-led / OnDemand / self-paced options direct from ISC2

**Free / community**
- [Destination Certification](https://destcert.com/) (Rob Witcher / Lou Hablas) — widely recommended free CISSP videos and study plan
- Kelly Handerhan's CISSP content (historically on Cybrary/Prepcast) — domain walkthroughs
- [Thor Teaches](https://thorteaches.com/) — free practice questions and paid course
- [CCCure](https://www.cccure.education/) — long-running CISSP study community, forums, and practice exams

**Practice exams**
- [Boson ExSim-Max for CISSP](https://www.boson.com/practice-exam/cissp-isc2-practice-exam) — realistic CAT-style practice exam, commonly recommended as a final readiness check
- (ISC)² Official Practice Tests (see above)
- CCCure practice exams

## Study notes

Track your own domain notes, weak areas, and practice-exam scores in [`notes/cissp/`](../notes/cissp/).

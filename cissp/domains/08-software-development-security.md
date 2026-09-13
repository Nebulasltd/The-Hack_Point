# Domain 8: Software Development Security (10%)

Security integrated into how software gets built — SDLC, secure coding, and the security implications of different development approaches.

## 8.1 Security in the Software Development Life Cycle (SDLC)

- **Classic SDLC phases**: Requirements → Design → Development/Implementation → Testing → Deployment → Maintenance → Disposal. Security should be integrated at **every** phase, not bolted on at the end ("shift left").
- **Security requirements** should be gathered alongside functional requirements (e.g., "the system shall encrypt PII at rest").
- **Threat modeling at design time** (see Domain 1/3 — STRIDE) — cheapest point to fix a flaw is before code is written.
- **Secure coding standards** applied during development (see 8.3 below).
- **Security testing** integrated into the testing phase (SAST/DAST/IAST — see Domain 6) rather than only at the end.
- **Change/release management** controlling what reaches production (see Domain 7).
- **Maintenance** — ongoing patching, vulnerability management for the software's dependencies for its entire supported lifetime.
- **Disposal** — secure decommissioning, data migration/sanitization when a system is retired.

## 8.2 Development methodologies and their security implications

- **Waterfall** — sequential, each phase completes before the next begins; security requirements must be nailed down early since change is costly later.
- **Agile/Scrum** — iterative sprints; security must be built into each sprint (security user stories, definition-of-done criteria) rather than treated as a separate final phase.
- **DevOps / DevSecOps** — integrates development, operations, and (in DevSecOps) security into a continuous pipeline. **"Shift left"** means moving security testing earlier in the pipeline (e.g., SAST in the CI build) rather than only scanning right before release.
- **CI/CD (Continuous Integration/Continuous Deployment)** — automated build/test/deploy pipelines; security controls include pipeline-integrated scanning, signed artifacts, and restricting who can approve production deploys.
- **Maturity models**: **SW-CMM/CMMI** (general process maturity, 5 levels from Initial to Optimizing), **SAMM (Software Assurance Maturity Model)** and **BSIMM (Building Security In Maturity Model)** — specifically measure software security program maturity.

## 8.3 Security controls in the development environment / secure coding

- **Input validation** — the single most important defensive coding practice; validate type, length, format, and range, and prefer **allow-listing** (defining what's permitted) over **deny-listing** (defining what's forbidden, which is always incomplete).
- **Output encoding** — encode data before rendering it in a different context (e.g., HTML-encode before writing to a web page) to prevent injection.
- **Parameterized queries / prepared statements** — the standard defense against SQL injection (never build SQL via string concatenation with user input).
- **OWASP Top 10** (web application risk categories — current framing emphasizes categories like): Broken Access Control, Cryptographic Failures, Injection, Insecure Design, Security Misconfiguration, Vulnerable and Outdated Components, Identification and Authentication Failures, Software and Data Integrity Failures, Security Logging and Monitoring Failures, Server-Side Request Forgery (SSRF). *(Check [owasp.org](https://owasp.org/www-project-top-ten/) for the current published version — this list is periodically revised.)*
- **CWE (Common Weakness Enumeration)** — a catalog of software weakness types (broader/more granular than OWASP Top 10, used for classifying specific code-level flaws).
- **Software composition analysis (SCA)** — scanning for known vulnerabilities in third-party/open-source dependencies (a large share of real-world breaches trace back to unpatched dependencies, not custom code).
- **Secrets management** — never hardcode credentials/API keys in source code; use a dedicated secrets manager/vault.
- **Version control security** — access control on repos, signed commits, preventing secrets from being committed (pre-commit hooks, secret-scanning).

## 8.4 Assess the effectiveness of software security

- Combines Domain 6 testing techniques (SAST, DAST, IAST, fuzzing, code review) applied specifically to software under development, plus tracking metrics like defect density and time-to-remediate for security findings.

## 8.5 Assess security impact of acquired software

- **Third-party/COTS (Commercial Off-The-Shelf) software risk**: vendor security posture, patch cadence, EOL/EOS (end-of-life/end-of-support) tracking.
- **Open-source software risk**: license compliance, project maintenance activity/abandonment risk, supply-chain attacks (a compromised upstream package/dependency, e.g., a malicious npm/PyPI package).
- **SBOM (Software Bill of Materials)** — an inventory of all components/dependencies in a piece of software, increasingly required for critical software supply chains — lets an organization quickly determine exposure when a new dependency vulnerability is disclosed.

## 8.6 Define and apply secure coding guidelines and standards

- Language/platform-specific secure coding standards (e.g., OWASP Secure Coding Practices, CERT Secure Coding Standards).
- **Database security specific to development**: stored procedures to limit direct query access, views to restrict visible columns/rows, least-privilege database accounts for applications (an app shouldn't connect as a DB admin/root account).
- **API security**: authentication/authorization on every endpoint (never assume an internal-only API is safe from misuse), rate limiting, input validation identical in rigor to any other input source.

## Key exam tips

- Input validation is the exam's favorite "best defense" answer for injection-style questions — allow-listing beats deny-listing.
- Know that security belongs in every SDLC phase, and that Agile/DevOps require security to be continuous (per-sprint/per-pipeline-run), not a final gate.
- Distinguish OWASP Top 10 (web app risk categories, high level) from CWE (granular weakness catalog) if a question tests the distinction.

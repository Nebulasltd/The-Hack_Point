# Domain 8 Practice Questions: Software Development Security

Original questions written for self-study, aligned to the domain outline in [`../domains/08-software-development-security.md`](../domains/08-software-development-security.md). Not sourced from any official exam.

---

**1.** Which input validation approach defines exactly what IS permitted and rejects everything else, generally considered stronger than defining what is forbidden?

A) Deny-listing (blocklisting)
B) Allow-listing (allowlisting)
C) Output encoding
D) Parameterized queries

<details><summary>Answer</summary>

**B.** Allow-listing defines the complete set of permitted values/patterns and rejects anything else. Deny-listing tries to enumerate what's forbidden, which is inherently incomplete — attackers can find variations that weren't blocked.
</details>

---

**2.** What is the standard, most effective defense against SQL injection?

A) Deny-listing known malicious SQL keywords
B) Parameterized queries / prepared statements
C) Client-side input validation only
D) Encrypting the database at rest

<details><summary>Answer</summary>

**B.** Parameterized queries (prepared statements) separate SQL code from user-supplied data at the database driver level, preventing user input from ever being interpreted as executable SQL — the standard defense against SQL injection.
</details>

---

**3.** In the phrase "shift left," what does "left" refer to in the context of secure software development?

A) Moving security testing later in the deployment pipeline
B) Moving security activities earlier in the SDLC/pipeline, closer to design and development
C) Migrating from Waterfall to Agile
D) Reducing the size of the codebase

<details><summary>Answer</summary>

**B.** "Shift left" means integrating security earlier in the development lifecycle (requirements, design, coding) rather than only testing for security right before deployment — catching issues when they're cheaper to fix.
</details>

---

**4.** An organization discovers that one of its open-source dependencies has a newly disclosed critical vulnerability. Which artifact allows them to quickly determine every application across their environment that uses this dependency?

A) A Protection Profile
B) An SBOM (Software Bill of Materials)
C) A Security Target
D) A CVSS score

<details><summary>Answer</summary>

**B.** An SBOM is an inventory of all components/dependencies used in a piece of software. Maintaining SBOMs across an environment lets an organization rapidly identify exposure when a new dependency vulnerability is disclosed.
</details>

---

**5.** Which testing approach tests a running web application from the outside, without access to source code, simulating how an external attacker would interact with it?

A) SAST
B) DAST
C) SCA
D) Code review

<details><summary>Answer</summary>

**B.** DAST (Dynamic Application Security Testing) exercises a running application externally/black-box style, catching runtime issues (like misconfigurations) that static source review might miss.
</details>

---

**6.** A development team hardcodes an API key directly into a source file, which is later discovered in a public repository. What should have been used instead?

A) A deny-list of forbidden characters
B) A dedicated secrets management/vault solution
C) SAST scanning alone, with no other control
D) A stronger password policy for developer accounts

<details><summary>Answer</summary>

**B.** Secrets (API keys, credentials, certificates) should never be hardcoded in source code — they belong in a dedicated secrets manager/vault, retrieved at runtime, kept out of version control entirely (often enforced additionally with pre-commit secret-scanning).
</details>

---

**7.** Which maturity model is specifically designed to measure and improve the maturity of an organization's software security assurance program, rather than general software process maturity?

A) CMMI
B) ITIL
C) BSIMM / SAMM
D) COBIT

<details><summary>Answer</summary>

**C.** BSIMM (Building Security In Maturity Model) and SAMM (Software Assurance Maturity Model) specifically measure software security program maturity. CMMI measures general software/process maturity; ITIL and COBIT are IT service management and governance frameworks, not software-security-specific.
</details>

---

**8.** An application connects to its database using an account with full administrative privileges, even though it only ever needs to read and write to two specific tables. This violates which principle?

A) Separation of duties
B) Least privilege
C) Defense in depth
D) Non-repudiation

<details><summary>Answer</summary>

**B.** The application's database account should be scoped to only the privileges it actually needs (e.g., SELECT/INSERT/UPDATE on specific tables) — granting admin-level access violates least privilege and expands the blast radius of any application-layer compromise (e.g., SQL injection).
</details>

---

**9.** Which of the following is the PRIMARY risk associated with using third-party open-source components in an application?

A) Open-source code is always slower than proprietary code
B) Known vulnerabilities in unmaintained or outdated dependencies, and potential supply-chain compromise of the package itself
C) Open-source licenses always prohibit commercial use
D) Open-source components cannot be scanned by SAST tools

<details><summary>Answer</summary>

**B.** The primary risks are inheriting known (and sometimes undisclosed) vulnerabilities from dependencies — especially unmaintained ones — and the possibility that an upstream package itself has been compromised (a supply-chain attack).
</details>

---

**10.** Under Agile/DevSecOps practices, how should security testing best be integrated?

A) As a single, final gate immediately before production release only
B) Continuously, integrated into each sprint/pipeline run (e.g., automated SAST in CI)
C) Only during the annual penetration test
D) Security testing is not compatible with Agile methodologies

<details><summary>Answer</summary>

**B.** Agile and DevSecOps integrate security testing continuously throughout each sprint or pipeline run, rather than treating it as a single gate at the very end — consistent with the "shift left" principle.
</details>

---

[← Back to CISSP module](../README.md)

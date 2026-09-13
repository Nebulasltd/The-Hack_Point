# Domain 6 Practice Questions: Security Assessment and Testing

Original questions written for self-study, aligned to the domain outline in [`../domains/06-security-assessment-and-testing.md`](../domains/06-security-assessment-and-testing.md). Not sourced from any official exam.

---

**1.** Which activity actively attempts to exploit identified weaknesses to demonstrate real-world business impact, rather than simply cataloging them?

A) Vulnerability assessment
B) Penetration testing
C) Log review
D) Code review

<details><summary>Answer</summary>

**B.** Penetration testing goes beyond identifying vulnerabilities (vulnerability assessment) by actively attempting exploitation to prove real-world impact.
</details>

---

**2.** A tester is given full access to source code and architecture diagrams before beginning an assessment. This is an example of:

A) Black box testing
B) Gray box testing
C) White box testing
D) Blind testing

<details><summary>Answer</summary>

**C.** White box testing provides the tester with full internal knowledge (source code, architecture), enabling the most thorough assessment.
</details>

---

**3.** A vulnerability scanner reports a critical finding on a server, but manual investigation confirms the vulnerable service isn't actually present on that system. This is an example of:

A) A false negative
B) A true positive
C) A false positive
D) A true negative

<details><summary>Answer</summary>

**C.** A false positive is a finding the tool flagged that turns out not to be real. This is generally less dangerous than a false negative (a real issue the tool missed), but still costs remediation-team time to investigate.
</details>

---

**4.** Which type of security testing examines source code without executing the application?

A) DAST
B) SAST
C) IAST
D) Fuzzing

<details><summary>Answer</summary>

**B.** SAST (Static Application Security Testing) analyzes source/binary code without running it. DAST tests a running application from the outside; IAST instruments a running application to combine both approaches.
</details>

---

**5.** An organization's SaaS vendor provides a report confirming that its security controls were both suitably designed AND operating effectively over the preceding 12 months. This is a:

A) SOC 1 report
B) SOC 2 Type I report
C) SOC 2 Type II report
D) ISO 27001 certificate

<details><summary>Answer</summary>

**C.** A SOC 2 Type II report covers both the design AND the operating effectiveness of controls over a period of time (commonly 6–12 months) — a stronger assurance than a Type I report, which only assesses design at a single point in time.
</details>

---

**6.** A testing technique that feeds malformed, unexpected, or random input into an application to discover crashes and unhandled conditions is called:

A) Misuse case testing
B) Fuzzing
C) Synthetic transaction testing
D) Interface testing

<details><summary>Answer</summary>

**B.** Fuzzing automates the generation of malformed/random inputs specifically to surface crashes, memory corruption, and unhandled edge cases.
</details>

---

**7.** Why is a false negative generally considered more dangerous than a false positive in a security testing program?

A) False negatives take longer to investigate
B) A false negative creates unwarranted confidence that a system is secure when a real issue exists undetected
C) False negatives are more common statistically
D) False positives always indicate a compromised system

<details><summary>Answer</summary>

**B.** A false negative means a real vulnerability or attack goes undetected — the organization believes it's safe when it isn't, which is a more dangerous failure mode than spending time chasing a false alarm.
</details>

---

**8.** Which merchant assessment path under PCI DSS involves an independent, accredited assessor conducting the audit, typically required for higher transaction volumes?

A) SAQ (Self-Assessment Questionnaire)
B) QSA (Qualified Security Assessor) audit
C) SOC 2 Type II
D) ISO 27001 certification

<details><summary>Answer</summary>

**B.** Higher-volume merchants under PCI DSS are typically required to undergo an audit performed by a QSA, an independent, PCI-accredited assessor, rather than self-assess via an SAQ.
</details>

---

**9.** An organization runs scripted, simulated transactions in its production environment on a schedule to verify both functional correctness and that its monitoring/alerting pipeline correctly detects anomalies. This technique is:

A) Fuzzing
B) Synthetic transactions
C) Static analysis
D) Chain of custody verification

<details><summary>Answer</summary>

**B.** Synthetic transactions are scripted, simulated user actions run against a live or staging environment to verify functionality, performance, and (often) that monitoring/alerting systems are working as expected.
</details>

---

**10.** During a security audit, which type of audit is conducted by the organization's own internal staff rather than an outside party?

A) Third-party audit
B) Second-party audit
C) First-party (internal) audit
D) Regulatory audit only

<details><summary>Answer</summary>

**C.** A first-party audit is a self-assessment conducted by the organization's own internal audit function. A second-party audit is performed by a customer auditing a supplier; a third-party audit is performed by an independent outside party, often for certification purposes.
</details>

---

[← Back to CISSP module](../README.md)

# Domain 1 Practice Questions: Security and Risk Management

Original questions written for self-study, aligned to the domain outline in [`../domains/01-security-and-risk-management.md`](../domains/01-security-and-risk-management.md). Not sourced from any official exam.

---

**1.** An organization's annual loss expectancy (ALE) for a specific risk is $50,000. A proposed control costs $60,000 per year and would reduce the ALE to $5,000. What is the most defensible recommendation?

A) Implement the control, since it eliminates most of the risk
B) Reject the control, since its annual cost ($60,000) exceeds the risk reduction it provides ($45,000)
C) Implement the control regardless of cost, since any risk reduction is worthwhile
D) Transfer the risk instead of evaluating the control's cost

<details><summary>Answer</summary>

**B.** The control reduces ALE by $45,000/year but costs $60,000/year — it costs more than the risk it removes. A control should only be adopted when its annual cost is less than the risk reduction it provides.
</details>

---

**2.** A security manager researches applicable regulations, consults legal counsel, and reviews industry best practices before selecting a new access control policy. This activity best demonstrates:

A) Due care
B) Due diligence
C) Risk acceptance
D) Separation of duties

<details><summary>Answer</summary>

**B.** Due diligence is the research/investigation done *before* acting ("doing the homework"). Due care is the follow-through — actually implementing what a reasonable person would do based on that research.
</details>

---

**3.** Which risk response is appropriate when the cost of a control exceeds the potential loss, and management formally documents the decision with executive sign-off?

A) Risk mitigation
B) Risk transfer
C) Risk avoidance
D) Risk acceptance

<details><summary>Answer</summary>

**D.** Risk acceptance is a formal, documented decision (with appropriate sign-off) to take no further action because the cost of the risk is judged acceptable relative to the cost of addressing it.
</details>

---

**4.** A company outsources its payroll processing and purchases cyber-liability insurance covering data breach costs. This is an example of:

A) Risk mitigation
B) Risk transfer
C) Risk avoidance
D) Risk acceptance

<details><summary>Answer</summary>

**B.** Both outsourcing (shifting operational risk to a third party under contract) and insurance shift the financial impact of a risk to another party — the defining characteristic of risk transfer.
</details>

---

**5.** According to the (ISC)² Code of Ethics, which canon takes precedence over the others when they conflict?

A) Advance and protect the profession
B) Provide diligent and competent service to principals
C) Act honorably, honestly, justly, responsibly, and legally
D) Protect society, the commonwealth, and the infrastructure

<details><summary>Answer</summary>

**D.** The four canons are applied in priority order, and "protect society, the commonwealth, and the infrastructure" is listed first — it takes precedence if canons conflict.
</details>

---

**6.** Which document type is MANDATORY and provides specific, measurable requirements in support of a policy (e.g., "passwords must be at least 14 characters")?

A) Guideline
B) Standard
C) Procedure
D) Baseline

<details><summary>Answer</summary>

**B.** A standard is mandatory and specific, translating a high-level policy into concrete requirements. Guidelines are discretionary/recommended; procedures are step-by-step instructions; a baseline is a defined minimum configuration state.
</details>

---

**7.** A hospital's Business Impact Analysis determines that its patient records system can be down for a maximum of 4 hours before causing unacceptable harm. This value is the:

A) RPO
B) RTO
C) MTD
D) SLE

<details><summary>Answer</summary>

**C.** MTD (Maximum Tolerable Downtime) is the maximum time a function can be unavailable before causing unacceptable harm. RTO (Recovery Time Objective) is the target recovery time and must be less than or equal to the MTD.
</details>

---

**8.** During threat modeling using STRIDE, a threat where an attacker convinces a system that fraudulent traffic came from a trusted source is best categorized as:

A) Tampering
B) Spoofing
C) Repudiation
D) Elevation of privilege

<details><summary>Answer</summary>

**B.** Spoofing is impersonating something or someone else — presenting fraudulent traffic as if it came from a trusted/authorized source.
</details>

---

**9.** A quantitative risk assessment determines: Asset Value = $200,000, Exposure Factor = 25%. What is the Single Loss Expectancy (SLE)?

A) $25,000
B) $50,000
C) $200,000
D) $500,000

<details><summary>Answer</summary>

**B.** SLE = AV × EF = $200,000 × 0.25 = $50,000.
</details>

---

**10.** A control that discourages an attacker from attempting an action in the first place (e.g., a visible security camera or "Property Protected By..." sign) is best classified by function as:

A) Preventive
B) Detective
C) Deterrent
D) Compensating

<details><summary>Answer</summary>

**C.** A deterrent control discourages an attack from being attempted. A preventive control stops the attack from succeeding if attempted; a detective control identifies that it happened.
</details>

---

[← Back to CISSP module](../README.md)

# Domain 3 Practice Questions: Information Systems Acquisition, Development, and Implementation

Original questions written for self-study, aligned to the domain outline in [`../domains/03-information-systems-acquisition-development-implementation.md`](../domains/03-information-systems-acquisition-development-implementation.md). Not sourced from any official exam.

---

**1.** An IS auditor is invited to participate in a new system development project. What role should the auditor take to preserve independence?

A) Design the access control matrix for the new system
B) Approve the final go-live decision on management's behalf
C) Serve as an independent observer/advisor assessing whether appropriate controls are being designed in
D) Write the application's security code

<details><summary>Answer</summary>

**C.** The IS auditor should remain independent — advising and assessing whether controls are appropriately designed, without personally designing, implementing, or approving the controls they may later need to audit.
</details>

---

**2.** Which document justifies an IT investment with cost/benefit analysis and expected ROI, and against which the auditor later checks the project was tracked?

A) Audit charter
B) Business case
C) Configuration management database
D) Post-implementation review

<details><summary>Answer</summary>

**B.** The business case provides the justification (costs, benefits, strategic alignment, expected ROI) for a project before approval, and serves as a baseline the auditor can compare actual outcomes against.
</details>

---

**3.** A payroll system uses batch totals to confirm that the number and value of transactions processed matches the number and value submitted. This is an example of:

A) An output control
B) A general control
C) A processing/input control
D) A governance control

<details><summary>Answer</summary>

**C.** Batch totals (and hash totals) are classic processing/input controls used to confirm completeness and accuracy of data as it moves through a system.
</details>

---

**4.** Which type of control applies broadly across the entire IT environment (e.g., logical access control, change management) and underpins the reliability of all application-level controls?

A) Application controls
B) General IT controls
C) Detective controls only
D) Compensating controls only

<details><summary>Answer</summary>

**B.** General IT controls (access control, change management, operations) apply across the whole environment. If general controls are weak, confidence in ALL application controls is undermined, even ones that individually appear well-designed.
</details>

---

**5.** Who should formally perform and sign off on User Acceptance Testing (UAT) before a system goes live?

A) The development team exclusively
B) The IS auditor
C) Business users who will actually use the system
D) The infrastructure/operations team exclusively

<details><summary>Answer</summary>

**C.** UAT should be performed and formally signed off by the actual business users, confirming the system meets their real needs — not solely by the developers who built it.
</details>

---

**6.** Testing performed after a change to confirm previously working functionality has not been broken is called:

A) Unit testing
B) Regression testing
C) Integration testing
D) Parallel testing

<details><summary>Answer</summary>

**B.** Regression testing specifically re-verifies that existing, previously working functionality continues to work correctly after a change has been introduced.
</details>

---

**7.** A team routinely copies live production customer data into the development/test environment without masking or anonymizing it. This practice is primarily a concern because:

A) It improves testing realism with no downside
B) It exposes sensitive/PII data outside the controls applied to the production environment
C) It is required by most SDLC methodologies
D) It eliminates the need for UAT

<details><summary>Answer</summary>

**B.** Using unmasked production data in lower (typically less controlled) environments exposes sensitive data to a broader population with weaker controls than production — a very commonly cited audit finding; masked/synthetic data should be used instead wherever feasible.
</details>

---

**8.** Which of the following is the auditor's primary purpose during a post-implementation review?

A) To approve the original business case retroactively
B) To confirm the system is delivering the benefits stated in the original business case and capture lessons learned
C) To perform the initial UAT
D) To design the system's access control matrix

<details><summary>Answer</summary>

**B.** A post-implementation review, typically conducted some months after go-live, verifies the system is actually delivering the benefits promised in the business case and captures lessons learned for future projects.
</details>

---

**9.** An emergency change is implemented in production outside the normal change management process due to a critical outage. What should happen next, from a control perspective?

A) No further action is needed since it was an emergency
B) The change should still be logged and go through retroactive review/approval
C) The change should be reversed immediately regardless of whether it fixed the issue
D) Emergency changes should never be permitted under any circumstances

<details><summary>Answer</summary>

**B.** Emergency changes are a recognized exception to normal process timing, but they must still be logged and subjected to retroactive review/approval to maintain control and accountability — bypassing documentation entirely is the actual control failure.
</details>

---

**10.** A CMDB (Configuration Management Database) is used primarily to:

A) Store the organization's password policy
B) Maintain an accurate, controlled record of a system's components and their current approved state
C) Track employee performance reviews
D) Calculate the organization's risk appetite

<details><summary>Answer</summary>

**B.** A CMDB records IT assets/components and their configurations, supporting configuration management and change impact analysis by providing an authoritative, current view of what's actually deployed.
</details>

---

[← Back to CISA module](../README.md)

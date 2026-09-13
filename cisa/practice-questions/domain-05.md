# Domain 5 Practice Questions: Protection of Information Assets

Original questions written for self-study, aligned to the domain outline in [`../domains/05-protection-of-information-assets.md`](../domains/05-protection-of-information-assets.md). Not sourced from any official exam.

---

**1.** An IS auditor samples the list of employees terminated in the past quarter and compares it against the list of currently active system accounts. This test is primarily designed to detect:

A) Segregation-of-duties conflicts
B) Delayed or missed deprovisioning of access for terminated employees
C) Weak password policy
D) Inadequate encryption key management

<details><summary>Answer</summary>

**B.** Comparing terminated employees against active accounts is one of the most standard and frequently referenced audit tests for detecting deprovisioning failures — access that should have been removed but wasn't.
</details>

---

**2.** Which finding would most concern an auditor reviewing firewall rule sets?

A) All rules are documented with a business justification
B) Rules are reviewed annually per policy
C) A large number of overly permissive or stale rules with no clear business justification remain in place
D) The firewall logs all denied connection attempts

<details><summary>Answer</summary>

**C.** Stale, overly permissive firewall rules without documented business justification are a classic and common finding — they expand the attack surface unnecessarily and often accumulate because rules are added but never removed as needs change.
</details>

---

**3.** A data classification policy exists and is well-written, but interviews and testing reveal that staff do not consistently apply classification labels or follow associated handling requirements. What is the auditor's most accurate conclusion?

A) The control is effective since the policy exists
B) The control is not operating effectively, despite good policy design, because it is not being followed in practice
C) No further testing is needed once policy documentation is confirmed
D) This is solely a legal department issue, not an IT audit concern

<details><summary>Answer</summary>

**B.** A well-designed policy that isn't actually followed in practice represents an operating-effectiveness failure — auditors must test whether a control is genuinely applied, not just whether it's documented.
</details>

---

**4.** Strong encryption algorithms are in use for sensitive data at rest, but the encryption keys are stored in a plaintext configuration file accessible to the same broad group of administrators who can access the encrypted data itself. What is the primary concern?

A) None — strong encryption algorithms alone are sufficient
B) Weak key management undermines the protection the encryption is meant to provide
C) This is only a concern if the data is also unencrypted in transit
D) Key storage location is outside the scope of an IS audit

<details><summary>Answer</summary>

**B.** Encryption is only as strong as its key management. If keys are easily accessible to the same population that can access the encrypted data, the encryption provides little real additional protection — a frequently tested point.
</details>

---

**5.** Which of the following is the BEST way for an auditor to verify that access reviews (recertification) are operating effectively, beyond confirming that a review was performed?

A) Confirming a review email was sent to managers
B) Sampling completed reviews and verifying that inappropriate access identified during the review was actually removed
C) Confirming the review policy document exists
D) Relying solely on management's verbal assurance that reviews are effective

<details><summary>Answer</summary>

**B.** The meaningful test is whether access identified as inappropriate during a review was actually acted upon (removed), not merely whether a review activity occurred on paper.
</details>

---

**6.** An organization's incident response plan has never been exercised via a tabletop or simulation. What risk does this create?

A) None, provided the plan is thoroughly documented
B) Untested assumptions, unclear roles, or outdated procedures may only surface during a real incident, when it's too late to correct them cheaply
C) Tabletop exercises are only relevant to DR planning, not incident response
D) This is acceptable as long as the plan was reviewed by legal counsel

<details><summary>Answer</summary>

**B.** As with DR plans, an untested incident response plan risks discovering gaps (unclear roles, missing contact information, unworkable procedures) during an actual incident rather than in a low-stakes exercise.
</details>

---

**7.** Which practice specifically helps prevent a single privileged administrator's actions from going unmonitored?

A) Using a single shared administrator account for the whole IT team, for simplicity
B) Individual, attributable privileged accounts combined with logging and independent review of privileged activity
C) Removing all logging to reduce storage costs
D) Granting all staff administrator access to reduce access request delays

<details><summary>Answer</summary>

**B.** Individual (not shared) privileged accounts, combined with logging and independent review, ensure privileged actions can be attributed to a specific person and are subject to oversight — shared accounts destroy accountability entirely.
</details>

---

**8.** During a physical security review, an auditor observes that the organization's backup generator has never actually been started/tested since installation. What should the auditor conclude?

A) The control is effective since the generator is present
B) The presence of the equipment alone does not confirm the control works — untested equipment may fail when actually needed
C) Generator testing is outside the scope of an IS audit
D) This is only relevant if the organization has experienced a power outage previously

<details><summary>Answer</summary>

**B.** As with backups and DR plans generally, physical/environmental controls (generators, UPS, fire suppression) must be periodically tested to provide real assurance — mere presence of the equipment doesn't confirm it will function when actually needed.
</details>

---

**9.** Which of the following best describes the purpose of maintaining a chain of custody when handling evidence related to a security incident?

A) To speed up the incident response process by skipping documentation
B) To preserve evidence integrity and provenance in case it's later needed for disciplinary, legal, or regulatory action
C) To satisfy a requirement that applies only to law enforcement, not internal investigations
D) To classify the data according to the organization's data classification scheme

<details><summary>Answer</summary>

**B.** Chain of custody documents who handled evidence, when, and how, preserving its integrity so it remains defensible if later relied upon for disciplinary action, litigation, or a regulatory proceeding.
</details>

---

**10.** An organization's security awareness training is delivered once, during new-hire onboarding, with no subsequent refreshers or phishing simulations. An auditor would most likely characterize this program as:

A) Fully adequate, since all new hires receive training
B) Potentially insufficient, since awareness should be reinforced periodically (e.g., refreshers, phishing simulations), not a one-time event
C) Irrelevant to IS audit scope
D) Adequate as long as completion is tracked in an HR system

<details><summary>Answer</summary>

**B.** Effective security awareness programs are role-appropriate and reinforced over time (periodic refreshers, simulated phishing) rather than delivered once at onboarding and never revisited — a one-time-only program is a commonly cited gap.
</details>

---

[← Back to CISA module](../README.md)

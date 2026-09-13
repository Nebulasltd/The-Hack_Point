# Domain 4 Practice Questions: Information Systems Operations and Business Resilience

Original questions written for self-study, aligned to the domain outline in [`../domains/04-information-systems-operations-and-business-resilience.md`](../domains/04-information-systems-operations-and-business-resilience.md). Not sourced from any official exam.

---

**1.** A company's BIA specifies a 2-hour Recovery Time Objective for its order-processing system, but the current DR strategy relies on a cold site. What is the auditor's most appropriate conclusion?

A) The DR strategy is adequate since a cold site exists
B) The DR strategy is likely inadequate — a cold site cannot realistically support a 2-hour RTO
C) The RTO should be extended to match the cold site's capability with no further analysis
D) BIA and DR site selection are unrelated

<details><summary>Answer</summary>

**B.** A cold site (days to weeks to activate) cannot realistically support a 2-hour RTO — this is a classic, frequently tested logical gap between the BIA's requirement and the DR strategy's actual capability. The auditor should flag this misalignment.
</details>

---

**2.** Which ITIL process is specifically focused on identifying and eliminating the ROOT CAUSE of recurring incidents, rather than restoring service quickly?

A) Incident management
B) Problem management
C) Change management
D) Release management

<details><summary>Answer</summary>

**B.** Problem management targets root cause elimination to prevent recurrence. Incident management focuses on restoring normal service as quickly as possible for a specific occurrence.
</details>

---

**3.** An organization has a documented DR plan but has never actually tested it. From an audit perspective, this plan should be treated as:

A) Fully reliable, since it is documented in detail
B) Providing little real assurance, since an untested plan may not work as intended
C) Unnecessary, since documentation alone satisfies the control objective
D) Equivalent to a plan tested via full interruption

<details><summary>Answer</summary>

**B.** A DR/BC plan that has never been tested provides limited real assurance — untested assumptions, missing steps, and outdated contact/system information often only surface during an actual test (or, worse, a real disaster).
</details>

---

**4.** Which DR test type restores systems at the alternate site and validates recovery capability without disrupting the actual production environment?

A) Tabletop exercise
B) Parallel test
C) Full interruption test
D) Structured walkthrough only

<details><summary>Answer</summary>

**B.** A parallel test restores operations at the alternate site to validate the recovery capability, while production continues to run undisturbed — providing stronger assurance than a tabletop exercise without the risk of a full interruption test.
</details>

---

**5.** A critical financial calculation used company-wide is performed by a complex spreadsheet built and maintained by a single employee, entirely outside the formal SDLC. This is an example of an end-user computing (EUC) risk primarily because:

A) Spreadsheets are always less accurate than applications
B) It lacks independent testing, version control, and creates a single point of failure/knowledge
C) EUC tools are prohibited under all circumstances
D) It violates data classification policy automatically

<details><summary>Answer</summary>

**B.** EUC tools like spreadsheets typically bypass formal SDLC controls (independent testing, version control, documentation) and often depend on a single individual's knowledge — significant risks when the tool supports a critical business process.
</details>

---

**6.** Which of the following is the auditor's best test to verify that a backup process is actually a reliable recovery control, rather than simply confirming backups run on schedule?

A) Confirming the backup job log shows "success" each night
B) Performing or reviewing evidence of an actual test restoration of backup data
C) Reviewing the backup retention policy document
D) Confirming backup media is stored in a locked cabinet

<details><summary>Answer</summary>

**B.** A backup job reporting "success" only confirms the backup process ran — it does not confirm the data can actually be restored. Test restoration is the control that proves recoverability.
</details>

---

**7.** High Availability (HA) design, such as clustering and redundant power paths, primarily addresses which type of risk?

A) Data classification errors
B) Routine component failures, by minimizing downtime through automatic failover within a site
C) Regulatory non-compliance
D) Segregation of duties conflicts

<details><summary>Answer</summary>

**B.** HA is designed to minimize downtime from routine failures (a failed disk, a failed server) via redundancy and automatic failover — distinct from DR, which addresses recovery from major, often site-wide disasters.
</details>

---

**8.** A help desk logs an unusually high volume of incidents related to the same underlying issue over several weeks, but each is individually resolved with a workaround and closed. What is missing from the process?

A) Incident management, which is clearly functioning
B) Problem management, which should identify and address the recurring root cause
C) Change management approval
D) A service level agreement

<details><summary>Answer</summary>

**B.** Repeatedly resolving the same underlying issue with workarounds, without ever addressing the root cause, indicates problem management is not functioning — incidents are being closed, but the recurring cause is never eliminated.
</details>

---

**9.** Which statement about patch management is most accurate from an audit perspective?

A) Patches should be applied immediately to production with no testing, to minimize exposure window
B) A documented patch management process balancing timely application against appropriate testing and change control is the expected control
C) Patch management is outside the scope of IS audit
D) Only operating system patches need to be tracked, not applications

<details><summary>Answer</summary>

**B.** Effective patch management balances the need for timely remediation of vulnerabilities against the need to test patches and follow change control before deploying to production — auditors look for a documented, consistently followed process with defined SLAs by severity.
</details>

---

**10.** Which of the following would MOST concern an auditor reviewing database administrator (DBA) access controls?

A) DBAs have access needed to perform their job functions
B) DBA activity is logged and periodically reviewed by someone independent of the DBA function
C) DBA access is granted but no logging or independent review of DBA activity exists
D) DBA accounts require MFA

<details><summary>Answer</summary>

**C.** Highly privileged DBA access without any logging or independent review is a significant control gap — given the DBA's ability to access/modify data directly, monitoring and independent review of that activity is essential compensating control.
</details>

---

[← Back to CISA module](../README.md)

# Domain 7 Practice Questions: Security Operations

Original questions written for self-study, aligned to the domain outline in [`../domains/07-security-operations.md`](../domains/07-security-operations.md). Not sourced from any official exam.

---

**1.** Which stage of the NIST incident response lifecycle comes immediately AFTER "Containment, Eradication & Recovery"?

A) Detection & Analysis
B) Preparation
C) Post-Incident Activity (lessons learned)
D) Notification

<details><summary>Answer</summary>

**C.** The NIST lifecycle order is: Preparation → Detection & Analysis → Containment, Eradication & Recovery → Post-Incident Activity. The lessons-learned phase closes the loop and feeds improvements back into Preparation.
</details>

---

**2.** An organization needs a 4-hour Recovery Time Objective but has a limited budget and can tolerate the cost/complexity of near-real-time data replication and a fully staffed standby facility. Which DR site type best fits this requirement?

A) Cold site
B) Warm site
C) Hot site
D) Reciprocal agreement only

<details><summary>Answer</summary>

**C.** A hot site is fully equipped with near-real-time data replication and can fail over within minutes to a few hours — appropriate when the RTO is very short, despite being the most expensive option.
</details>

---

**3.** Which backup type requires only the last full backup and the single most recent backup of its own type to fully restore a system?

A) Incremental
B) Differential
C) Full
D) Snapshot only

<details><summary>Answer</summary>

**B.** A differential backup captures all changes since the last FULL backup, so restoration only needs the last full backup plus the most recent differential. Incremental backups require the last full backup plus every incremental since, making restoration slower/more complex.
</details>

---

**4.** During a digital forensic investigation, an investigator images a hard drive using a write-blocker and calculates a cryptographic hash of both the original and the image before proceeding. This step primarily supports:

A) Data classification
B) Chain of custody and evidence integrity
C) Risk transfer
D) Business continuity planning

<details><summary>Answer</summary>

**B.** Hashing before and after imaging (with a write-blocker preventing any modification of the original) proves the image is an unaltered, exact copy — essential to maintaining evidence integrity and a defensible chain of custody.
</details>

---

**5.** Which operational control specifically helps surface fraud by requiring someone other than the regular employee to perform their duties for a period of time?

A) Least privilege
B) Mandatory vacation
C) Need-to-know
D) Data classification

<details><summary>Answer</summary>

**B.** Mandatory vacation forces another person to cover a role temporarily, increasing the chance that ongoing fraud or irregularities the regular employee was concealing will be discovered.
</details>

---

**6.** A SIEM correlates login events from multiple systems to detect an anomaly, but the correlation is only accurate because all systems' clocks are synchronized. Which service is essential to this capability?

A) DNS
B) NTP (Network Time Protocol)
C) DHCP
D) LDAP

<details><summary>Answer</summary>

**B.** Accurate time synchronization via NTP across all log-generating systems is essential for correlating events chronologically — without it, event ordering and correlation become unreliable.
</details>

---

**7.** Which containment strategy involves immediately isolating a compromised system from the network, accepting a period of downtime, to stop an active attack from spreading?

A) Long-term containment
B) Short-term containment
C) Eradication
D) Recovery

<details><summary>Answer</summary>

**B.** Short-term containment takes immediate action (e.g., network isolation) to stop the spread of an incident, even at the cost of availability, while a longer-term plan is developed.
</details>

---

**8.** An organization restores its full production environment at an alternate site and actually cuts over live operations to test its DR plan, accepting the risk of a real service disruption if the test fails. This is:

A) A tabletop exercise
B) A parallel test
C) A full interruption test
D) A structured walkthrough

<details><summary>Answer</summary>

**C.** A full interruption test actually stops primary operations and cuts over to the alternate site — it provides the highest assurance but carries the highest risk, unlike a parallel test (which restores at the alternate site without disrupting production).
</details>

---

**9.** Which physical security design principle uses natural surveillance, natural access control, and territorial reinforcement to discourage crime through the design of the physical environment itself?

A) TEMPEST
B) CPTED (Crime Prevention Through Environmental Design)
C) Faraday shielding
D) Mantrap design

<details><summary>Answer</summary>

**B.** CPTED uses environmental design principles (sightlines, defined boundaries, controlled access points) to discourage criminal activity, rather than relying solely on guards or technology.
</details>

---

**10.** Which term describes the principle that a cleared/authorized individual should only access the specific information required for their current task, even if their clearance would technically permit broader access?

A) Least privilege
B) Need-to-know
C) Separation of duties
D) Job rotation

<details><summary>Answer</summary>

**B.** Need-to-know is narrower than least privilege (which governs system permissions generally) — it specifically limits access to the specific information required for the task at hand, regardless of what a person's overall clearance would allow.
</details>

---

[← Back to CISSP module](../README.md)

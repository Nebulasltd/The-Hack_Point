# Domain 7: Security Operations (13%)

The day-to-day and incident-driven work of running a security program: investigations, monitoring, incident management, and the operational (execution) side of BC/DR.

## 7.1 Investigations

- **Evidence types**: real/physical evidence, documentary evidence (must be authenticated), testimonial evidence (witness statements), demonstrative evidence (illustrates other evidence, e.g., a diagram).
- **Best evidence rule** — the original document/item is preferred over a copy where possible.
- **Chain of custody** — an unbroken, documented record of who handled evidence, when, and how — essential for evidence to be admissible; any gap can render evidence inadmissible or at least weaken it.
- **Digital forensics process**: identification → preservation (write-blockers, hashing for integrity verification) → collection → examination → analysis → presentation.
  - Practical commands/tools for this stage live in [`cheatsheets/forensics.md`](../../cheatsheets/forensics.md) elsewhere in this repo.
- **Investigation types**: administrative (internal policy violation), criminal (beyond reasonable doubt standard), civil (preponderance of evidence standard), regulatory (agency-specific standard), industry standards (e.g., PCI Forensic Investigator for card breaches).

## 7.2 Logging and monitoring

- **SIEM (Security Information and Event Management)** — centralizes, correlates, and alerts on log data from across the environment.
- **UEBA (User and Entity Behavior Analytics)** — baselines "normal" behavior and flags deviations (e.g., a user account suddenly accessing systems it never has before).
- **Egress monitoring** — watching outbound traffic for signs of data exfiltration.
- **Log management principles**: centralization, time synchronization (NTP — critical for correlating events across systems), retention aligned to policy/regulatory needs, protecting log integrity (write-once storage, restricted access to prevent tampering by an attacker covering tracks).
- **Continuous monitoring** — an ongoing process (not a point-in-time check) for detecting security-relevant changes/events.

## 7.3 Provisioning of resources

- Secure baseline configuration for new assets (hardened images), **asset management** throughout the lifecycle (provisioning → in-service → decommissioning), configuration management (tracking and controlling changes to baseline configs), **change management** (formal approval process for changes to production).

## 7.4 Foundational security operations concepts

- **Need-to-know** — access limited to information required for the specific task, even within a cleared/authorized population (narrower than "least privilege," which is about system permissions generally).
- **Separation of duties** — no single individual controls an entire critical process end-to-end (e.g., the person who requests a payment isn't the person who approves it).
- **Job rotation** and **mandatory vacation** — operational controls that surface fraud or single-person dependency by forcing coverage by someone else.
- **Privileged account management** — dedicated processes/tooling (PAM) for admin/root-level accounts, distinct from standard user account management.

## 7.5 Incident management

- **NIST incident response lifecycle**: **Preparation** → **Detection & Analysis** → **Containment, Eradication & Recovery** → **Post-Incident Activity (lessons learned)**.
- **Containment strategies**: short-term (isolate immediately, e.g., disconnect from network) vs. long-term (rebuild/patch while maintaining some operation).
- **Eradication** — removing the root cause (malware, attacker foothold, vulnerability) — not just the symptom.
- **Recovery** — restoring systems to normal operation, with heightened monitoring afterward for recurrence.
- **Lessons learned / post-incident review** — the step most often skipped under time pressure but the one that prevents recurrence; should feed back into Domain 1 risk management and Domain 6 testing.
- **Playbooks/runbooks** — predefined response procedures for common incident types (ransomware, phishing, data breach) to speed consistent response.

## 7.6 Disaster Recovery — the operational/execution side

*(Planning/BIA/RTO-RPO definitions live in Domain 1 — this is execution.)*

- **DR site types**:
  - **Hot site** — fully equipped, near-real-time data replication, can fail over in minutes/hours — most expensive.
  - **Warm site** — partially equipped, some data replication, restoration takes hours to a day or more.
  - **Cold site** — basic facility (power, space, connectivity) with no pre-installed systems — cheapest, slowest to activate (days to weeks).
  - **Mobile site / reciprocal agreement** — trailer-based or a mutual-aid arrangement with another organization (less common today, has reliability concerns).
- **Backup types**: full (everything, slowest to run, fastest to restore), incremental (changes since last backup of any type, fastest to run, slowest to restore — must replay the full chain), differential (changes since last full backup, middle ground — only needs the last full + last differential to restore).
- **Backup testing**: unannounced tests, tabletop exercises, parallel tests (restore without disrupting production), full interruption tests (highest assurance, highest risk).
- **High availability / fault tolerance**: RAID, clustering, redundant power/network paths, load balancing, geographic redundancy — reduces the *likelihood* of needing DR, complementary to but distinct from DR itself.

## 7.7 Physical security operations

- Perimeter/building/floor controls (also see Domain 3 for design principles); this domain covers the operational side: visitor management, badge/access log review, patrol procedures, alarm response, secure destruction operations, escort procedures for sensitive areas.

## Key exam tips

- Know the 4-phase incident response lifecycle in order — a very frequently tested sequence.
- Hot/warm/cold site trade-offs (cost vs. recovery time) are a classic scenario-question setup ("the business needs a 4-hour RTO and has a limited budget — which site type...").
- Incremental backups are fastest to create but slowest/most complex to restore (need every incremental since the last full); differential is the middle ground.

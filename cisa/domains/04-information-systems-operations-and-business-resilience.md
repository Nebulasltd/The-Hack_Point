# Domain 4: Information Systems Operations and Business Resilience (26%)

The largest domain (tied with Domain 5) — day-to-day IT operations, service management, and the organization's ability to withstand and recover from disruption.

## 4.1 IT operations management

- **Service management frameworks**: ITIL processes — **Incident Management** (restore normal service ASAP), **Problem Management** (find and eliminate root cause of recurring incidents), **Change Management** (control changes to the production environment), **Release Management**, **Service Level Management** (SLAs/OLAs).
- **Job scheduling** — controls over batch jobs/automated processes, including monitoring for failed jobs and appropriate authorization for schedule changes.
- **Capacity management** — ensuring IT resources (compute, storage, network) meet current and projected demand.
- **Help desk / service desk** — the primary interface for incident logging and initial triage; ticket data feeds problem management trend analysis.

## 4.2 Infrastructure and database management

- **Database administration**: DBA access should be monitored/logged given its highly privileged nature; segregation between DBA and application development/security functions.
- **Storage management**, **network operations**, **systems administration** — auditors assess whether privileged access to this infrastructure is appropriately restricted, logged, and reviewed.
- **Patch management** — timely application of security patches, balanced against change control and testing requirements; a documented patch management process/SLA is a standard audit test point.

## 4.3 Incident and problem management

- **Incident** — an unplanned interruption or reduction in quality of an IT service. **Problem** — the underlying cause of one or more incidents.
- Effective incident management restores service quickly; effective problem management prevents recurrence — auditors check both exist and that problem management actually closes the loop (root cause identified AND addressed, not just incidents repeatedly worked around).
- **Escalation procedures** and **severity/priority classification** — should be defined and consistently applied.

## 4.4 Change/configuration/release management in production

- (See also Domain 3, which covers change control during development.) In production, the auditor verifies: changes are requested formally, assessed for risk/impact, tested, approved by someone independent of the person making the change, scheduled appropriately (e.g., avoiding peak business periods), and that emergency changes still go through retroactive review/approval — not that they bypass control entirely.

## 4.5 End-user computing (EUC) controls

- Spreadsheets, small databases, and other end-user-developed tools that support business processes (sometimes significant financial ones) but are typically built and maintained OUTSIDE the formal SDLC/IT change control process.
- Key risks: no independent testing, no version control, single point of failure (the one person who understands the spreadsheet), formula errors going undetected.
- Controls: inventory of critical EUC tools, independent review/testing for high-risk ones, access restrictions, documentation requirements.

## 4.6 Business impact analysis (operational execution context)

- (Concepts — MTD, RTO, RPO — are foundational and consistently tested; see also general risk-management framing.) In this domain, the auditor's focus is whether the BIA is current, whether it was actually used to drive DR/BC planning decisions (recovery strategy, resource allocation), and whether it's periodically reassessed as the business changes.

## 4.7 Disaster recovery planning and testing

- **DR plan components**: recovery strategy, recovery team roles/responsibilities, communication plan, step-by-step recovery procedures, and a maintenance/update schedule.
- **DR site types** (hot/warm/cold — see the pentest repo's CISSP module for full detail) — auditor assesses whether the chosen site type actually supports the RTO defined in the BIA (a cold site cannot deliver a 4-hour RTO, for example — a very commonly tested logical gap).
- **DR testing types**: tabletop/structured walkthrough (lowest cost/risk, discussion-based) → simulation → parallel test (restore without disrupting production) → full interruption test (highest assurance, highest risk). Auditors check that DR plans are ACTUALLY tested periodically, not just documented — an untested plan provides false assurance.
- **Plan maintenance** — DR/BC plans must be updated as infrastructure, applications, staff, and contact information change; a plan that hasn't been updated to reflect a since-decommissioned system is a common finding.

## 4.8 System resilience and availability

- **Redundancy** — RAID, clustering, redundant power/network paths, geographic redundancy — reduces the likelihood of needing to invoke DR at all.
- **High availability (HA)** vs. **disaster recovery (DR)** — HA is about minimizing downtime from routine failures (automatic failover within a site); DR is about recovering from major/site-wide disasters.
- **Backup strategy** — full/incremental/differential trade-offs (see the CISSP module for the mechanics); auditors verify backups are actually tested for restorability (a backup that has never been test-restored is not a proven control), stored securely (including offsite/immutable copies as ransomware resilience), and retained per policy.

## Key exam tips

- This is the highest-weighted domain (tied with Domain 5) — expect the most questions here, often scenario-based ("the BIA specifies a 2-hour RTO, but the current DR site is cold — what is the auditor's most appropriate finding/recommendation?").
- An untested DR/BC plan should be treated by the auditor as providing no real assurance, regardless of how well-documented it looks.
- Know incident vs. problem management as distinct but related ITIL processes — incident restores service, problem eliminates root cause.

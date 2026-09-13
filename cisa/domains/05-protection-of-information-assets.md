# Domain 5: Protection of Information Assets (26%)

The security-control-heavy domain — tied for the highest weight. Heavy overlap with the CISSP CBK's IAM, network security, and operations domains, but examined here from an auditor's independent-assurance perspective rather than a practitioner's implementation perspective.

## 5.1 Information security frameworks, standards, and programs

- **ISO/IEC 27001/27002** — the internationally recognized ISMS (Information Security Management System) standard (27001 = requirements/certifiable; 27002 = code of practice/control guidance).
- **NIST Cybersecurity Framework (CSF)** — organizes activities into functions (Identify, Protect, Detect, Respond, Recover, and — in CSF 2.0 — Govern).
- **Security program governance** — policies, standards, defined roles/responsibilities, and a management review cycle (auditors check the program is actually operating, not merely documented).

## 5.2 Identity and access management controls

- **Provisioning/deprovisioning lifecycle** — timely account creation aligned to a valid business need, and (critically, from an audit perspective) timely deprovisioning upon termination/role change; auditors routinely sample terminated-employee lists against active-account lists to test this control.
- **Access review/recertification** — periodic manager/owner confirmation that existing access remains appropriate; catches privilege creep.
- **Segregation of duties (SoD)** — see Domain 2; auditors specifically test for SoD conflicts within application role/permission matrices (e.g., can one user both create and approve a vendor payment?).
- **Privileged access management** — elevated/admin accounts require additional controls: individual accountability (no shared admin accounts), enhanced logging, periodic review, and (where implemented) just-in-time/time-bound elevation.
- **Authentication controls**: password policy adequacy, MFA for remote/privileged access, account lockout thresholds.

## 5.3 Network and endpoint security controls

- Auditors assess whether network security controls (firewalls, segmentation, IDS/IPS) exist, are configured per policy/baseline, and are periodically reviewed (e.g., firewall rule review to remove stale/overly permissive rules — a very common finding).
- **Endpoint security**: antivirus/EDR coverage, patch compliance rates, device encryption for mobile/laptop assets.
- **Wireless security**: appropriate encryption standard in use, guest network segregation from corporate network.

## 5.4 Data classification, encryption, and PKI

- Auditors verify a data classification scheme exists AND is actually applied consistently (classification without enforcement is a common gap).
- **Encryption**: appropriate use for data at rest and in transit given classification; key management practices (generation, rotation, storage, destruction) are themselves an audit focus — strong encryption with weak key management provides little real protection.
- **PKI**: certificate lifecycle management (issuance, renewal, revocation) — expired or improperly validated certificates are a common, easily-tested finding.

## 5.5 Physical and environmental controls

- Data center/facility access controls (badge systems, visitor logs, mantraps), environmental controls (fire suppression, HVAC, power redundancy — UPS/generator), and periodic testing of these controls (e.g., does the generator actually start when tested?).

## 5.6 Security awareness training

- Auditors check that training is role-appropriate, mandatory, tracked for completion, and reinforced (e.g., phishing simulations) — not just a one-time onboarding checkbox.

## 5.7 Security incident response and management

- Auditor assesses whether an incident response plan exists, is tested (tabletop exercises), assigns clear roles, and — critically — whether past incidents were actually handled per the documented plan (comparing actual incident tickets/timelines against the plan).
- **Evidence handling / forensics** in an audit context: chain of custody, preservation of logs relevant to an investigation, coordination with legal/HR for personnel-related incidents.

## 5.8 Evidence collection and forensics (security-incident context)

- Overlaps with Domain 1's general evidence-handling principles, applied specifically to security incidents: auditors verify that when an incident occurs, evidence (logs, images, artifacts) is preserved with integrity (hashing, write-blockers) sufficient to support potential disciplinary, legal, or regulatory action later.
- Practical forensic tooling/commands are covered in this repo's [`cheatsheets/forensics.md`](../../cheatsheets/forensics.md) — useful background for an IS auditor assessing whether an organization's own incident response capability is adequate.

## Key exam tips

- This domain is where "auditor" and "practitioner" (CISSP-style) knowledge overlap most — but CISA questions test it from an assurance/control-verification angle: not "how do you configure this control" but "how would an auditor test whether this control is operating effectively."
- Sampling terminated employees against active access lists, and reviewing firewall rules for staleness, are two of the most frequently referenced real-world audit tests — expect scenario questions built around them.
- A documented control that isn't actually followed in practice is worse, from an audit perspective, than having no documentation at all combined with a consistent informal practice — because it demonstrates a governance/compliance gap on top of the control weakness itself.

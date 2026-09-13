# Domain 6: Security Assessment and Testing (12%)

Verifying that controls actually work — audits, testing methodologies, and how to interpret/report results.

## 6.1 Assessment and audit strategies

- **Assessment** — broader evaluation of security posture (can include testing, interviews, documentation review).
- **Audit** — formal, structured examination against a specific standard/baseline, often for compliance purposes.
- **Internal audit** — performed by the organization's own staff; **external/third-party audit** — performed by an independent outside party (often required for certain compliance regimes, e.g., SOC 2, PCI DSS).
- **First-party, second-party, third-party audits**: first-party = self-assessment; second-party = customer auditing a supplier; third-party = independent auditor for certification purposes.

## 6.2 Security control testing

- **Vulnerability assessment** — identifies and catalogs known weaknesses (often via automated scanners), no exploitation attempted. Produces a broad, relatively shallow list.
- **Penetration testing** — actively attempts to exploit vulnerabilities to demonstrate real-world impact. Deeper but narrower/more time-boxed than a vuln assessment.
  - **Black box** — tester has no prior knowledge (simulates an external attacker).
  - **White box** — tester has full knowledge (source code, architecture diagrams) — most thorough.
  - **Gray box** — partial knowledge (e.g., a standard user account) — simulates an insider or a post-initial-compromise attacker.
  - Phases generally: reconnaissance → scanning/enumeration → exploitation → post-exploitation → reporting.
- **Log reviews** — analyzing system/application/security logs for anomalies, often via a SIEM; requires log integrity (centralized, tamper-evident/write-once storage) to be trustworthy as evidence.
- **Synthetic transactions** — scripted, simulated user actions run against production/staging to verify functionality and performance (also used to test monitoring/alerting).
- **Code review / static analysis (SAST)** — examines source code without executing it, catches issues early in SDLC.
- **Dynamic analysis (DAST)** — tests a running application from the outside (black-box style), catches runtime issues SAST can miss.
- **Interactive analysis (IAST)** — instruments the running application to combine strengths of both.
- **Fuzzing** — feeds malformed/random/unexpected input to find crashes and unhandled conditions.
- **Misuse case testing** — testing from an attacker's perspective (the inverse of a use case).
- **Test coverage analysis** — measures how much of the code/functionality was actually exercised by tests.
- **Interface testing**: API, UI, and physical interface testing for security flaws (e.g., broken object-level authorization in an API).

## 6.3 Test output analysis and reporting

- **False positive** — the test flags an issue that isn't real; **false negative** — the test misses a real issue (the more dangerous of the two, since it creates false confidence).
- Findings should be prioritized by risk (severity × likelihood/exploitability, e.g., CVSS score) not just raw count.
- Reports should separate technical detail (for remediation teams) from executive summary (for leadership/risk owners) — see also the `notes/reporting/` and `cheatsheets/` material elsewhere in this repo for practical report-writing guidance.

## 6.4 Internal and third-party audits

- **SOC 1** — controls relevant to a service organization's impact on customer financial reporting.
- **SOC 2** — controls relevant to security, availability, processing integrity, confidentiality, privacy (Trust Services Criteria) — the most common report requested by enterprise customers of SaaS vendors.
  - **Type I** — controls' design at a point in time.
  - **Type II** — controls' design AND operating effectiveness over a period (typically 6–12 months) — a much stronger assurance.
- **ISO 27001 certification** — an organization's ISMS (Information Security Management System) audited against the ISO 27001 standard by an accredited certification body.
- **PCI DSS** — required for any organization handling cardholder data; assessed via **QSA (Qualified Security Assessor)** audit (for higher-volume merchants) or **SAQ (Self-Assessment Questionnaire)** (for lower-volume merchants).

## 6.5 Security process data

- Metrics/KPIs for the security program itself: mean time to detect (MTTD), mean time to respond (MTTR), patch compliance rate, phishing simulation click rate, number of findings by severity/age — used to demonstrate program maturity and drive continuous improvement (often tied back to a management review process, e.g., under ISO 27001's PDCA — Plan-Do-Check-Act — cycle).

## Key exam tips

- Vulnerability assessment finds and lists; penetration testing exploits and proves impact. Don't conflate them on the exam.
- SOC 2 Type II (a period of time) is a stronger assurance than Type I (a single point in time) — commonly tested.
- A false negative is generally worse than a false positive for security testing, because it creates unwarranted confidence.

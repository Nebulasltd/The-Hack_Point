# Domain 2: Governance and Management of IT (18%)

How IT is directed, structured, and aligned to the business — the auditor's view into IT governance rather than into a specific technical control.

## 2.1 IT governance frameworks and best practices

- **COBIT (Control Objectives for Information and Related Technologies)** — ISACA's own framework, the most directly relevant to CISA; organizes IT governance/management into domains and processes, distinguishes **governance** (Evaluate, Direct, Monitor — the board/exec level) from **management** (Plan, Build, Run, Monitor — the operational level).
- **ITIL** — IT service management framework (incident, problem, change, service-level management) — more operational/service-delivery focused than COBIT's governance focus.
- **ISO/IEC 38500** — international standard for corporate governance of IT.
- **Governance vs. management** — governance sets direction and monitors performance/compliance (board/executive responsibility); management executes within that direction (operational responsibility). A recurring conceptual distinction on the exam.

## 2.2 Organizational structure, roles, and responsibilities

- **IT steering committee** — cross-functional body (business and IT leadership) that prioritizes IT investments and aligns IT with business strategy.
- **CIO/CISO roles** — CIO typically owns IT service delivery and strategy; CISO owns the security program; reporting lines (does the CISO report to the CIO, creating a potential conflict of interest, or to the CEO/board?) is itself a governance topic auditors assess.
- **Segregation of duties (SoD)** in IT — e.g., developers should not have production deployment access; DBAs shouldn't be the sole approver of their own changes. SoD conflicts are a very common audit finding.

## 2.3 IT strategy and alignment

- **IT strategic plan** — should derive from and support the overall business strategy, not be developed in isolation.
- **Balanced Scorecard** — a framework (financial, customer, internal process, learning & growth perspectives) sometimes used to translate IT strategy into measurable objectives.
- **Enterprise architecture** — the structured blueprint of an organization's IT assets, processes, and their relationships, used to guide strategic IT decisions.

## 2.4 IT policies, standards, and procedures

- Same conceptual hierarchy as in security management generally: policy (mandatory, high-level) → standard (mandatory, specific) → procedure (mandatory, step-by-step) → guideline (discretionary). Auditors test whether actual practice matches documented policy — a gap here is itself a finding.

## 2.5 Enterprise risk management

- IT risk should be integrated into (not siloed from) enterprise-wide risk management.
- **Risk appetite** (how much risk the organization is willing to accept in pursuit of objectives) vs. **risk tolerance** (acceptable variation around that appetite) — set by the board, operationalized by management.
- **Three lines model** (formerly "three lines of defense"): 1st line = operational management/business owners who own and manage risk directly; 2nd line = risk management/compliance functions that oversee and support; 3rd line = internal audit, providing independent assurance to the board.

## 2.6 IT resource/portfolio/program management

- **Portfolio management** — selecting and prioritizing the right mix of IT investments/projects against strategy and available resources.
- **Program vs. project management** — a program is a coordinated group of related projects managed together for benefits not achievable by managing them individually.
- **IT budgeting and resource allocation** — auditors assess whether IT spend aligns with approved strategy/priorities and whether it's tracked/monitored appropriately.

## 2.7 Business continuity planning — governance level

- At this domain's level: does the organization have an approved BC policy, is a BC steering function established, is BCP resourced and does it have executive sponsorship? (The operational BIA/RTO/RPO details and DR execution live conceptually alongside Domain 4's operations content.)

## 2.8 Monitoring and reporting of IT performance

- **KPIs/KGIs (Key Performance/Goal Indicators)** — used to measure whether IT is delivering against its objectives.
- **IT balanced scorecards, dashboards, maturity assessments** (e.g., CMMI-based) — tools for ongoing governance oversight, reviewed periodically by the steering committee/board.

## Key exam tips

- Governance = direction-setting and oversight (board/exec); management = execution (operational). Almost every governance-domain scenario question hinges on correctly identifying which level a described activity belongs to.
- Know the three lines model — a favorite for questions about where internal audit fits relative to risk/compliance functions and business operations.
- Segregation of duties conflicts (e.g., a developer who can also push to production) are one of the most commonly tested IT governance findings.

# Domain 3: Information Systems Acquisition, Development, and Implementation (12%)

Auditing the project/SDLC side — is a system being built or acquired with appropriate controls, and were those controls actually followed?

## 3.1 Project governance and management practices

- **Project governance** — oversight structure ensuring a project delivers intended business value, stays within approved scope/budget/timeline, and has appropriate stakeholder involvement (steering committee, sponsor).
- **Project management methodologies**: traditional/Waterfall (sequential, phase-gated) vs. Agile (iterative, adaptive) — auditors need to assess controls appropriate to whichever methodology is actually in use, not force a Waterfall audit checklist onto an Agile project.
- **Role of the IS auditor in projects** — should be involved as an independent observer/advisor throughout (not a decision-maker) to assess whether appropriate controls are being designed in; auditor independence must be preserved (an auditor shouldn't design the controls they'll later audit).

## 3.2 Business case development and feasibility analysis

- **Business case** — justifies the investment (cost/benefit, expected ROI, strategic alignment) before a project is approved; the auditor checks that a business case existed, was approved at the right level, and that the project was tracked against it.
- **Feasibility study** dimensions: technical, operational, economic, schedule, legal/regulatory.
- **Cost-benefit analysis / ROI / NPV / payback period** — financial techniques used to evaluate whether an investment is justified.

## 3.3 System development methodologies

- **SDLC models**: Waterfall, Iterative, Spiral, Agile (Scrum/Kanban), DevOps — each has different control implications, e.g., in Agile, controls must be built into each sprint rather than as end-phase gates.
- **Prototyping and RAD (Rapid Application Development)** — faster delivery, but risk of insufficient documentation/control if not managed carefully.
- **Auditor's role by phase**: Requirements (are security/control requirements captured?) → Design (are controls designed appropriately, e.g., segregation-of-duties built into workflow logic?) → Development (secure coding practices, code review) → Testing (was testing independent of development, were security/UAT tests performed?) → Implementation (was there a formal go-live approval, data conversion validated?).

## 3.4 Control identification and design during development

- **Input controls**: validation, edit checks, completeness checks (e.g., batch totals, hash totals) to ensure data entering a system is accurate and complete.
- **Processing controls**: run-to-run totals, limit/reasonableness checks, exception reporting.
- **Output controls**: distribution controls, reconciliation of output to input/processing totals, review before release.
- **Application controls vs. general IT controls**: application controls are specific to a single application/process (e.g., a three-way match in a purchasing system); general controls apply broadly across the IT environment (e.g., logical access control, change management) and support the reliability of ALL application controls.

## 3.5 Testing methodologies

- **Unit testing** — individual components/modules, typically by developers.
- **Integration testing** — verifies components work together correctly.
- **System testing** — the complete, integrated system against requirements.
- **User Acceptance Testing (UAT)** — business users validate the system meets their actual needs before go-live; the auditor checks that UAT was performed by business users (not just IT) and formally signed off.
- **Regression testing** — confirms that changes haven't broken previously working functionality.
- Testing should occur in an environment segregated from production, using controls over test data (especially if production data — potentially containing sensitive/PII data — is used in test/dev environments, which is itself a common audit finding).

## 3.6 Configuration and release/change management

- **Change management process**: request → impact assessment/approval → testing → scheduled implementation → post-implementation review; unauthorized/emergency changes should still be logged and retroactively approved.
- **Configuration management** — maintaining an accurate, controlled record of a system's components and their current approved state (a CMDB — Configuration Management Database — is a common tool).
- **Version control** — for both application code and configuration, ensuring changes are tracked and can be rolled back if needed.

## 3.7 Post-implementation review

- Conducted after a system goes live (typically a defined period later, e.g., 3–6 months) to confirm the system is delivering the benefits stated in the original business case, that issues from go-live have been resolved, and to capture lessons learned for future projects.

## Key exam tips

- Application controls (specific to one process) vs. general controls (environment-wide, e.g., access control/change management) — general controls underpin the reliability of application controls, so weak general controls undermine confidence in ALL application-level controls, even ones that individually look fine.
- The IS auditor should remain independent during system development — advising/assessing controls, not designing or implementing them.
- Know input/processing/output control examples (batch totals, hash totals, reasonableness checks) — commonly tested with a scenario asking which control type would have caught a described error.

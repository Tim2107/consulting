# AI Governance Operating Model

Status: operational draft for board approval. Use this model to assign ownership before Phase 1 rollout.

## Operating Principle

AI governance should have one visible front door and several accountable control owners. The board sets red lines and exception authority; operational owners maintain the registry, review workflows, and evidence.

## Governance Roles

| Role | Accountable For | Typical Owner Type | Minimum Cadence |
| --- | --- | --- | --- |
| Board Sponsor | AI risk appetite, red lines, budget caps, high-risk exceptions, unresolved escalations. | Management board member or executive sponsor | Monthly during rollout; quarterly after stabilization |
| AI Governance Owner | Registry operation, intake process, policy updates, decision backlog, training coordination. | Security, IT governance, risk, or AI governance office | Weekly during rollout |
| Security Owner | Technical controls, secrets rules, access controls, logging, incident path, Delivery Pipeline Systems gates. | Security lead or CISO function | Per intake plus monthly control review |
| Legal / Data Protection Owner | DPA/subprocessor/transfer review, DPIA triggers, client-contract compatibility, legal escalation. | Legal, DPO, privacy counsel | Per restricted intake |
| Employee Transparency Owner | Employee AI Transparency Notice, HR review, labor/works-council coordination, monitoring-use boundaries. | HR, Legal, People Operations | Before employee-facing rollout and on material changes |
| Platform Owner | Self-hosted/managed-private infrastructure, runtime, monitoring, cost telemetry, support model. | Platform engineering or infrastructure | Weekly during pilot |
| Business Use-Case Owner | Purpose, users, data class, value case, output review, user training, acceptance criteria. | Delivery lead, department head, project owner | Per use case |
| Knowledge Owner | Source quality, taxonomy, freshness, access-control mapping, accepted internal answers. | Operations, knowledge management, delivery leadership | Per source set |

## Decision Rights

| Decision Type | Decision Owner | Required Input | Escalates To |
| --- | --- | --- | --- |
| Add or remove registry route | AI Governance Owner | Security, Legal/Data Protection, Business owner | Board Sponsor for restricted/high-risk routes |
| Permit Client Confidential Data in a third-party route | Legal / Data Protection Owner | Security, Business owner, client-contract reviewer | Board Sponsor |
| Approve Processing Location claim | Legal / Data Protection Owner | Provider evidence, Security, procurement/vendor owner | Board Sponsor if unclear |
| Approve Delivery Pipeline Systems action level | Security Owner | Platform owner, repository owner, Business owner | Board Sponsor for TGA-5 or exception |
| Trigger DPIA or legal assessment | Legal / Data Protection Owner | Intake owner, Security, Employee Transparency Owner where relevant | Board Sponsor if disputed |
| Approve employee-facing rollout | Employee Transparency Owner | Legal/Data Protection, Security, AI Governance Owner | Board Sponsor |
| Approve self-hosted RAG phase gate | Platform Owner | Security, Legal/Data Protection, Knowledge owner, Business owner | Board Sponsor |
| Approve training/fine-tuning exception | Board Sponsor | Legal/Data Protection, Security, client approval where needed | Full board |

## Required Standing Processes

### Registry Review

- Review all Restricted and Needs Decision rows monthly during rollout.
- Confirm owner, review date, approved data classes, routing constraints, retention/training settings, and employee-notice requirement.
- Retire tools that lack owner, contract basis, processing-location evidence, or control evidence.

### AI Use Case Intake

- Required for any non-public data, company confidential data, Client Confidential Data, source code, Delivery Pipeline Systems data, employee telemetry, automated action, or recurring/high-volume use.
- Intake must record tool route, Provider Stack, processing location, retention setting, training-use setting, access controls, logging, human review, output use level, and evidence references.

### Client-Data Exception Review

- Starts with the Contract Non-Ingestion Rule: do not paste or upload client contracts into AI tools.
- Human reviewer records only the compatibility outcome.
- Legal/Data Protection confirms contract, DPA, subprocessor, transfer, and processing-location posture.
- Security confirms access controls, secrets handling, audit logging, incident response, and exit path.
- Board Sponsor approves exceptions that leave the Company-Controlled Environment.

### Employee Rollout Review

- Required before broad employee use, workspace copilots, meeting/transcript tools, code assistants with employee telemetry, or tools that expose usage analytics.
- Review must cover transparency notice, log access, retention, permitted purposes, performance-management prohibition or limits, support contact, and local labor/works-council handling.

### DPIA Trigger Review

- Legal/Data Protection owns the DPIA trigger decision.
- Trigger review is required for personal data, employee monitoring, profiling, automated decision support, sensitive data, large-scale processing, client production data, or materially new technology use.
- Security and Business owners provide risk, control, and purpose evidence.

### Delivery Pipeline Systems Review

- Security owns the TGA classification and minimum controls.
- Platform and repository owners must confirm runner isolation, branch protection, protected environments, credential scope, policy-as-code, artifact integrity, rollback, and audit evidence.
- Production-impacting actions require human approval and separation of duties.

## Minimum Records

| Record | Owner | Retention Note |
| --- | --- | --- |
| Registry row and decision history | AI Governance Owner | Keep active version plus change history. |
| Intake decision | AI Governance Owner | Keep while workflow is active and through review period. |
| Provider evidence | Legal / Data Protection Owner | Keep source links, date accessed, contract basis, and evidence references. |
| Security review | Security Owner | Keep controls, residual risk, exceptions, and review date. |
| Employee notice | Employee Transparency Owner | Keep current notice and rollout evidence. |
| DPIA trigger decision | Legal / Data Protection Owner | Keep decision, rationale, and whether a DPIA was required. |
| TGA workflow evidence | Security Owner | Keep prompt/instruction summary, PR, workflow run, approvals, artifacts, deployment, and rollback evidence. |

## First 30 Days After Approval

| Week | Work Item | Primary Owner |
| --- | --- | --- |
| 1 | Name owners, confirm registry rows, freeze red lines, prepare employee notice. | Board Sponsor and AI Governance Owner |
| 2 | Launch training, intake, client-data exception path, and DPIA trigger triage. | AI Governance Owner and Legal/Data Protection |
| 3 | Validate security controls for approved tools and draft TGA implementation checklist. | Security |
| 4 | Review early usage, incidents, blocked requests, cost signals, and backlog priorities. | AI Governance Owner |

## Evidence References

- CLAIM-001 through CLAIM-004 for GDPR, provider, transfer, and DPIA baseline.
- CLAIM-007 and CLAIM-008 for financial-sector and cybersecurity supply-chain context.
- CLAIM-009 through CLAIM-011 for employee-facing AI and local labor/privacy review.
- CLAIM-055 through CLAIM-061 for Delivery Pipeline Systems controls.

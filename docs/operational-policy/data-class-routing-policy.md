# Data-Class Routing Policy

Status: first operational draft for board review. This policy should be used with the Approved AI Tool Registry, AI Use Case Intake, Client Contract Compatibility Check, and Employee AI Transparency Notice.

## Routing Principle

Data class comes before tool selection. A workflow may use AI only when the data class, provider route, processing location, retention posture, output use level, and required controls are approved together.

## Data Classes

| Data Class | Examples | Default AI Routing Status | Default Allowed Routes | Prohibited Routes | Required Gates |
| --- | --- | --- | --- | --- | --- |
| Public or approved-for-public data | Published website copy, public documentation, public marketing text | Allowed in approved tools | Approved enterprise tools, approved APIs, company self-hosted tools | Consumer/personal accounts unless explicitly approved | Basic usage guidance and output review |
| Internal non-confidential data | Internal notes, generic process drafts, non-sensitive templates | Restricted | Approved enterprise tools and approved internal/self-hosted tools | Consumer/personal accounts | Employee AI Transparency Notice where employee-facing |
| Company confidential data | Strategy notes, internal financials, non-public procedures, internal architecture | Restricted | Approved enterprise tools with no-training baseline, approved company self-hosted or managed-private deployment | Consumer tools, free developer tiers, unapproved plugins/extensions | AI Use Case Intake, retention/logging review, access controls |
| Source code and software-delivery data | Repositories, tickets, logs, architecture docs, dependency data | Restricted | Approved enterprise coding routes, approved provider API routes, self-hosted code-aware RAG | Consumer tools, unapproved IDE plugins, tools that retain/train without approval | Secrets scanning, repository scope controls, audit logs, no autonomous pipeline action |
| Delivery Pipeline Systems data | CI/CD configs, deployment logs, release approvals, infrastructure state | Restricted-by-default | Approved tools only for draft assistance or Technically Gated Actions | Unapproved agents, direct autonomous deployment, grey-market gateways | Technical gates, human approval, scoped permissions, rollback, policy-as-code |
| Employee AI Privacy data | Prompts tied to employees, work content, meeting transcripts, access logs, telemetry | Restricted | Approved employee-facing tools with transparency notice and retention controls | Hidden monitoring, unapproved transcript/log analysis | Employee AI Transparency Notice, minimization, labor/works-council review where required |
| Client Confidential Data | Client documents, regulated financial-sector material, production data, confidential project facts, personal data inside client material | Restricted | Company-controlled/self-hosted environment; managed private deployment; approved third-party route only after board/legal/client-contract gates | Consumer tools, free tiers with product-improvement use, unapproved providers | AI Use Case Intake, Client Contract Compatibility Check, DPA/subprocessor/transfer review, processing location, retention, routing controls |
| Regulated financial-sector Client Confidential Data | Bank/insurance production data, regulated reports, confidential financial records, outsourced ICT-relevant workflows | Restricted high-assurance | Company-controlled/self-hosted or managed-private deployment preferred; third-party route only after explicit approval | Consumer tools, global/default routing, unapproved subprocessors | DORA-style third-party risk review, client approval where required, auditability, incident/exit plan |
| Secrets and credentials | API keys, passwords, tokens, certificates, production credentials | Prohibited | None by default | All AI tools by default | Secret rotation and incident process if exposed |
| Client contracts and legal terms | MSAs, SOWs, DPAs, security appendices, confidentiality clauses | Prohibited until policy exception | Manual review; AI only if a future approved policy permits it | All AI tools by default | Contract Non-Ingestion Rule; legal approval before any exception |
| Training or fine-tuning datasets from company/client material | Tickets, code, chat logs, client files, labeled outputs | Prohibited by default | None by default | All default AI routes | Board, legal, security, data-protection, and client approval |

## Route Selection Rules

1. If the data is Client Confidential Data, first decide whether it may leave the Company-Controlled Environment.
2. If the answer is no, use a Company-Operated Self-Hosted Option, approved Managed Private Deployment, or client-controlled environment.
3. If the answer is yes, use only a registry route marked Restricted for Client Confidential Data and complete the required gates.
4. If the route depends on region, data residency, ZDR, modified abuse monitoring, or a routing constraint, the control must be technically enforced before use.
5. If the workflow touches Delivery Pipeline Systems, treat it as Restricted-by-Default even when no personal data is involved.
6. If the workflow performs or triggers an action, classify the output use level as Automated Action and require Technically Gated Action controls.
7. If employee prompts, files, telemetry, or work content are processed, issue or update the Employee AI Transparency Notice before rollout.
8. If the data includes secrets or client contracts, stop unless an explicit exception policy has been approved.

## Required Review Records

- AI Use Case Intake for any non-public data, Delivery Pipeline Systems data, automated action, or Client Confidential Data.
- Client Contract Compatibility Check before Client Confidential Data workflows.
- Provider Stack review for every third-party route.
- Processing Location and Provider Routing Constraint review for sensitive workflows.
- Employee AI Transparency Notice for employee-facing AI workflows.
- Cost Profile review for any route expected to become recurring or high-volume.

## Policy Gaps To Decide

- Whether any third-party provider may process Client Confidential Data outside the Company-Controlled Environment.
- Whether Microsoft 365 Copilot, Gemini Workspace, Grok Business, or ChatGPT Enterprise may process Workspace/tenant-held Client Confidential Data.
- Whether regional/DataZone/EU routes are sufficient for regulated financial-sector clients.
- Which provider routes are allowed for source code and Delivery Pipeline Systems data.
- Whether the self-hosted 70-user RAG pilot may include Client Confidential Data in Phase 1.

# Phase 1 Go-Live Checklist

Status: operational draft. Use this checklist before allowing broad employee use of approved AI tools.

## Phase 1 Definition

Phase 1 permits low-risk AI use in approved tools only. It is limited to public, approved-for-public, and non-confidential internal data. It does not approve Client Confidential Data, client source code, secrets, client contracts, autonomous actions, or training/fine-tuning on protected material.

## Go / No-Go Checklist

| Gate | Required Before Go-Live | Owner | Status |
| --- | --- | --- | --- |
| Board approval | DEC-001 and DEC-002 approved, with Phase 1 boundary recorded. | Board Sponsor | TBD |
| Registry owner | Named owner and deputy assigned. | Board Sponsor | TBD |
| Approved tool list | Phase 1 tools marked in registry with status, owner, allowed data classes, review date, and employee-notice requirement. | AI Governance Owner | TBD |
| Prohibited tool message | Consumer tools, personal accounts, unapproved plugins/extensions, free protected-data tiers, and grey-market gateways listed as prohibited. | AI Governance Owner | TBD |
| Data-class guidance | Allowed and prohibited data examples published for employees. | AI Governance Owner | TBD |
| Employee notice | Employee AI Transparency Notice completed for approved Phase 1 tools. | Employee Transparency Owner | TBD |
| HR/labor review | Local HR, labor-law, and works-council review path completed or explicitly marked not required by qualified owner. | Employee Transparency Owner | TBD |
| DPIA trigger triage | DPIA trigger decision path assigned and documented. | Legal / Data Protection Owner | TBD |
| Legal/provider review | DPA, subprocessor, transfer, retention, training-use, and processing-location posture checked for approved routes. | Legal / Data Protection Owner | TBD |
| Security controls | SSO/MFA, access controls, admin roles, retention/logging settings, and incident path confirmed. | Security Owner | TBD |
| Secrets rule | Employee guidance and reporting path for accidental secret exposure published. | Security Owner | TBD |
| Intake process | AI Use Case Intake path available for restricted workflows and exceptions. | AI Governance Owner | TBD |
| Client-data exception path | Client Contract Compatibility Check and route-exception review path ready. | Legal / Data Protection Owner | TBD |
| Training | Employee launch guidance issued, including examples and red lines. | AI Governance Owner | TBD |
| Support channel | Help/reporting channel for misuse, leakage, blocked requests, and quality issues active. | AI Governance Owner | TBD |
| Review cadence | First 30-day review meeting scheduled. | Board Sponsor | TBD |

## Phase 1 Allowed Uses

- Draft internal text from non-confidential notes.
- Summarize public material or approved internal non-confidential drafts.
- Translate or reformat approved text.
- Brainstorm generic ideas without client facts, secrets, or confidential strategy.
- Ask low-risk questions about approved policy or training material.

## Phase 1 Prohibited Uses

- Submit Client Confidential Data, regulated financial-sector client data, client contracts, production data, personal data from client material, or client source code.
- Submit secrets, credentials, keys, certificates, tokens, passwords, or production logs containing sensitive values.
- Use personal accounts, consumer AI tools, unapproved browser extensions, unapproved desktop agents, unofficial gateways, or free tiers that use protected data for product improvement.
- Connect tools to source control, ticketing, email, calendar, drives, chat, or repositories unless the connector is separately approved.
- Let AI make autonomous changes, trigger deployments, approve workflows, or modify credentials.
- Train, fine-tune, upload datasets, or opt into model improvement with company or client material.

## Employee Launch Message Content

The launch message should include:

- Which tools are approved.
- Which data classes are allowed.
- Which data classes are prohibited.
- Examples of acceptable and unacceptable prompts.
- Whether prompts, outputs, files, and usage logs are retained.
- Who can access logs and for which purposes.
- How to request a restricted use case.
- How to report accidental disclosure, bad output, or suspected misuse.

## First 30-Day Review

The first review should answer:

- Which tools were used and by whom at an aggregate level.
- Whether any prohibited data was reported or detected.
- Whether employee questions indicate unclear guidance.
- Whether any restricted use cases should enter intake.
- Whether any connector, plugin, browser extension, or desktop-agent request was blocked.
- Whether costs or usage volumes suggest a budget control is needed.
- Whether the registry rows need status, owner, retention, or review-date updates.

## Exit Criteria For Phase 2

Do not move to controlled internal workflows until:

- Phase 1 has no unresolved high-severity incidents.
- Registry owners and review cadence are working.
- Employee notice and support path are operating.
- DPIA trigger triage is operating.
- Security can verify logging, access controls, and retention settings.
- Restricted workflow intake has been tested with at least one non-client-data use case.

## Evidence References

- CLAIM-001 through CLAIM-004 for data protection, provider, transfer, and DPIA controls.
- CLAIM-009 through CLAIM-011 for employee-facing AI rollout controls.
- CLAIM-014 through CLAIM-047 for provider-specific route constraints.
- CLAIM-055 through CLAIM-061 for Delivery Pipeline Systems red lines.

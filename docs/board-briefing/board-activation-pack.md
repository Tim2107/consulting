# Board Activation Pack

Status: board-ready draft. This pack converts the current research dossier into a first set of board decisions, owners, and go-live conditions.

## Purpose

The board now has enough evidence to approve an initial AI governance baseline. The next decision should not be another provider comparison; it should be whether the company is ready to activate Phase 1 under controlled rules.

## Recommended Board Outcome

Approve a controlled Phase 1 launch with the following position:

- Adopt the Approved AI Tool Registry and Data-Class Routing Policy as the operating controls for AI use.
- Permit Phase 1 low-risk productivity only in approved tools and only with public, approved-for-public, or non-confidential internal data.
- Keep Client Confidential Data out of third-party AI routes unless a route-specific exception passes the Client Contract Compatibility Check, Provider Stack review, processing-location review, retention/training-use review, and Security approval.
- Treat Delivery Pipeline Systems as Restricted-by-Default and allow AI-assisted actions only through approved Technically Gated Action levels.
- Fund only planning or a staged pilot for the 70-user self-hosted RAG option until owners, budget cap, support model, data sources, and security controls are approved.
- Keep training and fine-tuning on company or client material prohibited by default.
- Assign named owners before any employee-wide rollout.

## Decisions For Approval

| Decision | Recommended Board Action | Practical Effect | Evidence |
| --- | --- | --- | --- |
| DEC-001: Phase 1 approved tools | Approve Option B: low-risk use through registry-listed tools only. | Employees can use approved tools for low-risk productivity, but not for protected data. | CLAIM-014 through CLAIM-054 |
| DEC-002: Client Confidential Data in third-party AI | Approve route-specific gated exceptions only. | No blanket approval; each client-data workflow needs contract, provider, location, retention, and security review. | CLAIM-002, CLAIM-003, CLAIM-016, CLAIM-022, CLAIM-025, CLAIM-026, CLAIM-032, CLAIM-033, CLAIM-040, CLAIM-042, CLAIM-050 |
| DEC-003: Routing constraints | Approve the routing principle, not every route. | Bedrock, Azure, Vertex, and similar routes must be approved by exact operating party, endpoint, geography, retention, and feature set. | CLAIM-016, CLAIM-017, CLAIM-018, CLAIM-025, CLAIM-026, CLAIM-032, CLAIM-033, CLAIM-034 |
| DEC-004 and DEC-017: Self-hosted RAG pilot | Approve design funding and choose a planning band before build-out. | The 70-user option can proceed as RAG-first, with no default training or fine-tuning. | CLAIM-048 through CLAIM-054 |
| DEC-005: Delivery Pipeline Systems | Approve Technically Gated Actions as the only automation path. | AI may assist delivery work only through defined TGA levels, human gates, scoped identity, temporary credentials, policy checks, audit evidence, and rollback. | CLAIM-055 through CLAIM-061 |
| DEC-006: Training or fine-tuning | Confirm prohibited-by-default. | Any training/fine-tuning on protected material needs separate board, legal, security, and client approval. | CLAIM-013, CLAIM-054 |
| DEC-007: Registry ownership | Approve the operating model owner roles. | Registry, route exceptions, security gates, legal review, employee transparency, and platform operations get named accountability. | CLAIM-002, CLAIM-003 |
| DEC-008: Employee rollout review | Approve employee transparency and HR/labor review as rollout gates. | Employee-facing tools cannot roll out broadly until notices, logging purposes, access, retention, and local consultation needs are reviewed. | CLAIM-004, CLAIM-009, CLAIM-010, CLAIM-011 |
| DEC-009: DPIA trigger ownership | Assign Legal/Data Protection as accountable owner with Security and Business input. | DPIA trigger decisions are made before high-risk personal-data, employee-monitoring, profiling, or automated decision-support workflows. | CLAIM-004 |

## Immediate Phase 1 Boundary

Approved in Phase 1:

- Drafting, summarization, brainstorming, translation, formatting, and low-risk knowledge lookup.
- Public, approved-for-public, and non-confidential internal data.
- Approved registry tools only.
- Human-reviewed outputs only.

Not approved in Phase 1:

- Client Confidential Data.
- Client source code, regulated financial-sector client data, production data, client contracts, or secrets.
- Delivery Pipeline Systems actions beyond read-only assistance or draft-only suggestions.
- Autonomous actions, direct production changes, or credential changes.
- Training, fine-tuning, or creation of model-improvement datasets from company or client material.

## Activation Conditions

Before Phase 1 goes live, the board should require:

| Condition | Owner Type | Required Output |
| --- | --- | --- |
| Registry ownership assigned | AI Governance Owner | Named owner, deputies, monthly review cadence. |
| Phase 1 tool list confirmed | AI Governance Owner and Security | Registry rows marked with owner, status, data classes, review date. |
| Employee notice ready | HR / Legal / Data Protection | Employee AI Transparency Notice for approved tools. |
| DPIA trigger path ready | Legal / Data Protection | DPIA triage rule and escalation path. |
| Client-data exception path ready | Legal / Data Protection and Security | Client Contract Compatibility Check and route-exception workflow. |
| Security controls confirmed | Security | SSO/MFA, access controls, logging, retention, secrets rule, incident path. |
| Training issued | AI Governance Owner | Employee guidance covering allowed use, prohibited data, red lines, and reporting path. |
| Exception board path ready | Board Sponsor | Red Line exception process and meeting cadence. |

## Recommended Approval Wording

> The board approves a controlled Phase 1 AI rollout. The Approved AI Tool Registry and Data-Class Routing Policy are adopted as operating controls. Phase 1 use is limited to approved tools and public, approved-for-public, or non-confidential internal data. Client Confidential Data, secrets, client contracts, autonomous actions, and training or fine-tuning on protected material remain prohibited unless a separate board-approved exception applies. Client Confidential Data may leave the Company-Controlled Environment only through a route-specific gated approval. Delivery Pipeline Systems may use AI only through approved Technically Gated Actions. The board assigns owners for registry governance, legal/data-protection review, security review, employee transparency, platform operations, and business use-case approval before rollout.

## Board Meeting Pack

Use these artifacts together:

- [Decision Packet: Initial AI Tool Registry And Client Data Routing](./decision-packet-dec-001-dec-002.md)
- [Decision Packet: Delivery Pipeline Systems And Technically Gated Actions](./decision-packet-dec-005-delivery-pipeline-actions.md)
- [70-User Self-Hosted RAG Pilot Proposal](./self-hosted-rag-pilot-proposal.md)
- [Recommendation Matrix](./recommendation-matrix.md)
- [Decision Backlog](./decision-backlog.md)
- [Approved AI Tool Registry](../operational-policy/approved-ai-tool-registry.md)
- [AI Governance Operating Model](../operational-policy/ai-governance-operating-model.md)
- [Phase 1 Go-Live Checklist](../operational-policy/phase-1-go-live-checklist.md)

## Open Items After Approval

- Fill named owners and review dates in the registry.
- Decide the self-hosted RAG pilot planning band and budget cap.
- Convert the Employee AI Transparency Notice template into tool-specific notices.
- Finalize the DPIA trigger checklist and client-data exception workflow.
- Decide provider-specific connector boundaries for Microsoft 365 Copilot, Gemini Enterprise/Workspace, Grok Business/Enterprise, and ChatGPT Enterprise.

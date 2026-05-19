# Decision Packet: Initial AI Tool Registry And Client Data Routing

Status: board-ready draft for discussion. This packet proposes decisions for DEC-001 and DEC-002 based on the current provider profiles, evidence register, recommendation matrix, and operational-policy drafts.

## Decisions Requested

The board should decide whether to:

1. Adopt the Approved AI Tool Registry as the operational control point for AI tool use.
2. Approve the first data-class routing policy.
3. Confirm the Red Lines that apply immediately.
4. Assign owners for the registry, legal review, security review, employee transparency, and platform operations.
5. Decide the default rule for Client Confidential Data leaving the Company-Controlled Environment.

## Recommended Board Resolution

Approve the following initial policy position:

- The Approved AI Tool Registry is the single operational source for permitted AI tools, provider routes, use cases, data classes, routing constraints, and required controls.
- Public and approved-for-public data may be used in approved tools for general productivity and knowledge retrieval.
- Internal non-confidential and company confidential data may be used only in registry-listed enterprise, API, managed-private, or self-hosted routes after the required controls are satisfied.
- Client Confidential Data may not be submitted to consumer tools, personal accounts, free developer tiers with product-improvement use, grey-market gateways, or unapproved plugins/extensions.
- Client Confidential Data may leave the Company-Controlled Environment only through a specific registry route approved for that workflow, after Client Contract Compatibility Check, Provider Stack review, processing-location review, DPA/subprocessor/transfer review, retention/training-use review, and Security approval.
- Training or fine-tuning on company or client material remains prohibited by default and requires explicit board, legal, security, and client approval.
- Delivery Pipeline Systems remain Restricted-by-Default; AI may assist only through approved tools and technically gated actions.
- The 70-user self-hosted RAG option should be developed as the high-assurance reference path for workflows where Client Confidential Data must remain inside the company or client-controlled boundary.

## DEC-001: Which AI Tools Are Approved For Phase 1?

### Proposed Resolution

Approve Phase 1 as a low-risk productivity phase with the following boundaries:

- Approved scope: public data, approved-for-public data, and non-confidential internal drafts.
- Approved use levels: draft assistance, summarization, brainstorming, translation, formatting, and low-risk knowledge lookup.
- Not approved in Phase 1: Client Confidential Data, source code from client projects, Delivery Pipeline Systems data, secrets, credentials, client contracts, autonomous actions, and training/fine-tuning datasets.
- Tool eligibility: only tools listed in the Approved AI Tool Registry may be used. Each tool remains subject to its registry row, owner, review date, and controls.

### Initial Phase 1 Statuses

| Category | Recommended Phase 1 Status | Notes |
| --- | --- | --- |
| Consumer AI tools and personal accounts | Prohibited | No company or client work. |
| Free developer tiers with product-improvement data use | Prohibited for protected data | Public demos only if separately approved. |
| Enterprise productivity tools | Restricted | Public and internal non-confidential data only until owners and controls are confirmed. |
| Approved provider APIs | Restricted | May support controlled internal workflows; no Client Confidential Data until per-route approval. |
| Workspace copilots and enterprise search | Restricted / Needs Decision for client data | Connector and permission posture must be reviewed before Client Confidential Data. |
| Self-hosted or managed-private routes | Restricted | Requires platform owner, security architecture, model/license review, logging/retention controls, and cost profile. |
| Training or fine-tuning on protected material | Prohibited by default | Requires separate exception approval. |

### DEC-001 Options

| Option | Description | Pros | Risks | Recommendation |
| --- | --- | --- | --- | --- |
| A | Keep all AI use prohibited until every provider route is fully approved. | Maximum caution. | Blocks low-risk productivity and delays governance learning. | Not recommended. |
| B | Approve Phase 1 low-risk use through registry-listed tools only. | Enables useful work while preserving gates for sensitive data. | Requires clear communication and owner assignment. | Recommended. |
| C | Broadly approve enterprise AI tools for internal use. | Fastest adoption. | Too much ambiguity around data classes, connectors, logs, and employee transparency. | Not recommended. |

## DEC-002: May Client Confidential Data Ever Go To Approved Third-Party Providers?

### Proposed Resolution

Approve the principle that Client Confidential Data **may** go to a third-party AI provider only as a gated exception, not as a blanket approval.

The default answer remains **no** unless all of the following are true:

- The workflow is recorded in the AI Use Case Intake.
- The tool/provider route is listed in the Approved AI Tool Registry for the relevant use case and data class.
- Client Contract Compatibility Check confirms that the client contract, SOW, security appendix, DPA, outsourcing terms, and confidentiality obligations allow the proposed processing.
- Provider Stack review identifies model provider, product provider, infrastructure provider, AI compute provider, subprocessors, and support-access paths.
- Processing Location and Provider Routing Constraint are documented and technically enforceable where required.
- Retention, logging, abuse monitoring, training-use, and deletion settings are approved.
- Security approves access controls, secrets handling, audit logging, incident response, and exit plan.
- Employee AI Transparency Notice is complete if employee prompts, work content, telemetry, or identity data are processed.

### DEC-002 Options

| Option | Description | Pros | Risks | Recommendation |
| --- | --- | --- | --- | --- |
| A | No Client Confidential Data may leave the Company-Controlled Environment. | Strongest confidentiality posture; simpler message to clients. | May block useful approved provider routes and create pressure for unmanaged workarounds. | Use for highest-sensitivity clients or where contracts require it. |
| B | Client Confidential Data may leave only through route-specific gated approval. | Balanced; supports Bedrock/Azure/Vertex/xAI enterprise routes when evidence and controls are sufficient. | Requires disciplined review and technical enforcement. | Recommended default. |
| C | Any approved enterprise provider may process Client Confidential Data. | Easiest operationally. | Too broad; ignores routing, retention, subprocessors, client contracts, and feature-specific caveats. | Not recommended. |

## Immediate Red Lines To Confirm

- No Client Confidential Data in consumer AI tools or personal accounts.
- No Client Confidential Data in free tiers that use data for product improvement.
- No secrets, credentials, keys, or production tokens in AI tools.
- No client contracts in AI tools unless a future policy exception explicitly permits it.
- No training or fine-tuning on company/client material without explicit exception approval.
- No autonomous Delivery Pipeline Systems actions unless approved as Technically Gated Actions.

## Owner Assignments Needed

| Role | Responsibility | Recommended Owner Type |
| --- | --- | --- |
| Registry Owner | Maintains Approved AI Tool Registry, review dates, statuses, and allowed data classes. | Security, IT governance, or AI governance office |
| Legal / Data Protection Owner | Reviews DPA, subprocessors, SCCs/transfers, DPIA triggers, and client-contract compatibility. | Legal, DPO, privacy counsel |
| Security Owner | Reviews technical controls, logging, secrets handling, routing enforcement, and incident response. | Security lead or CISO function |
| Platform Owner | Owns self-hosted/managed-private architecture, operations, monitoring, and cost telemetry. | Platform engineering or infrastructure |
| Employee Transparency Owner | Owns Employee AI Transparency Notice and labor/works-council coordination. | HR, Legal, or People Operations |
| Business Use-Case Owner | Owns each workflow's purpose, users, data class, output use level, and acceptance criteria. | Relevant delivery or business lead |

## Approval Wording

Recommended wording for the board minutes:

> The board approves the first operational AI governance baseline: the Approved AI Tool Registry and Data-Class Routing Policy are adopted as draft operating controls. Phase 1 AI use is limited to approved tools and public or non-confidential internal data. Consumer AI tools, personal accounts, unapproved plugins, secrets, client contracts, and training/fine-tuning on protected material remain prohibited. Client Confidential Data may be processed by a third-party AI provider only after route-specific approval, client-contract compatibility review, provider-stack and processing-location review, retention/training-use review, and Security approval. The board assigns owners for registry maintenance, legal/data protection review, security review, employee transparency, and platform operations.

## Follow-On Decisions

After DEC-001 and DEC-002, the next board decisions should be:

- DEC-003: Which provider routing constraints are sufficient for sensitive workflows?
- DEC-004 and DEC-017: Whether to fund the 70-user self-hosted RAG pilot, and with what monthly budget cap and service level.
- DEC-005: Which Technically Gated Actions are acceptable in Delivery Pipeline Systems?
- DEC-008 and DEC-009: Employee AI Transparency Notice, labor/works-council handling, and DPIA trigger ownership.
- DEC-013, DEC-014, and DEC-016: Workspace copilot, Gemini, and Grok connector/agent boundaries.

## Supporting Artifacts

- [Approved AI Tool Registry](../operational-policy/approved-ai-tool-registry.md)
- [Data-Class Routing Policy](../operational-policy/data-class-routing-policy.md)
- [Recommendation Matrix](./recommendation-matrix.md)
- [Provider Comparison Table](./provider-comparison-table.md)
- [Decision Backlog](./decision-backlog.md)
- [Red Lines And Gated Exceptions](./red-lines-and-gated-exceptions.md)

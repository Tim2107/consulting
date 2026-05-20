# AI Governance Situational Awareness Summary

Status: repo-safe handoff summary. This file is designed for a CTO, reviewer, or fresh AI session to read first after cloning the repo.

## How To Use This File

Feed this file together with [CONTEXT.md](../CONTEXT.md) into the next AI session. Then point the session to the specific artifacts listed below. This summary is intentionally high-context and low-detail: it orients the reader without duplicating the full research dossier.

## Public Repo Boundary

Do not add real employee names, client names, client contracts, contract excerpts, credentials, tenant IDs, security configurations, private budgets, or internal staffing decisions to this public repo.

Keep the following in private working documents or internal systems:

- named owners and deputies
- client-specific contract compatibility results
- client approvals or client objections
- actual DPA/procurement documents not already public
- tool tenant settings, account IDs, support contacts, or security configuration exports
- final budget approvals and commercial quotes
- employee-specific telemetry, HR conclusions, or works-council correspondence

The public repo should keep reusable governance structure, source-backed research, templates, red lines, and decision options.

## Project Goal

The project builds an AI governance dossier for a software consulting company serving financial-sector clients. The central question is how to adopt AI tools while protecting Client Confidential Data, employee privacy, software-delivery systems, and contractual obligations.

The current material is not a legal opinion and does not approve production use by itself. It gives the board and operational owners a structured basis for decisions.

## Current State

The repo now contains:

- board-ready decision packets for the initial registry/routing decisions and Delivery Pipeline Systems
- provider research on Anthropic/AWS, OpenAI/Microsoft, Google/Vertex/Gemini, xAI/Grok, and self-hosted/open-weight options
- an evidence register mapping claims to primary or authoritative sources
- an operational policy draft with registry, routing policy, intake template, employee notice template, and technical-gate policy
- an activation layer for moving from research to Phase 1 rollout

The decision backlog marks DEC-001 through DEC-009 and DEC-017 as **Ready For Board**, not approved. The next real-world step requires interaction with company stakeholders, so the public repo should stop short of filling names and private facts.

## Core Terms

Use the terms in [CONTEXT.md](../CONTEXT.md). The most important ones are:

- **Client Confidential Data**: confidential client information, regulated data, production data, client documents, and personal data inside client material.
- **Company-Controlled Environment**: systems or vendor configurations where the company controls access, retention, security policy, and contractual safeguards.
- **Provider Stack**: model provider, application/product provider, AI compute provider, cloud/infrastructure provider, subprocessors, and support-access paths.
- **Provider Routing Constraint**: a required limit on which provider, geography, region, endpoint, or compute environment may process data.
- **Delivery Pipeline Systems**: source control, tickets, builds, tests, releases, deployments, and internal execution environments.
- **Technically Gated Action**: an AI-assisted action allowed only through enforceable controls such as human approval, scoped identity, temporary credentials, branch/environment protection, policy-as-code, logging, and rollback.

## Main Conclusions

1. The Approved AI Tool Registry should be the operational control point for AI use.
2. Phase 1 should allow only low-risk productivity in approved tools with public, approved-for-public, or non-confidential internal data.
3. Client Confidential Data should not leave the Company-Controlled Environment by default.
4. Client Confidential Data may use third-party AI only as a route-specific gated exception, after client-contract, provider-stack, processing-location, retention/training-use, and security review.
5. Consumer AI tools, personal accounts, unapproved plugins, free protected-data tiers with product-improvement use, grey-market gateways, secrets, client contracts, and protected-material training/fine-tuning are prohibited by default.
6. Provider routing claims must identify the operating party and route, not just the brand name of the model.
7. The 70-user self-hosted option should be RAG-first: the system should learn company internals through curated sources, access-controlled indexes, feedback, evaluations, and retrieval, not recurring base-model training.
8. Delivery Pipeline Systems are Restricted-by-Default. AI may assist only through defined Technically Gated Action levels.
9. Employee-facing AI rollout needs transparency, log-access boundaries, retention clarity, HR/labor review, and DPIA trigger ownership before broad rollout.

## Artifact Map

Start here:

- [CONTEXT.md](../CONTEXT.md): shared language and terms.
- [Board Activation Pack](./board-briefing/board-activation-pack.md): board-ready activation summary.
- [Decision Backlog](./board-briefing/decision-backlog.md): current decisions, status, and evidence references.

Board materials:

- [Decision Packet: Initial AI Tool Registry And Client Data Routing](./board-briefing/decision-packet-dec-001-dec-002.md)
- [Decision Packet: Delivery Pipeline Systems And Technically Gated Actions](./board-briefing/decision-packet-dec-005-delivery-pipeline-actions.md)
- [70-User Self-Hosted RAG Pilot Proposal](./board-briefing/self-hosted-rag-pilot-proposal.md)
- [Recommendation Matrix](./board-briefing/recommendation-matrix.md)
- [Provider Comparison Table](./board-briefing/provider-comparison-table.md)

Operational policy:

- [Approved AI Tool Registry](./operational-policy/approved-ai-tool-registry.md)
- [Data-Class Routing Policy](./operational-policy/data-class-routing-policy.md)
- [AI Governance Operating Model](./operational-policy/ai-governance-operating-model.md)
- [Phase 1 Go-Live Checklist](./operational-policy/phase-1-go-live-checklist.md)
- [AI Use Case Intake Template](./operational-policy/ai-use-case-intake-template.md)
- [Client Contract Compatibility Instructions](./operational-policy/client-contract-compatibility-instructions.md)
- [Employee AI Transparency Notice Template](./operational-policy/employee-ai-transparency-notice-template.md)
- [Technically Gated Actions For Delivery Pipeline Systems](./operational-policy/technically-gated-actions.md)

Research and evidence:

- [Evidence Register](./evidence-register/evidence-register.md)
- [Provider Index](./research-dossier/provider-index.md)
- [Anthropic/AWS Provider Profile](./research-dossier/provider-profiles/anthropic-aws.md)
- [OpenAI/Microsoft Provider Profile](./research-dossier/provider-profiles/openai-microsoft.md)
- [Google/Vertex/Gemini Provider Profile](./research-dossier/provider-profiles/google-vertex-gemini.md)
- [xAI/Grok Provider Profile](./research-dossier/provider-profiles/xai-grok.md)
- [Self-Hosted/Open-Weight Provider Profile](./research-dossier/provider-profiles/self-hosted-open-weight.md)
- [Technical Control Patterns](./research-dossier/technical-control-patterns.md)
- [Legal And Regulatory Baseline](./research-dossier/legal-and-regulatory-baseline.md)

## Provider Research Snapshot

Anthropic/AWS:

- Claude in Amazon Bedrock is the AWS-operated route.
- Claude Platform on AWS is Anthropic-operated despite AWS IAM, billing, and CloudTrail integration.
- Bedrock in-region, geographic cross-region, and global routing modes must be separated.

OpenAI/Microsoft:

- Direct OpenAI and ChatGPT Enterprise are OpenAI-operated and should not be assumed to be Azure-only.
- Azure OpenAI / Microsoft Foundry Models sold by Azure are the Microsoft-operated route for OpenAI models.
- Microsoft 365 Copilot is governed as a Microsoft 365 workflow with tenant, connector, agent, web-search, Purview, and model-option controls.

Google/Vertex/Gemini:

- Vertex AI regional or EU endpoints are the candidate Google-operated route for sensitive workflows.
- Vertex global endpoints should not be used where ML-processing location matters.
- Gemini Enterprise and Gemini for Workspace require feature-level governance for connectors, grounding, CSE, DLP, data regions, and regional processing.

xAI/Grok:

- xAI API and Grok Business/Enterprise are restricted candidates only under enterprise terms, DPA, ZDR/retention controls, regional/data-at-rest controls where needed, and feature allowlists.
- Consumer Grok and personal X/Grok use should remain prohibited for protected data.
- xAI/SpaceXAI should also be tracked as a possible compute-provider layer, but public compute announcements do not prove customer workload routing.

Self-hosted/open-weight:

- Open-weight does not automatically mean open-source AI.
- Model licenses require model-by-model legal review.
- RAG, permission-aware indexes, feedback, evaluations, and model routing should be the default way to learn company internals.
- Training and fine-tuning on company or client material remain outside the default budget and approval path.

## Decisions Ready For Board

- DEC-001: approve Phase 1 low-risk use through registry-listed tools only.
- DEC-002: allow Client Confidential Data in third-party AI only through route-specific gated exceptions.
- DEC-003: approve provider-routing principle, not blanket provider approval.
- DEC-004 and DEC-017: decide whether to fund the staged 70-user self-hosted RAG pilot and choose budget/service band.
- DEC-005: approve Technically Gated Actions as the only path for AI-assisted Delivery Pipeline Systems automation.
- DEC-006: confirm training/fine-tuning on protected material is prohibited by default.
- DEC-007: assign real governance owners privately.
- DEC-008: require employee transparency and HR/labor review before broad rollout.
- DEC-009: assign DPIA trigger ownership privately.

## Work To Keep Private Next

The next phase should be handled outside the public repo or with placeholders:

1. Name actual board sponsor, registry owner, security owner, legal/data-protection owner, employee transparency owner, platform owner, and business owners.
2. Pick the actual Phase 1 approved tool list based on contracts and tenant settings.
3. Fill registry owners and review dates in a private copy or internal governance system.
4. Decide whether any real client engagement can use Client Confidential Data in an AI workflow.
5. Run client-contract compatibility checks without uploading contracts into AI tools.
6. Decide the self-hosted RAG pilot budget cap and service level based on private quotes and capacity assumptions.
7. Convert the employee notice template into a company-specific notice after HR/legal/labor review.
8. Assign the DPIA triage owner and document the internal escalation path.

## Public Repo Work That Can Continue

If work continues in this public repo, good next candidates are:

- DEC-010: define minimum evidence required for Processing Location and Provider Routing Constraint claims.
- DEC-011 and DEC-012: expand DORA/NIS2 decision support without naming clients.
- DEC-013, DEC-014, and DEC-016: draft feature-level connector/agent policies for Microsoft 365 Copilot, Gemini Enterprise/Workspace, and Grok Business/Enterprise.
- generic employee launch guidance with placeholders only.
- generic technical implementation checklist for TGA controls.
- generic provider-evidence checklist for future vendors.

## Suggested Prompt For A Fresh AI Session

Use something like:

> You are continuing AI governance work for a software consulting company serving financial-sector clients. Read `CONTEXT.md` and `docs/situational-awareness-summary.md` first. Preserve the terminology in `CONTEXT.md`. Do not invent approvals, owners, client facts, contract positions, or private budget commitments. Treat all board decisions as draft or Ready For Board unless the repo explicitly says approved. Use the Evidence Register for claims, and use primary or authoritative sources for any new current facts.

## Suggested Skills Or Working Mode

- Use a handoff/continuity skill when passing work to another AI session.
- Use web or browser research only with primary law, regulator guidance, official vendor terms, or official product documentation for current facts.
- Use the GitHub workflow only after checking that the repo contains no real people, clients, credentials, or private contract details.

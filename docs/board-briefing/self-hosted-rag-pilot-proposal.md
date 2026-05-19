# 70-User Self-Hosted RAG Pilot Proposal

Status: board-ready draft for DEC-004 and DEC-017. This proposal assumes approximately 70 named users, 10-15 peak concurrent interactive sessions, business-hours priority, and no recurring base-model training or default fine-tuning.

## Decisions Requested

The board should decide whether to:

1. Fund a 70-user self-hosted RAG pilot.
2. Choose company-operated self-hosting, managed private deployment, or a staged hybrid pilot.
3. Set a monthly pilot budget cap and service level.
4. Assign platform, security, legal/data-protection, and business owners.
5. Confirm that "learning the company" means RAG, curated knowledge, access-controlled indexes, feedback, and evaluations, not training/fine-tuning model weights.

## Recommended Resolution

Approve a staged 70-user self-hosted RAG pilot with the following conditions:

- Scope the pilot to internal knowledge retrieval, software-delivery assistance, and selected client project analysis only after client-contract compatibility review.
- Use RAG, embeddings, access-control metadata, source citations, feedback, and evaluation as the system's learning mechanism.
- Keep base-model training and routine fine-tuning out of scope.
- Start with a managed or company-operated pilot that can run small and mid-size open-weight models behind an internal API.
- Require isolated indexes for each client or regulated engagement.
- Require cost telemetry by use case, model route, user group, token volume, retrieval volume, indexing job, and security/audit overhead.
- Run a buy-vs-rent review before scaling beyond the pilot.

## Pilot Goals

| Goal | Success Signal |
| --- | --- |
| Protect Client Confidential Data | No external fallback, no cross-client retrieval, and all prompts, embeddings, indexes, logs, backups, and monitoring stay inside the approved boundary. |
| Make company knowledge usable | Users can retrieve cited answers from approved internal sources with visible freshness and source links. |
| Improve software delivery support | Developers can ask questions over approved repositories, architecture notes, tickets, and runbooks without exposing secrets or client-isolated data. |
| Avoid expensive training runs | The system improves through ingestion quality, ranking, curated answers, prompt/routing updates, and evaluations. |
| Prove cost discipline | Monthly cost, cost per active user, cost per answered question, and cost by use-case category are tracked from day one. |

## Recommended Pilot Scope

### In Scope

- Internal knowledge retrieval over approved company documentation, runbooks, architecture decisions, project retrospectives, and policy drafts.
- Software-delivery assistance over approved repositories, design docs, tickets, and documentation.
- Client project analysis only in isolated client workspaces after Client Contract Compatibility Check.
- Drafting, summarization, classification, code explanation, source-grounded Q&A, and internal research synthesis.
- Feedback capture on answer usefulness, missing sources, stale sources, and hallucination reports.

### Out Of Scope

- Base-model training on company or client material.
- Routine fine-tuning on tickets, code, emails, chats, or client documents.
- Autonomous Delivery Pipeline Systems actions.
- Customer-facing production service operations.
- Client contracts and legal terms unless a future exception policy permits it.
- Secrets, credentials, production tokens, and unredacted highly sensitive fields.
- Cross-client indexing or cross-client learning.

## Architecture

| Layer | Recommended Pilot Design | Notes |
| --- | --- | --- |
| User access | SSO, MFA, RBAC, project/client groups | Access model must match source-system permissions. |
| Application | Internal chat/search UI plus OpenAI-compatible internal API | Keeps applications portable across model routes. |
| Model router | Small model for cheap tasks, mid-size model for RAG, optional queued large-model route | Prevents every request from consuming expensive capacity. |
| Model serving | vLLM, NIM, TGI, or equivalent serving stack | Use a supported runtime with auditability and operational ownership. |
| Retrieval | Vector/search index with source ACLs, metadata, citations, freshness, and deduplication | Retrieval permissions must be enforced server-side. |
| Connectors | Approved docs, wikis, repos, tickets, runbooks, and project folders | Start narrow; expand only after quality and permission tests pass. |
| Data isolation | Separate client indexes and workspaces | Default is no cross-client retrieval. |
| Observability | Prompt/output logs, retrieval logs, cost telemetry, model metrics, eval results | Retention and admin access must be approved. |
| Evaluation | Leakage, hallucination, citation quality, prompt injection, stale-source detection | Gate each rollout phase on eval results. |

## Rollout Plan

| Phase | Duration | Users | Data Scope | Exit Criteria |
| --- | --- | --- | --- | --- |
| Phase A: Design and source audit | 2 weeks | Platform/Security/Legal only | No production Client Confidential Data | Owners assigned; approved sources selected; threat model and retention plan complete. |
| Phase B: Internal knowledge pilot | 4-6 weeks | 10-15 users | Internal non-confidential and company confidential data | Permission tests pass; answer citation rate above target; no high-severity leakage findings. |
| Phase C: Delivery-team beta | 6-8 weeks | 30-40 users | Approved repos, tickets, runbooks, architecture docs | Developer usefulness and latency targets met; secrets scanning and repo-scope controls pass. |
| Phase D: 70-user controlled rollout | 8-12 weeks | Up to 70 named users | Internal data plus gated client workspaces | Cost cap respected; support process works; client-isolated workspace test passes. |
| Phase E: Client Confidential Data expansion | Board-gated | Selected users only | Specific client workspace only | Client Contract Compatibility Check and route-specific approval complete. |

## Budget Bands

These are planning bands, not procurement quotes. They exclude internal staff time unless noted and must be replaced by vendor quotes before spend approval.

| Band | Monthly Planning Cap | Fit | Typical Shape | Risks |
| --- | --- | --- | --- | --- |
| Band 0: Design only | EUR 0-2k external spend | Source audit, architecture, model/license shortlist | No persistent GPU; local experiments only with non-sensitive data | Does not prove user value or inference cost. |
| Band 1: Lean pilot | EUR 2k-8k external spend | 10-15 users, internal knowledge retrieval, small models | Time-boxed managed GPU or modest single-GPU path; CPU services for API/indexing | May underperform on long context, code, and document-heavy tasks. |
| Band 2: Recommended pilot | EUR 8k-25k external spend | 30-70 users with modest concurrency | 48GB-96GB GPU class path or equivalent managed capacity; separate storage/indexing/monitoring | Requires careful routing and queueing to avoid latency spikes. |
| Band 3: High-assurance pilot | EUR 25k-75k external spend | Client-isolated workspaces, stronger uptime, larger models | Multi-GPU or managed-private environment with redundancy and support | Can become expensive before value is proven. |
| Band 4: Training/fine-tuning exception | Not pre-approved | Only if board/legal/client approve | Dataset prep, training GPUs, evals, legal review, model governance | Excluded from pilot; high cost and high governance burden. |

## Cost By Use Case Category

| Use Case Category | Pilot Priority | Expected Cost Band | Cost Drivers | Default Decision |
| --- | --- | --- | --- | --- |
| General productivity | Low | Band 0-1 | UI, prompt templates, small model inference | Use approved enterprise tools unless self-hosting is needed for confidentiality. |
| Internal knowledge retrieval | Highest | Band 1-2 | Connectors, parsing, embeddings, vector/search index, citations | Primary pilot use case. |
| Software delivery | High | Band 2 | Repo indexing, longer context, code quality, IDE/workflow integration, secrets scanning | Include in beta after source controls pass. |
| Delivery Pipeline Systems | Low initially | Band 2-3 | Approval gates, policy-as-code, audit, rollback, deterministic tool use | Keep draft-assistance only until DEC-005. |
| Client project analysis | High but gated | Band 2-3 | Client isolation, OCR, long documents, audit, legal review, storage | Add only after client-contract and security gates. |
| Customer/service operations | Defer | Band 3 | SLA, 24/7 support, monitoring, guardrails, fallback, escalation | Out of pilot unless separate owner and SLA exist. |
| Training/fine-tuning | Excluded | Band 4 | Dataset prep, training GPUs, privacy/legal review, evals | Prohibited by default. |

## Success Metrics

| Metric | Target For Pilot |
| --- | --- |
| Active adoption | At least 50% of invited users use the system weekly by Phase D. |
| Answer usefulness | At least 70% positive user rating on sampled knowledge answers. |
| Citation coverage | At least 90% of knowledge answers include cited sources. |
| Permission correctness | 100% pass rate on seeded access-control tests before Client Confidential Data. |
| Leakage findings | Zero high-severity cross-client, secret, or unauthorized-source leaks. |
| Latency | Track p50 and p95 by model route; set final targets after Phase B baseline. |
| Cost visibility | 100% of requests tagged by use case, model route, user group, and workspace. |
| Freshness | Critical sources re-indexed within agreed source-specific windows. |
| Support burden | Named owner and response process in place before 70-user rollout. |

## Required Owners

| Owner | Responsibility |
| --- | --- |
| Platform Owner | Architecture, runtime, deployment, monitoring, capacity, cost telemetry, support process. |
| Security Owner | Threat model, access controls, secrets scanning, logging, incident response, client isolation. |
| Legal / Data Protection Owner | DPIA triggers, client-contract compatibility, model/license review, retention and employee transparency review. |
| Knowledge Owner | Source selection, taxonomy, freshness, accepted answers, documentation cleanup. |
| Delivery Lead | Software-delivery use cases, repo scope, developer workflow, success metrics. |
| Board Sponsor | Budget cap, escalation, phase gates, and go/no-go decisions. |

## Phase Gates

The pilot should not move to the next phase unless:

- Owners are assigned and active.
- Registry row is updated with owner, review date, and allowed data classes.
- Data sources are inventoried and approved.
- Access-control tests pass.
- Logging, retention, and admin access are configured.
- Secret scanning and DLP checks are active for indexed sources.
- Evaluation suite has no high-severity failures.
- Cost telemetry is working.

## Proposed Board Approval Wording

> The board approves a staged 70-user self-hosted RAG pilot as the high-assurance reference path for AI workflows where data must remain inside a company or client-controlled boundary. The pilot may learn company internals only through retrieval, curated knowledge, feedback, evaluations, and controlled memory; base-model training and routine fine-tuning remain out of scope. The board sets an initial monthly external-spend cap of [insert cap], assigns Platform, Security, Legal/Data Protection, Knowledge, Delivery, and Board Sponsor owners, and requires phase-gate approval before Client Confidential Data is included.

## Recommended Initial Board Choices

- Choose Band 2 as the planning target if the board wants the pilot to reach all 70 users.
- Choose Band 1 only if the goal is a smaller proof of value before committing to the 70-user scope.
- Choose Band 3 only if client-isolated workspaces or stronger availability are required from the beginning.
- Keep Band 4 excluded unless a separate training/fine-tuning exception is approved.

## Evidence References

- CLAIM-048: open-weight is not automatically open-source AI.
- CLAIM-049: open-weight model licenses vary materially.
- CLAIM-050: RAG supports specialized knowledge without retraining the LLM entirely.
- CLAIM-051: self-hostable serving patterns can expose OpenAI-compatible internal endpoints.
- CLAIM-052: GPU cost depends on memory, SKU, region, and commitment.
- CLAIM-053: 70-user phase should use RAG, routing, and small/mid-size models.
- CLAIM-054: training/fine-tuning stays outside the default budget.

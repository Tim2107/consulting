# Provider Profile: Self-Hosted / Open-Weight / Managed Private Deployment

Date accessed: 2026-05-19

Status: first-pass deployment profile. This is not a legal opinion and should be validated against the selected model license, hosting contract, hardware quote, cloud region, security architecture, client-contract constraints, and operational ownership model before policy approval.

## Executive Conclusion

For roughly **70 named users**, self-hosted or managed-private AI should be treated as an internal platform product rather than a one-off model install.

The recommended first-pass posture is:

- Use self-hosting primarily when Client Confidential Data, source code, or internal knowledge cannot leave the approved company or client-controlled environment.
- Make **retrieval-augmented generation (RAG)**, embeddings, metadata, access-control trimming, and curated feedback the way the system "learns the company over time."
- Do **not** plan recurring base-model training or expensive fine-tuning runs. Training and fine-tuning on company/client material should remain a board/legal/client exception path.
- Size the pilot for 70 named users but only measured active concurrency. A reasonable first pilot assumption is 70 users, 10-15 concurrent interactive sessions at peak, business-hours priority, and queued batch jobs.
- Start with a two-tier model pattern: a small/fast model for routing, classification, extraction, and cheap drafts; and a mid-size model for RAG answers, code explanation, and client-document analysis. Add a large model only for clearly justified use cases.

Self-hosting improves control over prompts, files, logs, indexes, and processing location. It does not remove governance duties. The company becomes the operator responsible for model selection, patching, security, access controls, logging, output risk, licensing, data protection, incident response, and cost control.

## 70-User Target Architecture

### Recommended Shape

- Identity and access:
  - SSO, MFA, RBAC, project/client groups, and per-source permission sync.
  - User, team, and client/workspace boundaries must be represented in retrieval metadata.
- Knowledge ingestion:
  - Connectors for approved repositories, wikis, ticket systems, document stores, and client project folders.
  - Chunking, OCR/document parsing, embeddings, metadata extraction, and deduplication.
  - Separate indexes for internal company data and each client or regulated engagement unless Legal/Security approves shared indexing.
- Company memory:
  - RAG corpus, curated playbooks, glossary, architecture decisions, project retrospectives, and accepted-answer library.
  - Feedback loops that improve retrieval, prompts, source ranking, taxonomy, examples, and documentation quality.
  - Optional user/team memory only with opt-in, owner, purpose, expiry, export, and deletion controls.
- Model serving:
  - OpenAI-compatible serving layer where possible for portability.
  - Small model for low-risk/low-cost tasks.
  - Mid-size model for internal assistant and RAG.
  - Optional large model as a queued or premium route, not default.
- Controls:
  - No cross-client retrieval.
  - Source citations for knowledge answers.
  - Secrets/DLP filters before indexing and before sending prompts to the model.
  - Audit logs, prompt/output retention rules, admin-access controls, and incident workflow.
  - Evaluation suite for retrieval quality, hallucination, refusal behavior, data leakage, and code/security risks.

### What "Learning The Internals" Means

Approved meaning:

- The system indexes approved internal knowledge and retrieves relevant context at inference time.
- The company curates canonical answers, glossary terms, architecture patterns, project playbooks, and examples.
- Feedback improves search ranking, retrieval filters, prompts, routing, and documentation.
- Periodic evaluations identify missing documentation and stale or conflicting knowledge.

Not approved by default:

- Full base-model training on company or client material.
- Routine fine-tuning on client documents, source code, tickets, emails, or chat logs.
- Persistent personal memory without explicit user transparency and deletion controls.
- Cross-client learning where one client's materials improve another client's answers.

## Option Comparison

| Option | Operating party | Model/license posture | Processing location | Cost posture | 70-user fit |
| --- | --- | --- | --- | --- | --- |
| Company-operated self-hosted stack | Company | Model-specific open-weight or commercial license | Company data center, approved cloud VPC, or client environment | Upfront hardware or fixed GPU rental plus operations | Strong fit when data control matters and internal ops ownership exists. |
| Managed private deployment in cloud | Cloud provider / managed AI platform plus company controls | Open-weight or commercial model under cloud/platform terms | Selected cloud region/VPC; provider/subprocessor review still required | Ongoing GPU hourly/committed spend; easier burst scaling | Good pilot or burst option, but can become expensive for steady 70-user usage. |
| Supported inference appliance/runtime | Company plus vendor support | Vendor-packaged open/commercial models | Company or client infrastructure | License/support plus hardware | Good if the company wants support/SLA without building all runtime pieces. |
| Third-party enterprise API plus private RAG | Third-party model provider plus company RAG layer | Provider terms | Provider route plus company-controlled index | Lower ops burden; token usage cost | Useful fallback for non-confidential or approved confidential workflows, but not self-hosted. |
| Base-model training or repeated fine-tuning | Company or specialist vendor | Training data/license risk | Training cluster location | Very high and hard to bound | Not recommended for 70-user first phase. Keep as exception. |

## Model And Runtime Posture

### Model Families

- Llama-class models: useful ecosystem and tooling, but Meta's Llama license is a community license with acceptable-use and additional commercial terms. Treat as source-available/open-weight, not automatically OSI-open.
- Mistral-class models: several open-weight models are available under Apache 2.0 and can be deployed on compatible hardware; model-specific licenses still need review.
- Qwen-class models: Qwen3 documentation states its open-weight models are Apache 2.0, with vLLM and TensorRT-LLM deployment examples. Review model variant, jurisdiction, and client acceptance.
- DeepSeek-class models: some models have permissive licenses or model-specific licenses, but each release must be reviewed separately; do not treat all DeepSeek-family models as one legal posture.
- Specialist models: embeddings, rerankers, code models, OCR, speech, and vision models have separate licenses and data-flow behavior.

### Runtime

- vLLM, TensorRT-LLM, TGI, NVIDIA NIM, and similar runtimes can provide production-serving patterns.
- Prefer OpenAI-compatible APIs where possible so applications can switch between self-hosted and approved external providers.
- Use model routing so cheap tasks do not consume large-model capacity.
- Keep batch ingestion, OCR, embedding generation, and evaluation jobs off the interactive inference path.

## Cost Profile For 70 Users

### Sizing Assumptions

These are planning assumptions, not a hardware quote:

- 70 named users.
- 10-15 concurrent interactive sessions at peak.
- Business-hours priority; after-hours batch indexing allowed.
- Most value comes from internal RAG and code/project support, not from frontier-model parity.
- No recurring base-model training.
- Fine-tuning is not part of the default budget.

### Cost By Use Case Category

| Use case category | Recommended self-host pattern | Relative cost | Main cost drivers | Governance note |
| --- | --- | --- | --- | --- |
| General productivity | Small model, templates, no confidential data by default | Low | Inference, UI, prompt library | Often cheaper to keep external approved tools for non-confidential work. |
| Internal knowledge retrieval | RAG over company docs, tickets, wikis, code docs | Low to Medium | Connectors, parsing/OCR, embeddings, vector/search index, citations | Best fit for "learn the company" without training. |
| Software delivery | Code-aware RAG, repo indexing, small/mid code model | Medium | Longer context, code model quality, IDE integration, secrets scanning | Requires source-code controls and no secret leakage into logs/indexes. |
| Delivery Pipeline Systems | Tool-gated assistant, policy checks, human approval | Medium to High | Audit, deterministic tools, evals, approval workflow, CI/CD integration | Inference cost is secondary to safety and release-control engineering. |
| Client project analysis | Per-client isolated RAG and document analysis | High | Tenant isolation, OCR, long documents, audit, review, storage, legal controls | Strong self-host candidate when client data cannot leave approved boundary. |
| Customer/service operations | Production assistant or agent with SLA | High | 24/7 reliability, monitoring, guardrails, fallback, escalation, QA | Requires production support owner and incident process. |
| Training/fine-tuning on company/client material | Not in default plan | Very High / Exception | Dataset prep, GPUs, privacy/legal review, evals, model governance | Keep red-lined unless board/legal/client approve. |

### Infrastructure Cost Shape

For a 70-user pilot, avoid sizing around a large always-on model first. Prefer a measured pilot:

- **Lean pilot:** one modest GPU path for 7B-14B class models, plus CPU services for API, vector DB, ingestion, and monitoring. Good for internal Q&A, summarization, classification, and routing; not enough for high-quality long-context analysis.
- **Recommended pilot:** one 48GB-96GB GPU class path or equivalent managed GPU capacity for mid-size models, plus separate CPU/indexing services. Good balance for 70 named users if concurrency is modest and large jobs are queued.
- **High-assurance / high-quality path:** multiple GPUs or cloud H100/A100 capacity for larger models, longer contexts, and redundancy. Use only for client-confidential or high-value workflows that justify the cost.

Official pricing pages show why training-grade cloud capacity should not be the default for 70 users: AWS lists p5.48xlarge Capacity Blocks with 8 H100 accelerators at tens of USD per instance-hour, and newer B200/H200 capacity is higher. Google and Azure GPU pricing is similarly SKU, region, commitment, and availability dependent. This reinforces the no-expensive-training-run posture.

## Provider Stack And Processing Location

- AI model provider: selected model publisher, such as Meta, Mistral, Qwen/Alibaba Cloud, DeepSeek, NVIDIA, or another model author.
- Application or product provider: the company if it builds the assistant; otherwise the managed private deployment vendor.
- AI compute provider: company-operated hardware, cloud GPU provider, colocation provider, or managed private deployment provider.
- Cloud or infrastructure provider: company data center, client environment, or selected cloud/region.
- Contracting party: model publisher license plus runtime/vendor/cloud terms.
- Data processor or controller position: company is usually operator/controller or processor for client personal data; cloud/managed providers may be subprocessors.
- Processing locations: company-selected infrastructure only if all inference, embeddings, logs, backups, monitoring, and support access stay inside that boundary.
- Provider routing constraints:
  - Deny fallback to external APIs unless the fallback provider is approved for the specific data class.
  - Keep embeddings and reranking inside the same approved boundary as generation for Client Confidential Data.
  - Keep client indexes separate unless the board approves shared tenancy.
- Retention and training-use terms:
  - Self-hosting can avoid provider training use, but logs, indexes, backups, and feedback stores become company-managed retention surfaces.
  - No training/fine-tuning on company or client material by default.
- Employee AI Privacy implications: high. Internal assistants may process employee prompts, files, tickets, emails, repository activity, and usage logs. Transparency notice and labor review remain required.
- Uncertainty gaps: exact model, license, benchmark quality, hardware quote, cloud region, SLA, concurrency, logging retention, connector list, client-contract constraints, and support owner.

## Governance Recommendation

For the board:

1. Approve a **70-user self-hosted RAG pilot** only if an accountable platform owner is named.
2. Approve "learning the company" only as RAG, curated knowledge, feedback, taxonomy, and evaluations.
3. Keep training and fine-tuning on company/client material as a separate red-line exception.
4. Start with internal knowledge retrieval, software delivery assistance, and client project analysis where confidentiality justifies the cost.
5. Do not promise frontier-model quality from self-hosting. Measure task quality, latency, and cost before expanding.
6. Require a buy-vs-rent review after the pilot: steady business-hours usage may favor owned or committed capacity; bursty heavy analysis may favor managed cloud GPU.

## Minimum Controls Before Sensitive Use

- Select approved model families and record license obligations.
- Maintain a model inventory with version, checksum, license, source, evaluation status, and approved use cases.
- Keep all Client Confidential Data processing inside approved infrastructure, including embeddings, logs, indexes, backups, and monitoring.
- Enforce source ACLs during retrieval; do not rely only on UI permissions.
- Isolate client indexes and workspaces.
- Redact secrets and highly sensitive fields before indexing where possible.
- Set prompt/output/log retention and admin-access controls.
- Use source citations and confidence/retrieval diagnostics for knowledge answers.
- Run leakage, hallucination, prompt-injection, and jailbreak tests before rollout.
- Add cost telemetry by use case, model, user group, token volume, retrieval volume, and batch job.

## Evidence

### Current Facts

- The Open Source AI Definition distinguishes open-source AI from merely open weights by requiring sufficient data information, code, and parameters in the preferred form for modification. Sources: SRC-078.
- Mistral documentation says open-weight models under Apache 2.0 can be deployed on compatible hardware, including single-GPU to multi-node configurations. Sources: SRC-079.
- Qwen3 documentation states its open-weight models are Apache 2.0 and includes vLLM/TensorRT-LLM OpenAI-compatible deployment examples. Sources: SRC-080.
- Meta's Llama 4 license grants limited rights under a community license with acceptable-use and additional commercial terms. Sources: SRC-081.
- RAG lets a model reference authoritative custom documents outside its training data before generating a response, and NVIDIA describes RAG as integrating specialized knowledge without retraining the LLM entirely. Sources: SRC-083, SRC-084.
- vLLM provides an OpenAI-compatible serving API, and NVIDIA NIM provides containerized inference microservices that can be self-hosted in cloud, data center, or workstation environments. Sources: SRC-085, SRC-086.
- NVIDIA L4 has 24GB GPU memory; NVIDIA RTX PRO 6000 Blackwell has 96GB memory; cloud GPU pricing varies by SKU, region, and commitment. Sources: SRC-087, SRC-088, SRC-089, SRC-090, SRC-091.

### Near-Term Developments

- Open-weight model quality, license posture, hardware support, and inference runtimes are changing quickly. Treat model choice, GPU sizing, and cost assumptions as current-date facts only.

### Speculation

- Any claim that self-hosting is automatically cheaper than third-party APIs is Speculation until actual workload volume, concurrency, model choice, support cost, and hardware utilization are measured.
- Any claim that an open-weight model is legally equivalent to open-source software is Speculation unless the model satisfies the selected open-source AI definition and license review.
- Any claim that RAG "learns" correctly over time is Speculation unless ingestion, ACLs, freshness, feedback, and evaluation processes are operating.
- Any claim that a regional cloud GPU keeps all Client Confidential Data in-region is Speculation unless logs, backups, support access, telemetry, images, and managed services are covered.

## Open Questions

- Which 70 users are in scope: all employees, delivery teams only, or client-facing teams?
- What peak concurrency and latency target should the pilot support?
- Which systems should become company knowledge sources first?
- Which client data classes are permitted in the pilot?
- Is the first deployment company-operated, managed private cloud, or client-environment hosted?
- Which model licenses are acceptable to Legal and to financial-sector clients?
- What monthly budget cap should trigger routing, throttling, or scale-down?
- Who owns 24/7 operations if customer/service operations become in scope?

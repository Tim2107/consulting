# Provider Profile: OpenAI / Microsoft

Date accessed: 2026-05-19

Status: first-pass provider profile. This is not a legal opinion and should be validated against executed contracts, DPAs, private offers, tenant configuration, Azure deployment type, Microsoft 365 admin settings, and current product documentation before policy approval.

## Executive Conclusion

The OpenAI/Microsoft question should be framed like the Anthropic/AWS question: identify the customer-facing service and operating party, not only the model brand.

Current primary-source conclusion:

- **Direct OpenAI API / ChatGPT Enterprise** is OpenAI-operated. OpenAI's own platform data controls, Enterprise privacy commitments, DPA, subprocessor list, and pricing apply. Direct OpenAI should not be treated as Azure-only processing: Microsoft is OpenAI's primary cloud partner, but OpenAI can serve products across any cloud provider and has announced major non-Microsoft infrastructure relationships.
- **Azure OpenAI / Microsoft Foundry Models sold by Azure** is Microsoft-operated. Microsoft says it hosts OpenAI models in Microsoft's Azure environment and that these services do not interact with OpenAI-operated services such as ChatGPT or the OpenAI API. For an "Azure-operated" posture analogous to Bedrock, Azure OpenAI / Foundry Models sold by Azure is the candidate route.
- **Microsoft 365 Copilot** is Microsoft-operated inside the Microsoft 365 service boundary and uses Azure OpenAI services for processing rather than OpenAI's public services. It inherits Microsoft 365 permissions, compliance, and data-residency commitments, but optional agents, web search, connectors, and non-OpenAI model options can change the data-flow and boundary analysis.
- **OpenAI compute partnerships** are relevant infrastructure facts but not sufficient proof of where a specific customer workload is processed. OpenAI/Microsoft's April 2026 partnership update and OpenAI/AWS infrastructure announcement show a multi-cloud capacity posture; provider profiles must still rely on customer-facing product docs and contract terms for routing decisions.

For workflows involving **Client Confidential Data**, the default board posture should be:

- Azure OpenAI / Microsoft Foundry regional or DataZone deployments: **candidate restricted option**, subject to Azure/Microsoft DPA review, deployment type enforcement, region/data-zone selection, logging/abuse monitoring review, and client-contract compatibility.
- Direct OpenAI API with approved data residency and Zero Data Retention or Modified Abuse Monitoring controls: **candidate restricted option**, but not Azure-only or Microsoft-operated.
- ChatGPT Enterprise / Business / Edu: **candidate approved third-party provider option** for lower-risk or controlled workflows after retention/admin/audit/connector configuration, employee transparency, DPA, and client-contract review.
- Microsoft 365 Copilot: **candidate controlled internal-workflow option** for Microsoft 365 data, but it requires tenant-permission cleanup, oversharing review, employee transparency, web/agent/connector governance, and special caution where Anthropic or other non-OpenAI models are enabled.

## Option Comparison

| Option | Operating party for inference | Main contracting/data terms | Routing and residency posture | Feature posture | Cost posture | First-pass governance fit |
| --- | --- | --- | --- | --- | --- | --- |
| Direct OpenAI API | OpenAI | OpenAI Services Agreement, DPA, platform data controls, subprocessors | OpenAI-operated. API data is not used for training by default. Abuse-monitoring logs are retained up to 30 days by default unless approved controls apply. Data residency is project-based and has eligibility/model/endpoint limitations. | Native OpenAI platform features, fastest access to OpenAI API capabilities. | OpenAI per-token pricing; Batch/Flex/Priority/Scale Tier; 10% uplift for listed regional-processing endpoints. | Restricted third-party provider candidate, not Microsoft-operated. |
| ChatGPT Enterprise / Business / Edu | OpenAI | OpenAI Enterprise privacy commitments, Service Terms, DPA where applicable | OpenAI-operated. Business data not used for model training by default. Enterprise customers can control retention; admins may access content/logs depending on plan and settings. | Strong end-user productivity product; connectors and GPTs/actions need separate governance. | Seat/subscription and enterprise terms; compliance/audit tooling may add operational cost. | Candidate for approved productivity workflows with no Client Confidential Data until governance approval. |
| Azure OpenAI / Microsoft Foundry Models sold by Azure | Microsoft | Microsoft Product Terms, Microsoft Products and Services DPA, Azure service terms, Foundry/OpenAI data privacy docs | Microsoft-operated. Microsoft says OpenAI models hosted in Azure do not interact with OpenAI-operated services. Regional, DataZone, and Global deployment types have different processing implications. | Enterprise Azure integration, private networking, Azure identity, Azure Monitor, Foundry, provisioned throughput, Azure AI Search integration. | Azure per-token/model pricing, PTU/hourly/reservations, global/data-zone/regional deployment options, Azure service costs. | Primary candidate for Azure-operated sensitive workflows. |
| Microsoft 365 Copilot | Microsoft | Microsoft Product Terms, Microsoft DPA, Microsoft 365 privacy/security commitments | Microsoft 365 service boundary. EU users are covered by EU Data Boundary commitments, with caveats for web search, agents/connectors, and Anthropic models. | Deep Microsoft 365 integration over Graph, Teams, SharePoint, OneDrive, Outlook, Office apps. | Microsoft 365 Copilot licensing plus Purview, security, compliance, connector, and data-cleanup costs. | Candidate for controlled internal Microsoft 365 workflows after permission and oversharing controls. |
| OpenAI infrastructure partnerships | Mixed: Microsoft/Azure, AWS, Oracle, SoftBank, CoreWeave, and others | Infrastructure announcements; not necessarily customer-facing data terms | Shows OpenAI's compute stack is multi-provider. Does not prove workload-specific processing location or routing controls. | Capacity/availability context. | Indirect cost/capacity implications only. | Evidence for Provider Stack review, not an approval basis. |

## Direct OpenAI API

### Provider Stack And Processing Location

- AI model provider: OpenAI.
- Application or product provider: OpenAI.
- AI compute provider: OpenAI-selected infrastructure. Public announcements show Microsoft remains primary cloud partner, while OpenAI can serve products across any cloud provider and has announced AWS/Stargate infrastructure partnerships.
- Cloud or infrastructure provider: not fixed from the customer's point of view for direct OpenAI.
- Contracting party: OpenAI OpCo, LLC by default; OpenAI Ireland Ltd. for customers in the EEA or Switzerland under the DPA. Executed order forms may alter specifics.
- Data processor or controller position: OpenAI DPA states OpenAI acts as Data Processor for Customer Data when providing Services under the Agreement.
- Processing locations: not fully determined without the customer's OpenAI data-residency configuration and agreement. Data residency can be configured per API project for eligible customers, endpoints, models, and regions.
- Provider routing constraints:
  - No customer-facing "Azure-only" guarantee should be assumed for direct OpenAI.
  - Data residency controls can provide regional storage, and for identified regions/endpoints regional processing, subject to limitations.
  - Non-US data residency requires approval for abuse monitoring controls and a Zero Data Retention amendment.
- Subprocessors and onward transfers: OpenAI DPA references a public subprocessor list and SCCs/adequacy mechanisms for EEA/Swiss transfers.
- Retention and training-use terms:
  - OpenAI says API data is not used to train or improve OpenAI models by default unless the customer opts in.
  - Abuse monitoring logs may contain prompts/responses and are retained up to 30 days by default.
  - Zero Data Retention and Modified Abuse Monitoring are available only for eligible and approved customers and do not apply uniformly to every endpoint/capability.
  - Application state can persist for features such as Responses with `store=true`, conversations, threads, vector stores, files, background mode, code interpreter, and other stateful tools.
- Employee AI Privacy implications: API keys, project logs, usage, audit metadata, and application telemetry can identify employee behavior; disclose in Employee AI Transparency Notice.
- Uncertainty gaps: exact regional support for desired models/endpoints, ZDR/MAM eligibility, subprocessor countries, executed DPA/order-form terms, and whether system data or metadata remains outside a selected region.

### Cost Profile

- Published OpenAI API pricing is per 1M tokens and varies by model, context length, modality, and service tier.
- As of this pass, the pricing page lists GPT-5.5, GPT-5.4, GPT-5.4 mini, GPT-5.4 nano, and GPT-5.4 pro rates and states that regional-processing endpoints for listed GPT-5.5/GPT-5.4 series models carry a 10% uplift.
- Batch and Flex can reduce token rates for eligible workloads; Priority increases rates for premium latency/availability behavior.
- Scale Tier is an enterprise option with upfront token-units, minimum 30-day purchase, 99.9% uptime SLA, and prioritized compute.
- Additional cost drivers:
  - data residency uplift and eligibility work
  - ZDR/MAM approval and compliance obligations
  - prompt caching, background mode, tools, containers, file search, web search, and storage
  - application-side logging, DLP, moderation, and security review

## ChatGPT Enterprise / Business / Edu

### Provider Stack And Processing Location

- AI model provider: OpenAI.
- Application or product provider: OpenAI / ChatGPT.
- AI compute provider: OpenAI-selected infrastructure.
- Cloud or infrastructure provider: not fixed from the customer's point of view.
- Contracting party: OpenAI contracting entity under the relevant business/enterprise agreement and DPA.
- Data processor or controller position: OpenAI DPA should be reviewed for the specific plan and agreement.
- Processing locations: controlled by ChatGPT enterprise plan, retention settings, connected apps, and OpenAI product terms; not equivalent to Microsoft 365 tenant residency.
- Provider routing constraints: not Azure-operated and not Microsoft 365-boundary processing.
- Subprocessors and onward transfers: OpenAI DPA/subprocessor review required.
- Retention and training-use terms:
  - OpenAI Enterprise privacy page states business data is not used for model training by default.
  - Enterprise plans allow retention controls, depending on plan and configuration.
  - Service Terms state Enterprise administrators may access, share, remove content, and access logging/use information.
- Employee AI Privacy implications: high. Admin visibility, compliance logs, connectors, GPTs/actions, uploaded files, conversations, and audit systems must be disclosed and governed.
- Uncertainty gaps: exact retention period, compliance log export, connector behavior, GPT/action settings, workspace admin controls, and plan-specific guarantees.

### Cost Profile

- Cost is primarily seat/subscription or enterprise-contract based, plus compliance, data-governance, connector, and admin-review effort.
- Compliance Platform / logs may require enterprise-tier access and downstream SIEM/eDiscovery storage.
- Hidden operational cost is data-permission hygiene: SharePoint/Drive/connector cleanup before broad rollout.

## Azure OpenAI / Microsoft Foundry Models Sold By Azure

### Provider Stack And Processing Location

- AI model provider: OpenAI for OpenAI model families; Microsoft hosts Models sold by Azure in Azure.
- Application or product provider: Microsoft Azure / Microsoft Foundry.
- AI compute provider: Microsoft Azure.
- Cloud or infrastructure provider: Microsoft Azure.
- Contracting party: Microsoft under Azure/Microsoft Product Terms and the Microsoft Products and Services DPA.
- Data processor or controller position: Microsoft DPA and Product Terms govern Azure OpenAI / Foundry service processing. Exact role should be reviewed under the customer agreement.
- Processing locations:
  - Standard/regional deployments process prompts and responses within the customer-specified geography, with possible movement between regions within that geography for operational reasons.
  - DataZone deployments may process prompts/responses in any geography within the Microsoft-defined data zone.
  - Global deployments may process prompts/responses in any geography where the relevant model is deployed.
  - Stored data at rest for supported service features is stored in the customer-designated geography.
- Provider routing constraints:
  - For sensitive EU workflows, prefer regional or EU DataZone deployment types where model availability supports it.
  - Avoid Global deployments for Client Confidential Data unless the board accepts global Microsoft processing.
  - Use Azure Policy, RBAC, deployment templates, and resource governance to enforce allowed models/deployment types.
- Subprocessors and onward transfers: Microsoft subprocessors and Product Terms/DPA review required. Microsoft docs say OpenAI model providers do not receive prompts/completions through Models sold by Azure.
- Retention and training-use terms:
  - Microsoft says prompts, completions, embeddings, and training data are not available to OpenAI and are not used to improve OpenAI, Microsoft, or third-party products without permission/instruction.
  - Abuse monitoring can include automated review and human review of flagged content unless modified abuse monitoring is approved.
  - Stored feature data can be deleted by the customer; preview features may have different conditions.
- Employee AI Privacy implications: Azure logs, subscription usage, Foundry projects, prompt stores, model invocation telemetry, and human-review exceptions must be disclosed.
- Uncertainty gaps: exact model availability in EU regional/DataZone deployment, modified abuse monitoring eligibility, preview feature exclusions, selected resource geography, and Product Terms for specific Microsoft Foundry features such as Bing grounding.

### Cost Profile

- Azure pricing is model, deployment type, region, and commercial-agreement dependent.
- Standard/global/data-zone usage is generally token-based; provisioned throughput uses PTUs billed hourly with possible reservation discounts.
- Additional cost drivers:
  - Azure AI Search, Blob Storage, vector stores, Foundry projects, agents, and "on your data" architecture
  - private networking and managed identity
  - Azure Monitor, Log Analytics, Sentinel/SIEM, Defender, Purview
  - regional/DataZone availability constraints that may require fallback models or higher operational overhead
  - provisioned throughput sizing and reservation commitments

## Microsoft 365 Copilot

### Provider Stack And Processing Location

- AI model provider: Microsoft-hosted model stack; Microsoft docs say Microsoft 365 Copilot uses Azure OpenAI services for processing, not OpenAI's public services. Anthropic and other models may be available in some Copilot experiences and require separate review.
- Application or product provider: Microsoft 365 Copilot.
- AI compute provider: Microsoft Azure / Microsoft 365 service infrastructure.
- Cloud or infrastructure provider: Microsoft.
- Contracting party: Microsoft under Microsoft 365 Product Terms and Microsoft DPA.
- Data processor or controller position: Microsoft Product Terms/DPA govern commercial Microsoft 365 service commitments.
- Processing locations:
  - Microsoft 365 Copilot operates within the Microsoft 365 service boundary.
  - For EU users, Microsoft docs say EU traffic stays within the EU Data Boundary.
  - Customers outside the EU may have queries processed in the US, EU, or other regions.
- Provider routing constraints:
  - Microsoft 365 Copilot is not the same as Azure OpenAI; it is a Microsoft 365 orchestration product over Graph and Microsoft 365 apps.
  - EU Data Boundary commitments apply to Microsoft 365 Copilot, but web search queries and some third-party/agent/model capabilities can be excluded.
  - Microsoft docs specifically flag Anthropic models in Microsoft 365 Copilot as out of scope for the EU Data Boundary and in-country LLM processing commitments.
- Subprocessors and onward transfers: Microsoft Product Terms, DPA, EU Data Boundary docs, and any agent/connector terms must be reviewed.
- Retention and training-use terms:
  - Microsoft says prompts, responses, and data accessed through Microsoft Graph are not used to train foundation LLMs used by Microsoft 365 Copilot.
  - Copilot accesses only organizational data the signed-in user has permission to view, but oversharing in SharePoint/Teams/OneDrive becomes a Copilot exposure risk.
  - Stored interaction data is processed and stored in alignment with Microsoft 365 contractual commitments and can be audited/compliance-managed through Microsoft 365 controls.
- Employee AI Privacy implications: very high. Prompt history, Graph access, meeting/chat/email context, audit logs, Purview, security alerts, and admin controls require an Employee AI Transparency Notice and likely Austria/Germany labor/privacy review.
- Uncertainty gaps: enabled agents, connectors, web search, third-party app data, Anthropic model availability, tenant data location, Purview retention, and local works-council requirements.

### Cost Profile

- Cost includes Microsoft 365 Copilot licenses plus prerequisite Microsoft 365 plans and security/compliance tooling.
- Governance cost may dominate early rollout:
  - SharePoint/Teams/OneDrive permission cleanup
  - Purview sensitivity labels and DLP
  - audit/eDiscovery retention
  - agent/connector review
  - employee transparency and HR/works-council review

## Azure-Only / Microsoft-Operated Routing Answer

For the board:

1. If the intended meaning is "Microsoft operates inference and OpenAI does not receive prompts/completions," use **Azure OpenAI / Microsoft Foundry Models sold by Azure** as the candidate route.
2. If the intended meaning is "the model is made by OpenAI but the service is procured and operated inside Microsoft Azure," Azure OpenAI / Foundry is the candidate route.
3. If the intended meaning is "direct OpenAI API traffic should stay on Azure," do not assume that from current public docs. OpenAI has a primary-cloud relationship with Microsoft, but OpenAI can serve products across any cloud and has announced non-Microsoft compute partnerships.
4. If the intended meaning is "data must stay in one geography or EU boundary," choose and enforce Azure regional or DataZone deployment types where model availability supports the requirement. Global deployments should remain restricted for Client Confidential Data unless explicitly approved.
5. If the intended meaning is "Microsoft 365 tenant data stays within Microsoft 365 governance," Microsoft 365 Copilot is the relevant product, but it must be governed separately from Azure OpenAI and direct OpenAI.

## Minimum Controls Before Sensitive Use

### Direct OpenAI API

- Confirm OpenAI DPA and subprocessor list.
- Confirm data residency region, supported endpoints/models, and whether regional processing applies.
- Confirm ZDR/MAM eligibility and limitations.
- Disable `store=true` and avoid stateful endpoints/tools where incompatible with retention requirements.
- Govern files, vector stores, background jobs, code interpreter, web search, MCP servers, and connectors separately.
- Build application-side DLP, logging, moderation, and incident workflow.

### Azure OpenAI / Foundry

- Confirm model family, version, deployment type, region/geography/data zone, and availability.
- Deny Global deployments for Client Confidential Data unless approved.
- Enforce allowed deployments with Azure Policy/IaC/RBAC.
- Review Microsoft Product Terms, DPA, preview terms, and modified abuse monitoring status.
- Decide whether stored completions, threads, files, vector stores, and "on your data" features are permitted.
- Configure private networking, managed identities, customer-managed keys where applicable, logging, and SIEM.

### Microsoft 365 Copilot

- Complete permission cleanup before broad rollout.
- Configure Purview labels, DLP, retention, audit, eDiscovery, and oversharing controls.
- Govern agents, connectors, web search, and non-OpenAI model options separately.
- Document employee transparency for prompts, Graph access, meeting/chat/email data, audit logs, and admin access.
- Run local Austria/Germany employee/labor review before broad employee deployment.

## Evidence

### Current Facts

- OpenAI API data is not used to train or improve OpenAI models by default unless the customer opts in. Sources: SRC-036, SRC-037.
- OpenAI API abuse monitoring logs are retained up to 30 days by default, and ZDR/MAM require approval and have endpoint/tool limitations. Sources: SRC-036.
- OpenAI DPA states OpenAI acts as Data Processor for Customer Data and includes subprocessor, SCC, security, breach, deletion/return, and audit-support terms. Sources: SRC-038, SRC-039.
- OpenAI data residency is project-based, subject to eligibility, supported regions/endpoints/models, and does not apply to system data. Sources: SRC-036.
- Azure OpenAI / Microsoft Foundry Models sold by Azure are Microsoft-operated services and do not interact with OpenAI-operated services for customer prompts/completions. Sources: SRC-042.
- Microsoft Foundry deployment type matters: regional, DataZone, and Global deployments have different processing-location implications. Sources: SRC-042.
- Microsoft 365 Copilot operates inside the Microsoft 365 service boundary, uses Azure OpenAI services rather than OpenAI public services, and does not use prompts/responses/Graph data to train foundation LLMs. Sources: SRC-044.
- Microsoft 365 Copilot is an EU Data Boundary service for EU customers, but web search, agents/connectors, and Anthropic models can create exceptions or separate review paths. Sources: SRC-043, SRC-044.
- Microsoft and OpenAI's April 2026 partnership update states Microsoft remains OpenAI's primary cloud partner, OpenAI products ship first on Azure unless Microsoft cannot support required capabilities, and OpenAI can serve products across any cloud provider. Sources: SRC-049.
- OpenAI has announced major non-Microsoft infrastructure partnerships, including AWS and Stargate/Oracle/SoftBank/CoreWeave. Sources: SRC-050, SRC-051.

### Near-Term Developments

- OpenAI's AWS partnership targets full capacity deployment before the end of 2026, which should be tracked as infrastructure context but not as a customer routing control. Sources: SRC-050.
- Microsoft 365 Copilot and Foundry model availability, including non-OpenAI model options, is changing quickly and should be rechecked before each board approval. Sources: SRC-042, SRC-044.

### Speculation

- Any claim that a direct OpenAI API request is processed only in Azure, AWS, Oracle, CoreWeave, or another provider is Speculation unless OpenAI product docs or contract terms provide a workload-specific routing control.
- Any claim that Azure OpenAI and direct OpenAI have identical feature availability, model version timing, retention behavior, or price should be treated as Speculation until checked against current product docs and pricing.
- Any claim that Microsoft 365 Copilot is safe for all Microsoft 365 data is Speculation unless tenant permissions, sensitivity labels, connectors, agents, and employee transparency controls are validated.

## Open Questions

- Which route is the preferred candidate for Phase 1: ChatGPT Enterprise, OpenAI API, Azure OpenAI, or Microsoft 365 Copilot?
- Is the board willing to approve OpenAI-operated processing for any Client Confidential Data, or only Microsoft-operated Azure processing?
- Is EU Data Boundary / EU DataZone enough, or is single-country/single-region processing required?
- Does any client contract require named subprocessors, prohibit global processing, or require prior approval for OpenAI/Microsoft/Azure?
- Which Microsoft 365 Copilot connectors, agents, web search options, and non-OpenAI model options will be disabled by default?
- Will Azure OpenAI modified abuse monitoring be requested before Client Confidential Data workflows?
- Are direct OpenAI ZDR/MAM and data residency available for the needed model/endpoint combination?
- Which cost model is acceptable for predictable workloads: pay-as-you-go, Batch/Flex/Priority, OpenAI Scale Tier, Azure provisioned throughput, or Microsoft 365 seat licensing?

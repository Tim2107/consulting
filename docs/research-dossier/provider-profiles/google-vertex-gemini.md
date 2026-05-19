# Provider Profile: Google / Vertex AI / Gemini

Date accessed: 2026-05-19

Status: first-pass provider profile. This is not a legal opinion and should be validated against executed Google Cloud or Google Workspace terms, data-processing terms, selected regions, product edition, connector configuration, and current model availability before policy approval.

## Executive Conclusion

Google is different from the Anthropic/AWS and OpenAI/Microsoft cases because Google is usually both the model provider and the infrastructure/operator for Gemini on Google Cloud. The main routing question is therefore not "which third-party cloud operates the model?" but whether the customer has selected a Google product, endpoint, edition, and feature set that actually enforces the desired **Processing Location** and **Provider Routing Constraint**.

Current primary-source conclusion:

- **Vertex AI / Generative AI on Vertex AI** is the main Google Cloud route for Google-operated Gemini models. It can support regional or multi-region processing for supported models and endpoints, but the global endpoint should not be used where in-region or EU processing is required.
- **Gemini Enterprise / Agent Platform** is the enterprise search, assistant, connector, and agent platform route. It supports US/EU data residency and ML regional processing for core features, but several features are global-only or have limitations, including Grounding with Google Search, some agents, analytics, image/video features, and some newer Gemini models.
- **Gemini for Google Workspace** is a Workspace-boundary productivity route. Google states Workspace data is not used to train or improve Gemini/Search/other systems outside Workspace without permission, and Workspace with Gemini offers EU/US processing controls, data-region controls, and client-side encryption. This is not the same as Vertex AI and should be governed as a Workspace workflow.
- **Gemini Developer API / Google AI Studio** should be treated cautiously for company use. The paid tier says data is not used to improve Google products, but the free tier says data is used to improve products. For Client Confidential Data, prefer Vertex AI or an enterprise Google Cloud/Workspace route rather than the free developer tier.

For workflows involving **Client Confidential Data**, the default board posture should be:

- Vertex AI with EU multi-region or supported EU regional endpoints: **candidate restricted option**, subject to model/location verification, ZDR/caching/grounding controls, Google Cloud DPA review, IAM/org policy enforcement, logging policy, and client-contract compatibility.
- Vertex AI global endpoint: **not suitable** where processing location matters because Google states the customer cannot control or know which region receives ML processing.
- Gemini Enterprise with EU multi-region and supported features only: **candidate restricted option**, but grounding, connectors, agents, and model/feature limitations must be explicitly configured.
- Gemini for Google Workspace: **candidate controlled internal-workflow option** for Workspace data, but not a generic approved route for arbitrary Client Confidential Data unless Workspace data-region, CSE, DLP, access-control, and employee transparency controls are in place.
- Gemini Developer API free tier: **not suitable** for Client Confidential Data.

## Option Comparison

| Option | Operating party for inference | Main contracting/data terms | Routing and residency posture | Feature posture | Cost posture | First-pass governance fit |
| --- | --- | --- | --- | --- | --- | --- |
| Vertex AI / Gemini models | Google Cloud | Google Cloud Service Specific Terms, Cloud DPA, Vertex AI docs | Regional and multi-region endpoints can provide ML-processing commitments for supported models. Global endpoint should not be used for strict processing-location requirements. | Broad model/API route; supports Gemini, embeddings, Imagen/Veo, tuning, grounding, provisioned throughput, and Model Garden/partner/open models with caveats. | Token/model pricing, batch discounts, provisioned throughput, grounding, storage, logging, networking, security controls. | Primary Google candidate for restricted sensitive workflows. |
| Gemini Enterprise / Agent Platform | Google Cloud | Google Cloud terms, Gemini Enterprise docs, connector terms | US/EU data residency and ML regional processing for core features, with feature-specific limitations and allowlisted in-country options. | Enterprise search, assistants, agents, connectors, NotebookLM Enterprise, data stores. | Subscription/licensing plus connector ingestion, data stores, security controls, and administration. | Candidate for enterprise RAG/assistant workflows after connector and feature review. |
| Gemini for Google Workspace | Google Workspace / Google | Workspace terms, Cloud DPA where applicable, Workspace privacy/security docs | Workspace-boundary product. Google says customers can control US/EU storage/processing for Gemini in Workspace and use CSE for highest sensitivity. | Gmail, Docs, Sheets, Slides, Drive, Meet, Chat, Calendar, Vids; depends on Workspace permissions and admin controls. | Workspace/Gemini licenses plus data-region, CSE, DLP, Vault, audit, and permission-cleanup work. | Candidate controlled internal-workflow option, not a generic AI API route. |
| Gemini Developer API / Google AI Studio | Google | Gemini API terms/pricing; enterprise path points to Vertex AI | Free tier uses data to improve products; paid tier says data is not used to improve products. Enterprise route is Vertex AI. | Developer-friendly API and AI Studio. | Free tier, paid token pricing, batch, context caching, grounding charges. | Not appropriate for Client Confidential Data unless using paid/enterprise controls and approved terms. |
| Partner/open models on Vertex AI | Mixed: Google platform plus model provider/open model | Google Cloud terms plus partner/open model terms | Endpoint/data residency support varies by model and location. Partner/open model terms must be checked separately. | Useful for provider comparison and self-host/open-weight scenarios. | Model-specific pricing and support. | Requires separate profile before sensitive use. |

## Vertex AI / Gemini Models

### Provider Stack And Processing Location

- AI model provider: Google for Gemini and other Google models.
- Application or product provider: Google Cloud / Vertex AI / Gemini Enterprise Agent Platform.
- AI compute provider: Google Cloud.
- Cloud or infrastructure provider: Google Cloud.
- Contracting party: Google Cloud contracting entity under the applicable Google Cloud agreement, reseller agreement, or order form.
- Data processor or controller position: Google Cloud DPA states Google is a processor and Customer is controller or processor for Customer Personal Data.
- Processing locations:
  - Data stored at rest remains in the customer-selected location.
  - ML processing occurs in the specific region or multi-region where the request is made for supported Generative AI on Vertex AI services.
  - Google warns that not every regional endpoint guarantees in-region ML processing.
  - Global endpoints cover the world and should not be used where ML-processing location matters.
- Provider routing constraints:
  - Use explicit EU multi-region or supported EU regional endpoints where sensitive workflows require EU processing.
  - Do not use `global` endpoints for Client Confidential Data unless the board accepts unknown/global ML processing.
  - Validate each selected model/version against the current data-residency and locations tables.
  - Use IAM, organization policies, approved client libraries, and infrastructure-as-code to prevent accidental global endpoint use.
- Subprocessors and onward transfers: Google Cloud DPA and subprocessor terms apply; customer must review Google subprocessors, transfer terms, and data-location commitments.
- Retention and training-use terms:
  - Google Cloud Service Specific Terms say Google will not use Customer Data to train or fine-tune AI/ML models without prior permission or instruction.
  - For Google models on Vertex AI, prompt logging for abuse monitoring may apply for customers under certain terms; customers can request an exception if they need zero data retention.
  - Grounding with Google Search stores prompts, contextual information, and generated output for 30 days and cannot be disabled for ZDR; Google recommends Web Grounding for Enterprise where ZDR is required.
  - Gemini Live session resumption stores cached data for up to 24 hours when enabled.
  - Published Gemini models cache customer data in memory by default for up to 24 hours; this is project-isolated, in-memory only, follows data residency, and can be disabled at project level.
- Employee AI Privacy implications: Google Cloud audit logs, IAM, model invocation metadata, console/Code Assist usage, and admin visibility require Employee AI Transparency Notice and likely works-council review in Austria/Germany.
- Uncertainty gaps: selected Gemini model/version, exact EU regional support, ZDR/abuse monitoring exception status, grounding feature choice, caching status, partner/open model terms, and reseller data boundary.

### Cost Profile

- Vertex AI generative AI pricing is model, modality, context length, batch/online mode, feature, and region dependent.
- Cost drivers:
  - Gemini token pricing and batch discounts.
  - Provisioned throughput or reserved capacity where needed.
  - Grounding with Google Search, Web Grounding for Enterprise, Google Maps grounding, or grounding with customer data.
  - Context caching and storage.
  - Vector search, RAG corpora, Cloud Storage, BigQuery, AI Search, and connector ingestion.
  - Cloud Logging, Cloud Monitoring, Security Command Center, Sensitive Data Protection, DLP, VPC Service Controls, CMEK, and Assured Workloads if used.
- Cost uncertainty: strict EU regional support may limit model choice or require fallback models; global endpoints may be cheaper/easier operationally but are not acceptable where ML-processing location is a hard requirement.

## Gemini Enterprise / Agent Platform

### Provider Stack And Processing Location

- AI model provider: Google for Gemini features; partner/open model or third-party agents may add additional provider-stack layers.
- Application or product provider: Google Cloud / Gemini Enterprise.
- AI compute provider: Google Cloud.
- Cloud or infrastructure provider: Google Cloud.
- Contracting party: Google Cloud.
- Data processor or controller position: Google Cloud DPA applies under the relevant agreement.
- Processing locations:
  - Gemini Enterprise supports US and EU multi-regions.
  - For Gemini Enterprise, ML processes such as training, prediction, and tuning occur in the US for US regionally available APIs and in the EU for Europe regionally available APIs, subject to feature limitations.
  - In-country regions such as Canada and India are GA with allowlist; feature constraints apply.
- Provider routing constraints:
  - For EU workflows, create data stores and apps in `eu` and use `eu-discoveryengine` / `locations/eu` APIs.
  - Review limitations before enabling features. Some features are global-only or lack DRZ/MLP in EU or in-country locations.
  - Grounding with Google Search and some agents/features can be global-only or can temporarily log customer data.
- Subprocessors and onward transfers: Google Cloud subprocessors and any connector/third-party data-source terms apply.
- Retention and training-use terms: follows Google Cloud terms, but individual features such as grounding, agents, NotebookLM Enterprise, and connectors may add storage, caching, or logging behavior.
- Employee AI Privacy implications: high. Gemini Enterprise connects enterprise data, permissions, identity data, agents, and activity logs; transparency notice and access review are required.
- Uncertainty gaps: exact edition, enabled agents, connector list, data-store regions, Workspace connector limitations, source-system terms, and whether search is federated or ingested.

### Cost Profile

- Cost includes Gemini Enterprise licenses/subscriptions, data-store and connector setup, data ingestion/sync, storage, search/RAG usage, and security controls.
- Operational cost drivers include identity mapping, permissions cleanup, connector maintenance, data quality work, DLP, audit logging, and agent governance.

## Gemini For Google Workspace

### Provider Stack And Processing Location

- AI model provider: Google.
- Application or product provider: Google Workspace.
- AI compute provider: Google infrastructure.
- Cloud or infrastructure provider: Google.
- Contracting party: Google Workspace contracting entity under Workspace agreement, DPA, and plan-specific terms.
- Data processor or controller position: Google Cloud DPA covers Google Workspace and Cloud Identity under the relevant agreement; exact posture should be checked against the customer agreement.
- Processing locations:
  - Google states Workspace data stays in Workspace and is not used to train or improve Gemini, Search, or other systems outside Workspace without permission.
  - Google says customers can control where Gemini in Workspace data is stored and processed, US or EU.
  - Client-side encryption can restrict Gemini access to sensitive Workspace data.
- Provider routing constraints:
  - Use Workspace data-region and processing-region controls where available.
  - Use CSE, DLP, labels, access controls, Vault, and audit logs before broad rollout.
  - Do not treat Workspace Gemini as an approval route for non-Workspace Client Confidential Data unless the data is legitimately governed inside Workspace and contractually permitted.
- Subprocessors and onward transfers: Google Workspace subprocessors and DPA apply.
- Retention and training-use terms:
  - Workspace help states Gemini in Workspace does not store prompts or generated outputs without permission.
  - Personal-account or experimental programs can have different terms; these must be blocked for company data.
- Employee AI Privacy implications: very high. Gemini can access Gmail, Drive, Docs, Sheets, Slides, Meet, Chat, Calendar, and Vids according to user permissions. Employee transparency and permission hygiene are mandatory.
- Uncertainty gaps: exact Workspace edition, data-region SKU, CSE coverage, admin history settings, app-specific behavior, user-permission sprawl, and whether personal/experimental Gemini features are disabled.

### Cost Profile

- Cost includes Workspace/Gemini licenses and security/governance controls.
- Operational cost drivers:
  - Drive/Shared Drive permission cleanup.
  - DLP and classification rules.
  - Client-side encryption design and key management.
  - Vault, audit, retention, eDiscovery, and employee/labor review.

## Gemini Developer API / Google AI Studio

### Provider Stack And Processing Location

- AI model provider: Google.
- Application or product provider: Google AI for Developers / Gemini API / Google AI Studio.
- AI compute provider: Google.
- Cloud or infrastructure provider: Google.
- Contracting party: Google API/Gemini API terms unless upgraded to enterprise/Vertex AI.
- Processing locations: not evaluated as a sensitive enterprise route in this pass.
- Provider routing constraints: paid tier is better than free tier for product-improvement posture, but enterprise deployments should use Vertex AI.
- Retention and training-use terms: Gemini Developer API pricing page says free-tier data is used to improve products and paid-tier data is not used to improve products.
- Governance fit: avoid for Client Confidential Data unless Legal/Security explicitly approve paid/enterprise terms and controls.

## Vertex Routing Answer

For the board:

1. If the intended meaning is "Google operates inference and data can stay in a chosen Google region or multi-region," **Vertex AI with supported regional or EU multi-region endpoints** is the candidate route.
2. If the intended meaning is "data must stay in the EU for ML processing," use supported EU regional or EU multi-region locations and verify the exact model/version/feature in current location tables.
3. If the endpoint is `global`, do not treat it as regionally constrained. Google says the customer cannot control or know which region receives ML processing for global endpoint requests.
4. If the workflow uses Gemini Enterprise agents, connectors, grounding, image/video generation, analytics, or NotebookLM Enterprise, feature-level data-residency and ML-processing limitations must be checked separately.
5. If the workflow is Workspace productivity over Gmail/Drive/Docs/Meet/Chat data, evaluate it as **Gemini for Google Workspace**, not as Vertex AI.
6. If the workflow uses Google AI Studio or the Gemini Developer API free tier, do not approve Client Confidential Data because the free tier is product-improvement data.

## Minimum Controls Before Sensitive Use

- Confirm product route: Vertex AI, Gemini Enterprise, Gemini for Workspace, or Gemini Developer API.
- Confirm model, model version, endpoint, region or multi-region, and feature set.
- Deny global endpoints for Client Confidential Data unless explicitly approved.
- Disable in-memory caching at project level if required by policy, even though Google says it follows data residency and is in-memory only.
- Request abuse-monitoring exception if zero data retention is required and available.
- Avoid Grounding with Google Search for ZDR workflows; prefer Web Grounding for Enterprise where appropriate.
- Review Google Cloud DPA, Service Specific Terms, subprocessors, and reseller/account-boundary terms.
- Enforce allowed regions and APIs through IAM, org policy, VPC Service Controls, and infrastructure-as-code.
- Configure Cloud Audit Logs, logging retention, Sensitive Data Protection/DLP, CMEK/CSE where applicable.
- For Workspace/Gemini Enterprise, clean up permissions and connectors before enabling broad access.
- Document Employee AI Transparency Notice for prompts, files, email/calendar/chat access, logs, and admin visibility.

## Evidence

### Current Facts

- Google Cloud Service Specific Terms say Google will not use Customer Data to train or fine-tune AI/ML models without prior permission or instruction. Sources: SRC-054.
- Google Cloud DPA states Google is a processor and Customer is controller or processor for Customer Personal Data; it includes customer-instruction, subprocessor, data-location, transfer, and audit provisions. Sources: SRC-055.
- Vertex AI data residency docs say data at rest remains in the customer-selected location and ML processing occurs in the specific region or multi-region where the request is made for supported services. Sources: SRC-052.
- Vertex AI global endpoints do not guarantee data residency or in-region ML processing; Google says not to use the global endpoint where ML processing requirements apply. Sources: SRC-053.
- Vertex AI for Google models has specific retention and ZDR caveats, including prompt logging for abuse monitoring, 30-day retention for Grounding with Google Search, Live API session resumption, and in-memory caching. Sources: SRC-056.
- Gemini Enterprise supports US/EU multi-region data residency and ML regional processing for core features, with feature-level limitations. Sources: SRC-059.
- Gemini for Google Workspace states Workspace data is not used to train or improve underlying generative AI and LLMs outside Workspace without permission. Sources: SRC-057, SRC-058.
- Gemini Developer API pricing says free-tier data is used to improve products, while paid-tier data is not used to improve products. Sources: SRC-061.

### Near-Term Developments

- Gemini Enterprise docs show several model and feature capabilities marked as coming soon or limited for EU/in-country locations. Treat these as tracked near-term or roadmap items only when an official date or contractual commitment exists. Sources: SRC-059.

### Speculation

- Any claim that a Vertex AI global endpoint request stays in the EU is Speculation and contradicted by current docs.
- Any claim that Gemini Enterprise feature parity exists between global and EU locations is Speculation; feature limitations must be checked.
- Any claim that consumer Gemini, Google AI Studio free tier, or personal-account Gemini has enterprise privacy posture is Speculation unless the exact account, tier, and terms are verified.

## Open Questions

- Which Google route is actually under consideration: Vertex AI API, Gemini Enterprise, Gemini for Workspace, Gemini Code Assist, or Gemini Developer API?
- Does the board require EU multi-region, a single EU country/region, or merely Google-operated processing?
- Which Gemini model/version is acceptable if the latest model is not yet available with EU DRZ/MLP?
- Is Grounding with Google Search prohibited for Client Confidential Data because of 30-day storage and ZDR limitations?
- Will the company require ZDR and project-level cache disablement for sensitive workflows?
- Which Workspace data-region, CSE, DLP, and Vault controls are already licensed and configured?
- Which Gemini Enterprise connectors and agents are allowed, especially for Jira, Confluence, GitHub, SharePoint, Google Drive, Gmail, and BigQuery?

# Provider Profile: xAI / Grok / SpaceXAI

Date accessed: 2026-05-19

Status: first-pass provider profile. This is not a legal opinion and should be validated against executed xAI, X, reseller, or enterprise terms; selected endpoint; product edition; DPA; subprocessor list; retention configuration; and current regional availability before policy approval.

## Executive Conclusion

xAI/Grok should be evaluated as both an **AI Model Provider** and a potential **AI Compute Provider**.

Current primary-source conclusion:

- **xAI API** is the primary route to evaluate for enterprise-controlled application use. xAI documentation describes no training on Customer Content without explicit permission, 30-day temporary request/response storage by default, zero data retention for enterprise customers, regional endpoints, and a DPA/subprocessor framework. This can be a candidate restricted option only after enterprise terms, DPA, ZDR, regional endpoint, logging, and transfer controls are confirmed.
- **Grok Business and Grok Enterprise** are user-facing workplace routes. xAI states that business data is not used to train models. Enterprise adds SSO/SCIM/RBAC, advanced audit logs, CMEK, dedicated data plane, enterprise search, and admin controls. These routes need the same connector, permission, audit, and employee-transparency review as Microsoft 365 Copilot and Gemini Workspace.
- **Consumer Grok / X-integrated Grok** should not be approved for Client Confidential Data. xAI consumer terms and privacy materials allow broad content use for service operation and improvement, and consumer FAQ language says user content and interactions may be used to train models unless covered by a private-chat or business/enterprise exception.
- **xAI / SpaceXAI compute-provider role** is in scope because xAI describes Colossus as a large training and inference supercomputer, and xAI/SpaceXAI publicly announced compute access for Anthropic. That evidence matters for Provider Stack analysis, but it does not prove that a given customer workload runs on Colossus or that customers can enforce Colossus-only routing.

For workflows involving **Client Confidential Data**, the default board posture should be:

- xAI API with enterprise terms, DPA, ZDR, and a configured regional endpoint: **candidate restricted option**, subject to Legal/Security review and region, transfer, subprocessor, logging, connector, and audit controls.
- xAI API default/global route without ZDR or regional controls: **Needs Decision / Restricted**, because default temporary storage, auto-routing, and non-EU subprocessor/transfer posture need review.
- Grok Business or Grok Enterprise: **candidate controlled internal-workflow option**, subject to admin controls, connector scope, permission hygiene, audit logs, employee transparency, DPA, and data-region/transfer review.
- Consumer Grok, personal X Grok, or free/personal Grok accounts: **not suitable** for Client Confidential Data.
- xAI/SpaceXAI as compute provider for other model providers: **evidence input only**, not an approval route unless the customer contract or provider documentation exposes workload-specific routing, processing location, and audit controls.

## Option Comparison

| Option | Operating party for inference | Main contracting/data terms | Routing and residency posture | Feature posture | Cost posture | First-pass governance fit |
| --- | --- | --- | --- | --- | --- | --- |
| xAI API | xAI | xAI Enterprise Terms, DPA, API docs, security FAQ | Global/auto routing by default; regional endpoints exist. Data at-rest residency requires sales contact and may cost extra. | Chat, reasoning, vision, image generation, embeddings, tools, files, batch, fine-tuning and enterprise features where available. | Token/model pricing, regional pricing, batch discounts, provisioned throughput, tool costs, ZDR/enterprise terms. | Candidate restricted API route only with enterprise terms, DPA, ZDR, regional controls, and feature restrictions. |
| Grok Business / Enterprise | xAI / Grok | Business or enterprise terms, DPA, admin/security terms | Business route has enterprise privacy commitments; Enterprise adds dedicated data plane and advanced controls. Regional/transfer posture must be verified in contract. | Workplace assistant, enterprise search, Spaces, Google Drive connector, SSO/SCIM/RBAC in Enterprise. | Business at published per-user price; Enterprise custom. Governance/security controls add operational cost. | Candidate internal-workflow option after permission, connector, logging, and employee review. |
| Consumer Grok / X-integrated Grok | xAI / X ecosystem | Consumer Terms, Privacy Policy, Consumer FAQ, X terms where applicable | No enterprise processing-location or retention approval baseline identified in this pass. | Consumer chatbot and X-integrated features. | Consumer subscription or bundled access. | Not suitable for Client Confidential Data. |
| xAI / SpaceXAI compute-provider role | xAI / SpaceXAI | Partnership and infrastructure announcements | Public announcements show compute capacity, but not customer-selectable routing for a specific enterprise workload. | Training, fine-tuning, inference, and high-performance AI workloads according to xAI announcement language. | Strategic capacity economics; not a customer-selectable cost model unless exposed in product terms. | Provider Stack evidence only, not an approval route by itself. |

## xAI API

### Provider Stack And Processing Location

- AI model provider: xAI.
- Application or product provider: xAI API / developer platform.
- AI compute provider: xAI and disclosed subprocessors or infrastructure providers, depending on route and enterprise agreement.
- Cloud or infrastructure provider: not fully workload-specific in public docs. xAI subprocessor list includes cloud and infrastructure providers that may process customer personal data.
- Contracting party: xAI under Enterprise Terms, DPA, API documentation, or customer order form.
- Data processor or controller position: xAI DPA states the customer is controller or processor and xAI is processor for Customer Personal Data.
- Processing locations:
  - xAI API has a default endpoint that auto-routes across xAI clusters.
  - Regional endpoints are available for API requests, including US and EU options.
  - xAI states that if a regional endpoint cannot process a request, it fails rather than falling back to another region.
  - Data at-rest residency for customer data requires contacting xAI sales and may involve additional cost.
- Provider routing constraints:
  - Use a regional endpoint for workflows with location constraints.
  - Confirm data-at-rest region, logs, backup, support access, and subprocessor transfer terms in the enterprise agreement.
  - Do not assume a regional endpoint alone creates EU-only processing for all customer data, logs, support, or subprocessors.
- Subprocessors and onward transfers:
  - xAI DPA references subprocessors and international transfer mechanisms.
  - xAI subprocessor list includes multiple infrastructure, security, analytics, billing, support, and operations providers.
  - The list is US-heavy and includes non-EEA locations; transfer assessment is required for EU personal data.
- Retention and training-use terms:
  - xAI security FAQ states customer data is not used to train xAI models unless the customer explicitly gives permission.
  - Default API behavior temporarily stores request and response data for up to 30 days for abuse monitoring and auditing.
  - Zero data retention is available for enterprise customers and can be verified through an API response header.
  - Enterprise Terms describe deletion of User Content within 30 days after receipt unless an exception applies; zero data retention means User Content is transmitted only transiently to generate Output and is not stored.
- Employee AI Privacy implications: xAI API use can expose prompts, files, tool calls, audit metadata, developer identity, and application logs. Employee AI Transparency Notice and logging governance are required.
- Uncertainty gaps: exact contracted DPA/order form, ZDR approval and coverage, regional endpoint and data-at-rest terms, support access, fine-tuning data handling, tool-specific retention, and whether dedicated capacity changes subprocessor or processing-location posture.

### Cost Profile

- Base usage price: xAI publishes model-specific token pricing for API models, including Grok text, reasoning, vision, image, embedding, and specialized models.
- Data residency or routing premium: xAI says regional endpoint price differs from default endpoint pricing and that data at-rest residency may involve additional cost.
- Commitment, reserved capacity, or private-offer terms: provisioned throughput is available with 30-day billing units and model-specific hourly rates.
- Logging, monitoring, and audit costs: ZDR, enterprise logging, audit integrations, and private networking may require enterprise terms or operational controls.
- Security and compliance control costs: DPA review, subprocessor review, transfer assessment, IAM, secrets management, DLP, and application logging controls.
- Integration and migration costs: API adaptation, model evaluation, prompt/tool compatibility, regional endpoint enforcement, and fallback planning.
- Operational support costs: abuse-monitoring exception/ZDR management, region availability monitoring, rate limits, key management, and incident response.
- Cost uncertainties: model availability and pricing change quickly; enterprise terms, regional pricing, ZDR, and provisioned throughput may alter the baseline.

## Grok Business / Enterprise

### Provider Stack And Processing Location

- AI model provider: xAI.
- Application or product provider: xAI / Grok Business or Grok Enterprise.
- AI compute provider: xAI and disclosed subprocessors or infrastructure providers under business or enterprise terms.
- Cloud or infrastructure provider: not fully workload-specific in public materials.
- Contracting party: xAI under Business or Enterprise terms/order form.
- Data processor or controller position: xAI DPA should be confirmed for the relevant business or enterprise offering.
- Processing locations: not fully resolved from public marketing materials. Enterprise dedicated data plane, data-region, and transfer terms must be contractually confirmed.
- Provider routing constraints:
  - Require enterprise terms and DPA before allowing Client Confidential Data.
  - Require admin controls for SSO/SCIM/RBAC, audit logs, retention, connector approvals, data-region or transfer posture, and tenant separation.
  - Treat enterprise search, Spaces, and connectors as separate data-flow surfaces.
- Subprocessors and onward transfers: xAI DPA and subprocessor list apply where the enterprise offering is covered; connected data-source providers also matter.
- Retention and training-use terms:
  - xAI Business page states company data is never used to train models.
  - Google Drive connector documentation states Google Drive content is not used for training and access follows Drive permissions.
  - Retention, export, deletion, and audit behavior must be validated for each business/enterprise plan.
- Employee AI Privacy implications: high. Grok Business/Enterprise can combine chat, uploaded files, enterprise search, Spaces, and connected source systems. Transparency notices and works-council/labor review may be required in Austria/Germany.
- Uncertainty gaps: exact enterprise contract, data-region commitments, admin control availability by SKU, connector list, dedicated data plane scope, audit log contents, and whether user or admin settings can permit training or analytics use.

### Cost Profile

- Base usage price: xAI publishes Grok Business at 30 USD per user per month and lists Enterprise as custom pricing.
- Security and compliance control costs: Enterprise controls such as SSO, SCIM, RBAC, advanced audit logs, CMEK, dedicated data plane, and compliance support may require custom pricing and security implementation.
- Integration and migration costs: identity provisioning, permission cleanup, connector setup, enterprise search indexing, data classification, DLP, and admin training.
- Cost uncertainties: Enterprise pricing, storage, connector, support, dedicated data plane, and data-region costs are not fully public.

## Consumer Grok / X-Integrated Grok

### Provider Stack And Processing Location

- AI model provider: xAI.
- Application or product provider: xAI, Grok, and potentially X depending on integration path.
- AI compute provider: xAI and infrastructure providers under consumer service terms.
- Contracting party: xAI consumer terms, X terms where integrated, and consumer subscription terms where applicable.
- Data processor or controller position: not an enterprise processor baseline for company Client Confidential Data.
- Processing locations: no enterprise processing-location commitment identified in this pass.
- Provider routing constraints: none suitable for regulated Client Confidential Data identified in public consumer materials.
- Retention and training-use terms:
  - Consumer terms grant xAI broad rights to use user content for service operation, improvement, and related purposes.
  - Consumer FAQ states xAI may use prompts, searches, other submitted materials, and Grok responses to train models, with exceptions such as private chats and business/enterprise customer contexts.
  - xAI Privacy Policy says it does not apply to xAI business offerings or third-party platforms such as X where separate terms may apply.
- Governance fit: prohibit consumer or personal-account Grok for Client Confidential Data, employee personal data requiring protection, client documents, source code, secrets, financial-sector client material, and production incident data.

## xAI / SpaceXAI Compute Provider Role

### Provider Stack And Processing Location

- AI model provider: may be xAI or another model provider using xAI/SpaceXAI compute.
- Application or product provider: depends on the customer-facing service.
- AI compute provider: xAI/SpaceXAI where disclosed by partnership or contract.
- Cloud or infrastructure provider: Colossus and related xAI/SpaceXAI infrastructure where applicable.
- Contracting party: depends on the model/product provider and compute arrangement.
- Processing locations:
  - xAI describes Colossus as located in Memphis, Tennessee.
  - xAI/SpaceXAI announced a partnership giving Anthropic access to Colossus 1.
- Provider routing constraints:
  - Public compute announcements are not enough to establish where a specific customer API or chat request is processed.
  - Treat Colossus as a Provider Stack risk/availability/capacity input unless contract terms expose customer-selectable routing and audit rights.
- Governance fit: include in provider-stack questionnaires, but do not approve or reject a customer workload solely because an upstream provider has announced access to Colossus.

## xAI Routing Answer

For the board:

1. If the intended meaning is "xAI enterprise API with no training and no persistent request storage," require xAI API enterprise terms plus ZDR confirmation.
2. If the intended meaning is "EU or regional processing," require a regional endpoint, data-at-rest residency agreement, transfer/subprocessor review, and technical enforcement that blocks default endpoint use.
3. If the workflow is workplace productivity or enterprise search, evaluate it as Grok Business/Enterprise and review connectors, permissions, audit logs, retention, and employee transparency.
4. If the workflow uses consumer Grok or personal X/Grok accounts, do not approve Client Confidential Data.
5. If the question is whether Colossus is part of the compute stack, treat it as a provider-stack inquiry, not as proof of where a specific customer workload runs.

## Minimum Controls Before Sensitive Use

- Confirm product route: xAI API, Grok Business, Grok Enterprise, consumer Grok, X-integrated Grok, or upstream compute relationship.
- Confirm enterprise terms, DPA, subprocessor list, transfer mechanism, support access, deletion, audit, and breach-notice obligations.
- Require ZDR for Client Confidential Data unless Legal/Security explicitly accept 30-day default temporary storage.
- Require regional endpoint and data-at-rest residency terms where Processing Location matters.
- Technically deny default endpoint use for workflows that require regional routing.
- Review tool-specific behavior for web search, X search, code execution, file uploads, collections, image generation, fine-tuning, and connectors.
- Disable consumer/personal Grok for company and client data through policy and technical controls where possible.
- For Grok Business/Enterprise, configure SSO, SCIM, RBAC, audit logs, DLP, connector allowlists, and permission cleanup before rollout.
- Document Employee AI Transparency Notice covering prompts, files, connector access, logs, audit metadata, and admin visibility.

## Evidence

### Current Facts

- xAI Enterprise Terms state that Customer owns Input and xAI assigns Output rights to Customer, and that xAI will not train foundation AI systems on User Content except as permitted by the agreement. Sources: SRC-062.
- xAI API security FAQ states customer data is not used to train models without explicit permission; default API behavior temporarily stores requests and responses for up to 30 days; enterprise ZDR prevents persistent request/response storage. Sources: SRC-066.
- xAI DPA states Customer is controller or processor and xAI is processor for Customer Personal Data; the DPA includes subprocessor, transfer, deletion, audit, and security provisions. Sources: SRC-064, SRC-065.
- xAI regional endpoint docs state that default endpoints auto-route across clusters, while regional endpoints fail if the selected region cannot process the request; data at-rest residency requires sales contact and may cost extra. Sources: SRC-067.
- xAI Business page states that company data is never used to train models, while Enterprise adds SSO, SCIM, RBAC, advanced audit logs, CMEK, dedicated data plane, enterprise search, and compliance support. Sources: SRC-069.
- xAI Google Drive connector documentation states that Drive content is not used to train models and that access follows Google Drive permissions. Sources: SRC-075.
- xAI consumer terms, privacy materials, and consumer FAQ do not provide a suitable enterprise baseline for Client Confidential Data; consumer FAQ says user content and interactions may be used to train models, with exceptions. Sources: SRC-070, SRC-071, SRC-072.
- xAI describes Colossus as a Memphis supercomputer supporting Grok, and xAI/SpaceXAI announced Colossus compute access for Anthropic training, fine-tuning, inference, and high-performance workloads. Sources: SRC-035, SRC-073, SRC-077.

### Near-Term Developments

- xAI regional endpoint, model, pricing, and enterprise-control docs are evolving quickly. Treat model availability, regional coverage, and enterprise features as current-date facts only. Sources: SRC-067, SRC-068, SRC-069, SRC-076.

### Speculation

- Any claim that xAI API requests are EU-only by default is Speculation and contradicted by the regional endpoint documentation.
- Any claim that ZDR is active for a customer by default is Speculation unless the account is enterprise-enabled and response headers confirm ZDR behavior.
- Any claim that Anthropic or another model provider routes a specific customer workload through Colossus is Speculation unless the customer-facing provider discloses workload-specific routing or the contract requires it.
- Any claim that Grok Business/Enterprise connectors preserve original source-system permissions forever is Speculation unless sync configuration, identity mapping, and connector behavior are tested.

## Open Questions

- Is the company considering xAI API, Grok Business, Grok Enterprise, consumer Grok, or xAI as an upstream compute provider?
- Is xAI willing to execute the required DPA, SCCs, ZDR, regional endpoint, and data-at-rest residency terms for the company or client?
- Which xAI region is acceptable for EU/EEA client work, and what logs/support/subprocessor data remain outside that region?
- Does ZDR cover every planned endpoint, model, file, tool, batch, fine-tuning, image, search, connector, and audit path?
- Are web search, X search, Google Drive connector, Spaces, enterprise search, and file uploads allowed for Client Confidential Data?
- Which enterprise audit fields are visible to admins, exported to SIEM, or retained by xAI?
- Can xAI provide workload-specific information about compute facilities or Colossus use if a client asks?

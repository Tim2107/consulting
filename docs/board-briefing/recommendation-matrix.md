# Recommendation Matrix

This matrix maps AI use case archetypes and deployment options to a governance status. Each cell should include a short rationale and evidence references.

## Governance Status Values

- Allowed
- Restricted
- Prohibited
- Needs Decision

## Deployment Options

- No Client Confidential Data
- Client Confidential Data inside Company-Controlled Environment
- Approved third-party provider with enterprise terms
- Provider with routing or data-residency constraint
- Managed Private Deployment
- Company-Operated Self-Hosted Option
- Training or fine-tuning on company or client material

## Matrix Template

| AI Use Case Archetype | No Client Confidential Data | Client Confidential Data inside Company-Controlled Environment | Approved Third-Party Provider | Provider Routing Constraint | Managed Private Deployment | Company-Operated Self-Hosted Option | Training or Fine-Tuning |
| --- | --- | --- | --- | --- | --- | --- | --- |
| General productivity | Needs Decision | Needs Decision | Needs Decision | Needs Decision | Needs Decision | Needs Decision | Needs Decision |
| Software delivery | Needs Decision | Needs Decision | Needs Decision | Needs Decision | Needs Decision | Needs Decision | Needs Decision |
| Delivery Pipeline Systems | Needs Decision | Needs Decision | Needs Decision | Needs Decision | Needs Decision | Needs Decision | Needs Decision |
| Knowledge retrieval | Needs Decision | Needs Decision | Needs Decision | Needs Decision | Needs Decision | Needs Decision | Needs Decision |
| Client project analysis | Needs Decision | Needs Decision | Needs Decision | Needs Decision | Needs Decision | Needs Decision | Needs Decision |
| Customer or service operations | Needs Decision | Needs Decision | Needs Decision | Needs Decision | Needs Decision | Needs Decision | Needs Decision |

## Technical Gate Note

Automated deployment, release, and infrastructure actions should not be treated as categorically prohibited. They may be allowed when approved as Technically Gated Actions with enforceable controls.

## Provider Routing Note

Anthropic/AWS first-pass research indicates that provider routing constraints must identify both the commercial access path and the operating party:

- Claude in Amazon Bedrock is the candidate AWS-operated route for sensitive workflows that require AWS to operate inference.
- Claude Platform on AWS is not an AWS-only processing route, even though it uses AWS IAM, billing, and CloudTrail integration.
- Global Bedrock inference profiles should remain Needs Decision or Restricted for Client Confidential Data unless the board accepts worldwide AWS commercial-region processing.

Evidence references: CLAIM-016, CLAIM-017, CLAIM-018.

## OpenAI / Microsoft Routing Note

OpenAI/Microsoft first-pass research indicates that the same provider-stack distinction applies:

- Direct OpenAI API and ChatGPT Enterprise are OpenAI-operated and should not be assumed to be Azure-only.
- Azure OpenAI / Microsoft Foundry Models sold by Azure are the candidate Microsoft-operated route for OpenAI models.
- Microsoft 365 Copilot is a separate Microsoft 365-boundary workflow and must be governed through tenant permissions, Purview, connectors, agents, web search, and model-option controls.

Evidence references: CLAIM-021 through CLAIM-030.

## Google / Vertex / Gemini Routing Note

Google first-pass research closes the third leg of the Bedrock/Azure/Vertex routing question:

- Vertex AI with supported regional or EU multi-region endpoints is the candidate Google-operated route for sensitive workflows.
- Vertex AI global endpoints should not be approved for Client Confidential Data where ML-processing location matters.
- Gemini Enterprise and Gemini for Google Workspace need feature-level governance because connectors, grounding, agents, data regions, CSE, and DLP controls materially change the data-flow posture.
- Gemini Developer API / Google AI Studio free tier should not be used with Client Confidential Data.

Evidence references: CLAIM-031 through CLAIM-038.

## xAI / Grok / SpaceXAI Routing Note

xAI/Grok first-pass research indicates that xAI should be evaluated both as a model/product provider and as a possible AI compute-provider layer:

- xAI API with enterprise terms, DPA, ZDR, and regional endpoint/data-at-rest controls is a candidate restricted route for sensitive workflows.
- Default xAI API routing, default 30-day temporary storage, and consumer/personal Grok are not sufficient for Client Confidential Data approval.
- Grok Business/Enterprise can be a candidate internal-workflow route, but connectors, enterprise search, permissions, audit logs, employee transparency, and data-region/transfer terms must be reviewed.
- Colossus and xAI/SpaceXAI compute partnerships matter for Provider Stack analysis but do not by themselves establish workload-specific routing for a customer request.

Evidence references: CLAIM-039 through CLAIM-047.

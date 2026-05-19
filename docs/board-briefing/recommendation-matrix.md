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

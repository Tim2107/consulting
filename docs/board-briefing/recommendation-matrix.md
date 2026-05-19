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

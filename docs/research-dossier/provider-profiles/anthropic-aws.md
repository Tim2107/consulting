# Provider Profile: Anthropic / AWS

Date accessed: 2026-05-19

Status: first-pass provider profile. This is not a legal opinion and should be validated against executed contracts, DPAs, private offers, service terms, and current console configuration before policy approval.

## Executive Conclusion

The "AWS-only" question should be framed as a **Provider Routing Constraint**, not as a generic Anthropic feature.

Current primary-source conclusion:

- **Claude in Amazon Bedrock** is the cleaner current path when the governance requirement is AWS-operated inference and no prompt/completion disclosure to Anthropic. Anthropic describes this route as AWS-managed infrastructure with no Anthropic operator access; AWS says model providers do not have access to Bedrock deployment accounts, logs, prompts, or completions.
- **Claude Platform on AWS** is not equivalent to AWS-only processing. It uses AWS entry points, IAM, CloudTrail visibility, AWS Marketplace billing, and optional PrivateLink, but Anthropic operates the stack and processes inference inputs/outputs. Official AWS and Anthropic pages both say data is processed by Anthropic outside the AWS boundary.
- **Direct Anthropic / Claude API / Claude for Work** remains Anthropic-operated. Anthropic's commercial terms and DPA are relevant, including processor terms, SCCs, subprocessors, confidentiality, no model training on Customer Content under the commercial terms, and available data-retention controls.
- **Compute partnership announcements** show Anthropic uses multiple compute providers, including AWS, Google/Broadcom, Microsoft/NVIDIA, Fluidstack, and SpaceX/Colossus. These announcements support the need to review the compute layer, but they do not by themselves prove where a particular customer request, API workload, or Client Confidential Data is processed.

For workflows involving **Client Confidential Data**, the default board posture should be:

- Bedrock in-region or geography-bound routing: **candidate restricted option**, subject to client-contract compatibility, DPA/transfer review, IAM/SCP enforcement, logging policy, and cost confirmation.
- Claude Platform on AWS: **not suitable for AWS-only processing**; may remain a candidate for less restricted workflows that need Anthropic-native features and accept Anthropic processing outside AWS.
- Direct Anthropic API / Claude for Work: **candidate for approved third-party-provider workflows** only after Anthropic DPA, subprocessors, retention, processing-location, employee transparency, and client-contract checks are satisfied.

## Option Comparison

| Option | Operating party for inference | Main contracting/data terms | Routing and residency posture | Feature posture | Cost posture | First-pass governance fit |
| --- | --- | --- | --- | --- | --- | --- |
| Direct Anthropic API / Claude for Work | Anthropic | Anthropic Commercial Terms and DPA | Anthropic-operated; no AWS-only posture. US-only inference is listed for direct API pricing at 1.1x input/output token pricing. Other routing controls must be verified by contract/product docs. | Native Claude features, fastest access to Anthropic platform features. | Direct Claude API prices; batch processing discount; enterprise/private terms possible. | Restricted third-party provider candidate, not AWS-only. |
| Claude in Amazon Bedrock | AWS | Amazon Bedrock data handling and AWS account/service terms; model access/EULA terms also apply. | AWS-operated. Supports in-region, geographic cross-region, and global cross-region routing. Global routing may process in any commercial AWS Region; geo routing stays within a defined geography; in-region stays in a single AWS Region. | More limited than Anthropic-native platform where features require Anthropic-operated infrastructure. | AWS Bedrock model pricing, regional/source-region pricing, quota and throughput model; Zero Data Retention available by AWS support request. | Strongest current candidate for AWS-only or AWS-operated sensitive workflows. |
| Claude Platform on AWS | Anthropic, with AWS IAM/billing/CloudTrail integration | Anthropic Commercial Terms, DPA, usage policy, AWS Marketplace/AWS terms for access/billing/identity metadata | Not AWS-only. Official docs say data may not reside in AWS and may route to Anthropic's primary cloud. `inference_geo` can pin geography, but not make AWS the sole processor. | Full Anthropic platform experience, beta/native features, Agent Skills, code execution, and same-day-ish feature availability. | Same as direct Claude API according to AWS page; private offers may apply. | Candidate where AWS procurement and audit trail are desired, but not for strict AWS-only processing. |
| Anthropic compute-provider variants | Mixed: AWS, Google/Broadcom, Microsoft/NVIDIA, SpaceX/Colossus, Fluidstack, and possibly others | Varies by provider and Anthropic contracts; customer-facing terms may not disclose workload routing. | Announcements show diversified training/inference capacity. They do not disclose enough to map a specific customer workload to a compute site. | May improve capacity/limits/resilience. | Indirectly affects availability and provider economics; not a customer-selectable cost option unless surfaced in product/contract terms. | Evidence of why compute layer must be reviewed; not an approval basis by itself. |

## Direct Anthropic / Claude API / Claude For Work

### Provider Stack And Processing Location

- AI model provider: Anthropic.
- Application or product provider: Anthropic.
- AI compute provider: Anthropic-selected infrastructure; public announcements show diversified compute relationships, but customer-facing routing for a given request must be verified from product docs or contract.
- Cloud or infrastructure provider: not fixed from the customer's point of view for the first-party service.
- Contracting party: Anthropic Ireland, Limited for customers in the EEA, Switzerland, or UK under the Commercial Terms; Anthropic, PBC elsewhere.
- Data processor or controller position: Anthropic DPA states Customer is controller and Anthropic is processor for Customer Personal Data.
- Processing locations: not fully determined in this pass; must be verified through the DPA, subprocessor list, trust center, and any enterprise/order-form terms.
- Provider routing constraints: no AWS-only routing. Direct API pricing currently lists US-only inference at 1.1x input/output token pricing.
- Subprocessors and onward transfers: Anthropic DPA references a public subprocessor list.
- Retention and training-use terms: Commercial Terms state Anthropic may not train models on Customer Content from Services. DPA includes deletion/return and SCC provisions. Pricing page lists custom data retention controls for enterprise plans and "None by default" for model training in Team/Enterprise comparison.
- Employee AI Privacy implications: Claude for Work/admin features can log usage, audit, and analytics; Employee AI Transparency Notice should disclose what is logged and how it is used.
- Uncertainty gaps: exact processing locations, available EU-only/geography controls for first-party Anthropic, ZDR availability and scope, subprocessor countries, and private-offer terms.

### Cost Profile

- Published API pricing examples as of 2026-05-19:
  - Opus 4.7: $5 / MTok input and $25 / MTok output.
  - Sonnet 4.6: $3 / MTok input and $15 / MTok output.
  - Haiku 4.5: $1 / MTok input and $5 / MTok output.
- Prompt caching and batch processing can materially change unit economics.
- US-only inference is listed at 1.1x input/output pricing.
- Enterprise cost also includes SSO/SCIM, audit logs, compliance API, retention controls, employee notice, data classification, and admin ownership.

## Claude In Amazon Bedrock

### Provider Stack And Processing Location

- AI model provider: Anthropic.
- Application or product provider: AWS/Amazon Bedrock.
- AI compute provider: AWS-managed Bedrock infrastructure for inference.
- Cloud or infrastructure provider: AWS.
- Contracting party: AWS for Bedrock usage; Anthropic model terms/EULA may also be part of access enablement.
- Data processor or controller position: must be reviewed under AWS customer agreement, AWS DPA/service terms, and Bedrock terms for the selected account and region.
- Processing locations:
  - In-Region: request processed within the specified AWS Region.
  - Geographic cross-region: request may move within a defined geography such as EU, US, APAC, Japan, or Australia.
  - Global cross-region: request may be processed in commercial AWS Regions worldwide.
- Provider routing constraints:
  - Use in-region model IDs where available for strict single-region processing.
  - Use geography-prefixed inference profiles such as `eu.*` only where geography-level routing is acceptable.
  - Disable or deny `global.*` inference profiles where data residency or client-contract constraints prohibit global processing.
  - Use IAM and Service Control Policies to enforce allowed models, profiles, and destination Regions.
- Subprocessors and onward transfers: AWS Bedrock posture should be reviewed under AWS subprocessors and AWS DPA; Anthropic is not supposed to receive prompts/completions under Bedrock data-protection docs.
- Retention and training-use terms: AWS Bedrock data protection governs data handling. Anthropic docs for Claude in Bedrock say Zero Data Retention is available by contacting AWS support.
- Employee AI Privacy implications: AWS IAM, CloudTrail, CloudWatch, cost allocation, and invocation logs may create employee telemetry; disclose in Employee AI Transparency Notice.
- Uncertainty gaps: precise AWS DPA/service terms for a given contract, whether model invocation logging is enabled, selected inference profile destinations, ZDR scope, and customer-specific private terms.

### Cost Profile

- Bedrock pricing is model/provider/region/service-tier dependent and must be quoted for the selected Claude model and endpoint mode.
- AWS supports on-demand, batch, and provisioned/reserved-style throughput models depending on model and feature availability.
- AWS regional availability docs state in-region, geo, and global options are priced at source-region rates with no surcharge for cross-region routing, while Anthropic's Bedrock page states regional endpoints carry a 10% premium over global endpoints. Treat this as a pricing-source discrepancy to verify during procurement.
- Additional cost drivers:
  - IAM/SCP policy work for routing controls.
  - CloudTrail/CloudWatch/model invocation logging and SIEM ingestion.
  - PrivateLink/VPC endpoints if used.
  - Guardrails, Knowledge Bases, Agents, prompt management, evaluation, and batch jobs.
  - ZDR enablement/support process and any private offer terms.

## Claude Platform On AWS

### Provider Stack And Processing Location

- AI model provider: Anthropic.
- Application or product provider: Anthropic platform, accessed via AWS.
- AI compute provider: Anthropic-selected infrastructure.
- Cloud or infrastructure provider: Anthropic-managed infrastructure; AWS provides authentication, IAM integration, billing, CloudTrail, Marketplace integration, and optional PrivateLink.
- Contracting party: Anthropic terms for service use; AWS terms for Marketplace/access/billing metadata.
- Data processor or controller position: Anthropic docs identify Anthropic as the data processor for inference inputs and outputs; AWS processes billing and identity metadata under the marketplace model.
- Processing locations: official Anthropic docs say data may not reside in AWS, inference may route to Anthropic's primary cloud, and subservices may move under the hood without notice. AWS FAQ says data and associated metadata are processed by Anthropic outside AWS in a location of Anthropic's choosing.
- Provider routing constraints: `inference_geo` can pin inference to a geography, but this is not an AWS-only or AWS-operated constraint.
- Subprocessors and onward transfers: Anthropic DPA/subprocessors apply; AWS also processes identity/billing metadata.
- Retention and training-use terms: same retention policy as first-party Claude API; ZDR available on request through Anthropic account representative.
- Employee AI Privacy implications: AWS CloudTrail visibility plus Anthropic platform logs/admin controls must be disclosed and configured.
- Uncertainty gaps: geography options supported by `inference_geo`, exact data locations, subservice routing, metadata scope sent through AWS, and whether private offer terms alter retention/security posture.

### Cost Profile

- AWS says Claude Platform on AWS pricing is the same as accessing directly through the Claude API.
- Private offers may apply but discounts are not retroactive to usage before the private offer is accepted.
- Cost should include Anthropic feature usage such as Managed Agents, web search, code execution, batch processing, prompt caching, and service tier selection where applicable.
- Operational cost is lower than a separate procurement path if AWS Marketplace, IAM, CloudTrail, and consolidated billing reduce governance overhead.

## Compute-Provider Variants And Infrastructure Announcements

Anthropic's 2026 compute announcements materially affect the Provider Stack analysis:

- Anthropic/Amazon announced up to 5 GW of AWS capacity, including Trainium2/Trainium3 capacity and expansion of international inference in Asia and Europe.
- Anthropic states it trains and runs Claude on a range of AI hardware, including AWS Trainium, Google TPUs, and NVIDIA GPUs.
- Anthropic and SpaceX/xAI announced a May 2026 compute arrangement for Colossus 1. Anthropic says the capacity improves Claude Pro/Max and API capacity; xAI says Colossus supports training, fine-tuning, inference, and high-performance AI workloads.

Governance implication: these announcements are **Current Fact** as infrastructure relationships, but they are not sufficient to approve Client Confidential Data processing. The provider profile must still identify the customer-facing service, contract, processor chain, routing constraints, and whether the customer can enforce or audit where a particular workload runs.

## AWS-Only Routing Answer

For the board:

1. If the intended meaning is "only AWS operates inference and Anthropic cannot access prompts/completions," use **Claude in Amazon Bedrock** as the candidate option.
2. If the intended meaning is "we buy through AWS and use AWS IAM/billing/CloudTrail," **Claude Platform on AWS** may satisfy procurement/audit-trail preferences but not AWS-only data processing.
3. If the intended meaning is "data must stay in one AWS Region," Bedrock must be configured for in-region routing where the selected model supports it; geographic or global inference profiles are not equivalent.
4. If the intended meaning is "data must stay within the EU," Bedrock geographic EU inference may be a candidate where available, but prompts/outputs can move within the EU geography. Legal review must still check whether this satisfies client-contract and GDPR transfer requirements.
5. Global inference profiles should be disallowed for Client Confidential Data unless the board explicitly accepts worldwide AWS commercial-region processing.

## Minimum Controls Before Sensitive Use

- Confirm selected Claude model and Bedrock endpoint mode: in-region, geo, or global.
- Enforce allowed models and inference profiles through IAM and SCPs.
- Disable or deny global inference profiles for sensitive workflows.
- Decide whether model invocation logging is enabled and where logs are stored.
- Enable CloudTrail and CloudWatch with retention aligned to incident response and employee transparency.
- Verify AWS DPA, AWS service terms, Bedrock terms, Anthropic model access terms, and any private offer terms.
- Check AWS and Anthropic subprocessors where applicable.
- Confirm whether ZDR is needed and available for the chosen route.
- Run Client Contract Compatibility Check without ingesting contracts into AI.
- Update Approved AI Tool Registry with exact allowed data classes and routing constraints.
- Document Employee AI Transparency Notice for prompts, usage logs, identity data, billing metadata, and audit logs.

## Evidence

### Current Facts

- Anthropic commercial terms define Customer Content and state Anthropic may not train models on Customer Content from Services. Sources: SRC-021.
- Anthropic DPA states Customer is controller and Anthropic is processor for Customer Personal Data, includes subprocessor authorization, SCCs, security controls, deletion/return terms, and audit support. Sources: SRC-022.
- Claude in Amazon Bedrock runs on AWS-managed infrastructure and data handling is governed by Amazon Bedrock. Anthropic personnel have no access to Bedrock inference infrastructure according to Anthropic docs. Sources: SRC-023.
- AWS Bedrock data-protection docs say model providers do not have access to Bedrock deployment accounts, logs, prompts, or completions. Sources: SRC-026.
- Claude Platform on AWS is Anthropic-operated, with AWS providing IAM/access/billing/CloudTrail integration. Sources: SRC-024, SRC-025.
- Claude Platform on AWS is not AWS-only processing; official docs say customer data is processed by Anthropic outside AWS. Sources: SRC-024, SRC-025.
- Bedrock supports in-region, geography-bound, and global routing options with different data-residency implications. Sources: SRC-027, SRC-028, SRC-029.
- Anthropic has announced diversified compute relationships, including AWS/Amazon, Google/Broadcom, Microsoft/NVIDIA, Fluidstack, and SpaceX/Colossus. Sources: SRC-032, SRC-033, SRC-034, SRC-035.

### Near-Term Developments

- AWS/Anthropic capacity expansion includes nearly 1 GW of new capacity by the end of 2026 and international inference expansion in Asia and Europe. This is beyond the six-month horizon in part and should be tracked as near-term only where the official milestone falls within six months. Sources: SRC-032, SRC-034.

### Speculation

- Any claim that a specific direct Anthropic customer workload will or will not route to SpaceX/Colossus, Google TPUs, Azure, Fluidstack, or AWS Trainium is Speculation unless supported by product documentation, contract terms, or provider-specific routing controls.
- Any claim that Claude Platform on AWS can satisfy an AWS-only processor requirement is contradicted by current official docs and should not be used in policy.

## Open Questions

- What exact Claude models are candidates for Phase 1 workflows, and do they support in-region/EU geo routing on Bedrock?
- Does the company require single-region EU processing or is EU geography-bound routing sufficient?
- Does any client contract prohibit global commercial-region routing even if AWS remains the processor?
- Which AWS account boundary, SCPs, and IAM roles would enforce the routing constraint?
- Will model invocation logging be disabled, minimized, or retained for audit/security?
- Is Zero Data Retention required for any Client Confidential Data workflow?
- What does the executed AWS DPA/private offer say about subprocessors, transfers, audit, and deletion?
- Does the board accept Anthropic processing outside AWS for non-Client Confidential Data workflows that need native Claude Platform features?

# Research Session Continuity

Date captured: 2026-05-19

Source export: `/Users/nina/Desktop/Company-AI-integration-research.md`

Original session source recorded in export: `/Users/nina/.codex/sessions/2026/05/19/rollout-2026-05-19T10-29-36-019e3f5a-d06e-70b2-a951-3b60b42499be.jsonl`

This file preserves the reusable decisions from the first research/grilling session so future research passes do not need the full chat transcript. It is not an evidence source for legal or provider claims; use the Evidence Register for validated sources.

## Output System

The research should be maintained as three aligned outputs:

- Board Briefing: decision-oriented material for the AI Governance and Steering Board.
- Research Dossier: source-backed legal, technical, provider, and cost research.
- Operational Policy Draft: practical rules, controls, templates, and review gates.

All three outputs should reference the shared Evidence Register where possible. Claims must distinguish Current Fact, Near-Term Development, and Speculation.

## Scope Decisions

- Primary first-pass scenario: internal employee AI workflows that may process Client Confidential Data.
- Keep customer-facing AI features and training/fine-tuning as separate higher-risk classes.
- Use Client Confidential Data as the canonical term for confidential information received from financial-sector clients, including business data, production data, documents, financial records, regulated data, and any personal data within those materials.
- Classify workflows by whether Client Confidential Data leaves the Company-Controlled Environment.
- Treat GDPR as the floor, with client confidentiality, financial-sector expectations, contractual duties, employee privacy, security controls, and provider terms layered on top.
- First jurisdictional scope: European Union, Austria, and Germany.
- Network connectivity providers are out of scope unless they directly process Client Confidential Data for AI workloads.
- AI compute providers are in scope when they affect where model workloads run or where data is processed.

## Use-Case Archetypes

The first-pass use-case archetypes are:

- General productivity.
- Software delivery.
- Knowledge retrieval.
- Client project analysis.
- Customer/service operations.
- Training/fine-tuning.
- Delivery Pipeline Systems.

Delivery Pipeline Systems are separate from general software delivery and are restricted by default because they may expose source code, tickets, build logs, deployment configuration, secrets-adjacent metadata, internal environments, and access paths.

## Governance Structure

- Use an Evidence Register with stable source and claim IDs.
- Use a strict Source Hierarchy: primary law and regulators first, authoritative vendor legal/security/product terms next, standards and expert commentary only as supporting context.
- Define Near-Term Development as evidence-backed developments expected within six months.
- Treat claims beyond six months, roadmap-like claims without enforceable commitment, and unsupported marketing claims as Speculation.
- Maintain a Decision Backlog so unresolved policy choices do not become hidden assumptions.
- Use Adoption Phases so low-risk AI workflows can proceed while sensitive workflows remain gated.
- Use a Recommendation Matrix with Governance Status labels: Allowed, Restricted, Prohibited, or Needs Decision.

## Operational Controls Agreed

- Require AI Use Case Intake before AI use with non-public data or controlled systems.
- Maintain an Approved AI Tool Registry.
- Require Employee AI Transparency Notice for employee-facing tools, especially where prompts, code, usage analytics, transcripts, telemetry, or productivity signals are logged.
- Keep Client Contract Compatibility Check human-led under the Contract Non-Ingestion Rule until policy explicitly permits otherwise.
- Assess Input Data Risk and Output Data Risk separately.
- Treat Automated Action as a separate AI Output Use Level.
- Automated delivery, release, and infrastructure actions are not a blanket red line; they may be allowed only as Technically Gated Actions.
- Maintain Red Lines and Gated Exceptions separately.
- Include Technical Control Patterns, not only legal/vendor analysis.

## Provider Comparison Scope

The first-pass Provider Comparison Scope is:

- OpenAI: ChatGPT Enterprise or Team, OpenAI API, Azure OpenAI or Microsoft-hosted variants where relevant.
- Anthropic: Claude Enterprise or API, Claude in Amazon Bedrock, Claude Platform on AWS, Vertex AI or Microsoft Foundry where relevant.
- Microsoft: Microsoft 365 Copilot, Azure AI Foundry, Azure OpenAI, Microsoft 365 data boundary and GDPR terms.
- Amazon/AWS: Amazon Bedrock, AWS European Sovereign Cloud, Bedrock data protection, regional routing, and provider-stack controls.
- Google: Gemini for Workspace, Vertex AI, Google Cloud processing and data-residency terms.
- xAI/Grok/SpaceXAI: model-provider role and AI compute-provider role where applicable.
- Self-hosted/open-weight models: Llama, Mistral, Qwen, DeepSeek-class models, and similar options evaluated by scenario.

## Provider Profile Requirements

Each provider profile should include:

- AI model provider.
- Application or product provider.
- AI compute provider.
- Cloud or infrastructure provider.
- Contracting party and legal entity where known.
- Controller/processor position.
- Processing locations.
- Provider routing constraints.
- Subprocessors and onward transfers.
- Retention and training-use terms.
- Employee AI Privacy implications.
- Cost Profile.
- Current facts, Near-Term Developments, Speculation, and uncertainty gaps.

## AWS-Only Routing Decision

The exported conversation resolved the phrase "run on AWS" as a Provider Routing Constraint requiring verification. The next provider research pass should not treat "AWS-billed" as equal to "AWS-operated" or "AWS-only processing."

The specific Anthropic/AWS distinction to research and validate from current primary sources:

- Direct Claude / Anthropic API.
- Claude in Amazon Bedrock.
- Claude Platform on AWS.
- Any disclosed compute/provider-stack variants, including xAI/Colossus-type compute relationships where relevant.

The conversation's provisional finding was:

- Claude in Amazon Bedrock appears to be the cleaner option to analyze where AWS must be the operating party.
- Claude Platform on AWS may be accessed or billed through AWS while Anthropic operates the platform; therefore it should not be assumed to mean data stays in AWS.

This must be revalidated with current official sources before becoming a policy conclusion.

## Current Next Step

Question 32 was answered "yes": start the provider pass with Anthropic/AWS, then compare OpenAI/Microsoft next.

The provider pass should produce:

- Anthropic/AWS provider profile.
- Updated Evidence Register entries for official Anthropic and AWS sources.
- Claim entries on AWS-only routing, Bedrock data isolation, Claude Platform on AWS, retention/training use, processing location, and cost-profile implications.
- Follow-on OpenAI/Microsoft comparison notes.

## Suggested Skills And Tools

- Use web research because provider documentation, legal terms, regions, pricing, and subprocessors are temporally sensitive.
- Use primary sources wherever available.
- Use the `openai-docs` skill for OpenAI API/platform claims in the OpenAI/Microsoft pass.

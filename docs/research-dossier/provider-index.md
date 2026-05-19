# Provider Index

This index lists the first-pass Provider Comparison Scope. Each provider profile should use [provider-profile-template.md](./provider-profile-template.md) and reference the evidence register.

## Provider Profiles

- [Anthropic / AWS](./provider-profiles/anthropic-aws.md)
- [OpenAI / Microsoft](./provider-profiles/openai-microsoft.md)
- [Google / Vertex AI / Gemini](./provider-profiles/google-vertex-gemini.md)
- [xAI / Grok next pass](./provider-profiles/xai-grok-next-pass.md)
- [OpenAI / Microsoft next pass](./provider-profiles/openai-microsoft-next-pass.md)

## First-Pass Providers And Options

- OpenAI: ChatGPT Enterprise or Team, OpenAI API, Azure OpenAI or Microsoft-hosted variants where relevant.
- Anthropic: Claude Enterprise or API, Claude in Amazon Bedrock, Claude Platform on AWS, Vertex AI or Microsoft Foundry where relevant.
- Microsoft: Microsoft 365 Copilot, Azure AI Foundry, Azure OpenAI, Microsoft 365 data boundary and GDPR terms.
- Amazon/AWS: Amazon Bedrock, AWS European Sovereign Cloud, Bedrock data protection, regional routing, and provider-stack controls.
- Google: Gemini for Workspace, Vertex AI, Google Cloud processing and data-residency terms.
- xAI/Grok/SpaceXAI: model-provider role and AI compute-provider role where applicable.
- Self-hosted/open-weight options: Llama, Mistral, Qwen, DeepSeek-class models, and similar options evaluated by scenario.

## Out Of Scope For Version 1

- General network connectivity providers unless they directly process Client Confidential Data for AI workloads.
- Niche AI tools unless already used, procured, or requested by a client project.
- Unsourced media claims unless validated through the Source Hierarchy.

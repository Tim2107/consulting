# Next Provider Pass: OpenAI / Microsoft

Date created: 2026-05-19

Status: research queue. Use this after the Anthropic/AWS pass.

## Purpose

Compare OpenAI/Microsoft using the same provider-stack method as the Anthropic/AWS profile. The key question is analogous: when a workflow uses OpenAI models through Microsoft/Azure, which party operates the stack, where is data processed, and which terms govern customer data?

## Scope

Profiles to produce:

- OpenAI direct API.
- ChatGPT Team / Enterprise / Edu where relevant.
- Azure OpenAI Service.
- Microsoft 365 Copilot and Microsoft 365 data boundary where relevant.
- Azure AI Foundry / Microsoft-hosted model catalog variants.
- Any disclosed OpenAI compute/provider-stack variants that affect training, fine-tuning, inference, or processing location.

## Questions To Answer

- Is the model provider OpenAI, Microsoft, or both?
- Is the customer-facing service operated by OpenAI or Microsoft?
- Which entity is the contracting party and data processor?
- Are prompts/completions available to the model provider or only to the cloud/service operator?
- What retention, abuse-monitoring, training-use, and logging terms apply?
- What regional/data-boundary controls are available?
- Is there an Azure-only or Microsoft-operated equivalent to the Bedrock question?
- How do Azure OpenAI, OpenAI direct, and Microsoft 365 Copilot differ for Client Confidential Data?
- Which features or model versions lag or differ across direct OpenAI and Microsoft-hosted routes?
- What cost premium or operational overhead comes with data-boundary, logging, private networking, provisioned throughput, or committed capacity controls?

## Evidence Sources To Prioritize

- Official OpenAI docs, enterprise privacy pages, API data-use docs, subprocessors, DPA, and trust/security materials.
- Official Microsoft Azure OpenAI Service docs, product terms, Data Protection Addendum, Trust Center, regional availability, data-zone docs, and pricing pages.
- Official Microsoft 365 Copilot data, privacy, security, and EU Data Boundary docs.
- Official OpenAI/Microsoft partnership and compute-capacity announcements only as infrastructure context, not as customer-data routing proof.

## Expected Outputs

- `docs/research-dossier/provider-profiles/openai-microsoft.md`
- Evidence Register source entries and claim entries.
- Decision Backlog update if Azure/Microsoft routing constraints remain unresolved.
- Recommendation Matrix row/column notes for direct OpenAI, Azure OpenAI, and Microsoft 365 Copilot.

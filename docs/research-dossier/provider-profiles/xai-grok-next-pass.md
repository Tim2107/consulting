# Next Provider Pass: xAI / Grok / SpaceXAI

Date created: 2026-05-19

Status: research queue. Use after the Google / Vertex AI / Gemini first-pass profile.

## Recommendation

Include xAI/Grok after Google, but keep the first pass narrower than Anthropic/AWS, OpenAI/Microsoft, and Google/Vertex.

The reason to include it is not only Grok as a user-facing chatbot or API. The more important governance angle is that xAI/SpaceXAI can be both:

- an **AI Model Provider** through Grok products and APIs; and
- an **AI Compute Provider** through Colossus-style compute arrangements that may support other model providers.

This is directly relevant to **Provider Stack**, **AI Compute Provider**, and **Processing Location** analysis.

Evidence basis for including the compute-provider angle: CLAIM-019, especially SRC-034 and SRC-035.

## Scope

Profiles to produce:

- Grok consumer and business/API routes, if enterprise terms exist.
- xAI API / developer platform, if relevant to company use.
- xAI / SpaceXAI compute-provider role, including Colossus.
- Any disclosed partnerships where xAI provides compute for Anthropic or other model providers.

## Questions To Answer

- Is there an enterprise-grade xAI/Grok route with a DPA, subprocessors, no-training terms, retention controls, and processing-location commitments?
- What is the contracting entity and controller/processor posture?
- Are prompts, completions, uploads, telemetry, or account data used for model training by default?
- Are there EU/EEA routing, residency, or processor commitments?
- Is Colossus used for training, inference, fine-tuning, or capacity overflow for customer-facing services?
- Can a customer enforce or audit whether workloads run on Colossus or another compute provider?
- How does xAI/Grok pricing compare with established enterprise routes?

## Expected Outputs

- `docs/research-dossier/provider-profiles/xai-grok.md`
- Evidence Register source and claim entries.
- Decision Backlog update if xAI/Grok is not enterprise-ready for Client Confidential Data.
- Provider Stack note distinguishing xAI as model provider from xAI/SpaceXAI as compute provider.

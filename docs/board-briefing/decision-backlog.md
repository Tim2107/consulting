# Decision Backlog

This backlog tracks unresolved AI governance decisions until they are approved, rejected, or deferred.

| Decision ID | Decision | Owner | Status | Due Date | Evidence References | Notes |
| --- | --- | --- | --- | --- | --- | --- |
| DEC-001 | Which AI tools are approved for Phase 1? | TBD | Open | TBD | TBD |  |
| DEC-002 | May Client Confidential Data ever go to approved third-party providers? | TBD | Open | TBD | TBD |  |
| DEC-003 | Are Bedrock, Azure, or Vertex routing constraints sufficient for sensitive workflows? | TBD | Open | TBD | CLAIM-016, CLAIM-017, CLAIM-018, CLAIM-025, CLAIM-026, CLAIM-032, CLAIM-033, CLAIM-034 | First-pass profiles now identify Bedrock as the AWS-operated route, Azure OpenAI / Foundry as the Microsoft-operated route, and Vertex AI regional/EU endpoints as the Google-operated route. Global endpoints and feature-level exceptions remain restricted. |
| DEC-004 | When should the company invest in managed private deployment or company-operated self-hosting? | TBD | Open | TBD | CLAIM-048, CLAIM-049, CLAIM-050, CLAIM-051, CLAIM-052, CLAIM-053, CLAIM-054 | First-pass profile recommends a 70-user RAG-first self-hosted pilot only where data control or client constraints justify the operational burden; avoid recurring training runs. |
| DEC-005 | Which Technically Gated Actions are acceptable in Delivery Pipeline Systems? | TBD | Open | TBD | TBD |  |
| DEC-006 | Is training or fine-tuning on client material ever allowed? | TBD | Open | TBD | CLAIM-013, CLAIM-054 | Default remains no; self-hosting does not make training or fine-tuning on company/client material automatically acceptable. |
| DEC-007 | Who owns the Approved AI Tool Registry? | TBD | Open | TBD | TBD |  |
| DEC-008 | Is employee HR, labor-law, or works-council review required before rollout? | TBD | Open | TBD | TBD |  |
| DEC-009 | Who owns DPIA trigger decisions for AI workflows? | TBD | Open | TBD | CLAIM-004 |  |
| DEC-010 | What minimum evidence is required for a provider Processing Location claim? | TBD | Open | TBD | CLAIM-002, CLAIM-003 |  |
| DEC-011 | Which financial-sector client engagements require DORA-style controls for AI tools? | TBD | Open | TBD | CLAIM-007 |  |
| DEC-012 | Does the company qualify directly under NIS2, or only receive NIS2-style duties through clients? | TBD | Open | TBD | CLAIM-008 |  |
| DEC-013 | Which Microsoft 365 Copilot agents, connectors, web search options, and non-OpenAI models are allowed? | TBD | Open | TBD | CLAIM-027, CLAIM-028 | Copilot inherits Microsoft 365 protections, but optional agents/connectors/web search and Anthropic model options can change data flow and EU Data Boundary posture. |
| DEC-014 | Which Gemini Enterprise connectors, agents, grounding features, and Workspace Gemini controls are allowed? | TBD | Open | TBD | CLAIM-036, CLAIM-037 | Google routes require feature-level governance because Gemini Enterprise and Workspace Gemini have connector, grounding, CSE, DLP, and regional-processing constraints. |
| DEC-015 | Should xAI/Grok be evaluated as a model provider, a compute provider, or both? | TBD | Open | TBD | CLAIM-019, CLAIM-045 | First-pass profile recommends both: xAI/Grok as model/product provider, and xAI/SpaceXAI as a compute-provider stack risk where Colossus or related capacity supports other providers. |
| DEC-016 | May xAI API or Grok Business/Enterprise process Client Confidential Data? | TBD | Open | TBD | CLAIM-039, CLAIM-040, CLAIM-041, CLAIM-042, CLAIM-043, CLAIM-044, CLAIM-046 | Candidate restricted only for enterprise routes with DPA, ZDR, regional/data-at-rest terms where needed, feature allowlists, connector governance, audit controls, and employee transparency. Consumer Grok should remain prohibited. |
| DEC-017 | What monthly budget cap and service level should the 70-user self-hosted pilot use? | TBD | Open | TBD | CLAIM-050, CLAIM-052, CLAIM-053 | Cost should be tracked per use-case category, model route, token volume, retrieval volume, indexing jobs, and security/audit overhead before scaling. |

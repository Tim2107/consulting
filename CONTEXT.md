# AI Governance Research

This context defines the shared language for evaluating AI adoption in a software consulting company serving financial-sector clients.

## Language

**Client Confidential Data**:
Confidential information received from financial-sector clients, including business data, production data, documents, financial records, regulated data, and any personal data contained inside those materials.
_Avoid_: customer data, client data

**Employee AI Privacy**:
The privacy and labor-rights concerns created when AI workflows process employee prompts, work content, identity data, access logs, communications, transcripts, or behavioral telemetry.
_Avoid_: employee monitoring, worker data

**Employee AI Transparency Notice**:
A clear notice that tells employees which AI tools are approved, what data may be submitted, what usage data is logged, who can access it, and how it may be used.
_Avoid_: AI disclosure, employee notice

**Company-Controlled Environment**:
Systems, accounts, infrastructure, and approved vendor configurations where the company controls access, retention, security policy, and contractual safeguards.
_Avoid_: internal environment, safe environment

**Privacy and Confidentiality Baseline**:
The combined governance frame for AI use that treats EU data-protection obligations as the floor and client, financial-sector, contractual, and security obligations as additional constraints.
_Avoid_: GDPR only, legal checklist

**AI Use Case Archetype**:
A category of AI-enabled workflow used to evaluate governance risk before selecting or approving specific tools.
_Avoid_: vendor category, tool list

**Delivery Pipeline Systems**:
Systems used to manage source code, work items, builds, tests, releases, deployments, and internal execution environments.
_Avoid_: CI/CD only, DevOps tools

**Restricted-by-Default Archetype**:
An AI use case category that requires explicit governance approval before use because it can expose sensitive information or affect controlled systems.
_Avoid_: allowed with caution, medium risk

**Board Briefing**:
A decision-oriented document for the AI Governance and Steering Board that summarizes findings, options, risks, and required decisions.
_Avoid_: executive summary, management report

**Research Dossier**:
A source-backed legal and technical research document that separates current facts, near-term developments, and speculation.
_Avoid_: appendix, source dump

**Operational Policy Draft**:
A draft governance document that translates approved research conclusions into practical rules, controls, and review processes.
_Avoid_: policy report, implementation guide

**Evidence Register**:
A shared register of sourced claims, risks, decisions, and assumptions used to keep governance outputs traceable and aligned.
_Avoid_: bibliography, source list

**Evidence Classification**:
A label that marks a statement as a current fact, near-term development, or speculation.
_Avoid_: confidence level, status

**Current Fact**:
A statement that is true now and supported by authoritative evidence.
_Avoid_: verified claim, fact

**Near-Term Development**:
A foreseeable AI governance, provider, legal, or technical development expected within six months and supported by concrete evidence.
_Avoid_: future trend, prediction

**Speculation**:
A plausible but not yet concrete statement, including claims beyond six months or claims lacking authoritative support.
_Avoid_: forecast, hypothesis

**Source Hierarchy**:
The ranking used to decide which evidence can support governance conclusions, prioritizing primary law, regulators, and authoritative vendor terms over commentary.
_Avoid_: source preference, citation style

**Jurisdictional Scope**:
The legal and regulatory scope for the first governance research version, covering the European Union, Austria, and Germany.
_Avoid_: Europe, DACH

**AI Model Provider**:
A third-party provider that makes frontier or foundation AI models available for use through products, APIs, or managed services.
_Avoid_: AI vendor, LLM company

**AI Infrastructure Provider**:
A third-party provider that supplies cloud, hosting, compute, networking, or managed platform infrastructure used to run, expose, or integrate AI services.
_Avoid_: cloud vendor, hyperscaler

**AI Compute Provider**:
A third-party provider that supplies compute capacity used for AI training, fine-tuning, inference, or other model workloads.
_Avoid_: data center provider, GPU provider

**Processing Location**:
The jurisdiction, facility, region, or controlled environment where data is stored, transmitted, accessed, or processed during an AI workflow.
_Avoid_: hosting location, server location

**Provider Stack**:
The set of providers and contractual layers involved in an AI workflow, including model, application, hosting, infrastructure, and integration providers.
_Avoid_: vendor, supplier

**Provider Routing Constraint**:
A required condition that limits which provider, geography, region, or compute environment may process data in an AI workflow.
_Avoid_: provider preference, deployment option

**Cost Profile**:
The cost view for an AI option, including usage price, routing or residency premiums, commitments, integration costs, controls, and operational overhead.
_Avoid_: price, license cost

**Self-Hosted AI Option**:
An AI deployment option where the company operates the model runtime and compute environment within a company-approved boundary.
_Avoid_: local model, private model

**Company-Operated Self-Hosted Option**:
A self-hosted AI option where the company operates the model runtime and compute environment inside its approved infrastructure.
_Avoid_: fully local, on-prem model

**Managed Private Deployment**:
An AI deployment option where a third party provides dedicated, isolated, or contractually constrained AI infrastructure or runtime for the company.
_Avoid_: private model, dedicated cloud

**Operational Ownership Cost**:
The cost of running an AI option beyond usage fees, including setup, hardware, hosting, maintenance, updates, monitoring, security, and specialist effort.
_Avoid_: maintenance cost, overhead

**Recommendation Matrix**:
A decision table that maps AI use case archetypes and deployment options to governance statuses, rationale, and evidence references.
_Avoid_: risk table, approval chart

**Governance Status**:
The decision label assigned to an AI workflow option: allowed, restricted, prohibited, or needs decision.
_Avoid_: risk rating, traffic light

**Provider Comparison Scope**:
The bounded set of AI model, platform, infrastructure, and self-hosted options included in the first research pass.
_Avoid_: market overview, vendor landscape

**Adoption Phase**:
A staged level of AI adoption that defines which data, tools, controls, and approvals are permitted at that maturity level.
_Avoid_: rollout wave, maturity level

**AI Use Case Intake**:
The required review record for proposed AI workflows that use non-public data or affect controlled systems.
_Avoid_: AI request, approval form

**Approved AI Tool Registry**:
The operational list of AI tools, provider options, allowed use cases, data permissions, required controls, owners, and review dates.
_Avoid_: tool list, vendor registry

**AI Output Use Level**:
The level of reliance placed on AI output: draft assistance, decision support, or automated action.
_Avoid_: output risk, human-in-the-loop level

**Automated Action**:
An AI output use level where AI output triggers, performs, or materially changes an action in a business, delivery, or client-facing system.
_Avoid_: agentic action, automation

**Technically Gated Action**:
An automated action that is allowed only through enforceable technical controls such as scoped permissions, approval gates, policy-as-code, sandboxing, logging, rollback, and separation of duties.
_Avoid_: allowed automation, controlled action

**Red Line**:
A prohibited AI use that is not allowed unless the board explicitly approves an exception.
_Avoid_: hard rule, forbidden use

**Gated Exception**:
A normally restricted AI use that may proceed only when specified governance, legal, and technical gates are satisfied.
_Avoid_: exception, conditional use

**Technical Control Pattern**:
A repeatable technical safeguard used to reduce AI workflow risk, such as access control, routing constraint, logging, sandboxing, DLP, approval gate, or rollback.
_Avoid_: mitigation, security control

**Decision Backlog**:
The board-facing list of unresolved AI governance decisions, with owners, status, due dates, and evidence references.
_Avoid_: open questions, action list

**Client Contract Compatibility Check**:
A human-led review that verifies whether a proposed AI workflow is compatible with relevant client confidentiality, outsourcing, subcontracting, transfer, and data-use obligations.
_Avoid_: contract AI review, contract upload

**Contract Non-Ingestion Rule**:
The rule that client contracts are not submitted to AI tools unless and until an approved policy explicitly permits it.
_Avoid_: no contract analysis, manual-only contracts

**Input Data Risk**:
The risk created by the data submitted to an AI workflow.
_Avoid_: prompt risk, upload risk

**Output Data Risk**:
The risk created by AI-generated content and how it is stored, shared, relied on, or used in downstream workflows.
_Avoid_: hallucination risk, result risk

## Relationships

- **Client Confidential Data** may include personal data, regulated financial information, trade secrets, or contractually confidential material.
- **Employee AI Privacy** is assessed separately from **Client Confidential Data**.
- An **Employee AI Transparency Notice** is required for employee-facing AI workflows.
- **Client Confidential Data** may stay within the **Company-Controlled Environment** or be disclosed outside it.
- Disclosure of **Client Confidential Data** outside the **Company-Controlled Environment** is a distinct governance decision.
- The **Privacy and Confidentiality Baseline** applies whenever AI workflows process **Client Confidential Data**.
- **Delivery Pipeline Systems** are a distinct **AI Use Case Archetype**, separate from general software-delivery assistance.
- **Delivery Pipeline Systems** are a **Restricted-by-Default Archetype**.
- The **Board Briefing**, **Research Dossier**, and **Operational Policy Draft** are separate outputs that must remain aligned.
- The **Evidence Register** supplies shared references for the **Board Briefing**, **Research Dossier**, and **Operational Policy Draft**.
- Every substantive sourced statement should have an **Evidence Classification**.
- A **Current Fact** must be true now and supported by authoritative evidence.
- A **Near-Term Development** is limited to a six-month time horizon.
- **Speculation** must not be used as the sole basis for a governance rule.
- The **Source Hierarchy** determines which evidence is strong enough to support a governance conclusion.
- The first research version uses the **Jurisdictional Scope**.
- An AI workflow may involve both an **AI Model Provider** and one or more **AI Infrastructure Providers**.
- An **AI Compute Provider** may be different from the **AI Model Provider**.
- The **Provider Stack** determines which provider terms, GDPR commitments, subprocessors, and data-transfer claims must be reviewed.
- The **Processing Location** must be identified for AI workflows that process **Client Confidential Data**.
- A **Provider Routing Constraint** may be required to satisfy the **Privacy and Confidentiality Baseline**.
- Each provider option should include a **Cost Profile**.
- A **Self-Hosted AI Option** can reduce some third-party disclosure risks but creates **Operational Ownership Cost**.
- A **Self-Hosted AI Option** still requires review under the **Privacy and Confidentiality Baseline** when it processes **Client Confidential Data**.
- A **Self-Hosted AI Option** may be a **Company-Operated Self-Hosted Option** or a **Managed Private Deployment**.
- A **Managed Private Deployment** remains part of the **Provider Stack** because a third party still affects processing, controls, or operations.
- The **Recommendation Matrix** assigns a **Governance Status** to each reviewed AI workflow option.
- The first **Provider Comparison Scope** includes selected third-party model providers, infrastructure providers, platform providers, and self-hosted options.
- An **Adoption Phase** translates governance decisions into a staged path for AI use.
- The **AI Use Case Intake** records the information needed to assign a **Governance Status** and **Adoption Phase**.
- The **Approved AI Tool Registry** translates the **Recommendation Matrix** into permitted tools and conditions.
- The **AI Output Use Level** affects required controls and approvals.
- **Automated Action** is a **Restricted-by-Default Archetype** when it involves **Client Confidential Data** or **Delivery Pipeline Systems**.
- An **Automated Action** in **Delivery Pipeline Systems** may be permitted as a **Technically Gated Action**.
- A **Red Line** blocks AI use unless the board explicitly approves an exception.
- A **Gated Exception** may proceed only when its required gates are satisfied.
- A **Technical Control Pattern** supports a **Gated Exception** or **Governance Status**.
- The **Decision Backlog** tracks unresolved governance decisions until they are approved, rejected, or deferred.
- A **Client Contract Compatibility Check** may be required before AI workflows process **Client Confidential Data**.
- The **Contract Non-Ingestion Rule** applies until an approved policy explicitly permits AI use on client contracts.
- **Input Data Risk** and **Output Data Risk** are assessed separately.
- **Output Data Risk** affects the required **AI Output Use Level** controls.

## Example dialogue

> **AI Governance Board member:** "Can this workflow process **Client Confidential Data**?"
> **Domain expert:** "Only if the tool, legal basis, contractual controls, and technical safeguards are approved for that data class."
>
> **AI Governance Board member:** "If no client data is involved, are privacy concerns gone?"
> **Domain expert:** "No — **Employee AI Privacy** may still apply to prompts, logs, transcripts, telemetry, or work-content analysis."
>
> **AI Governance Board member:** "How do employees know what AI usage is logged?"
> **Domain expert:** "Use an **Employee AI Transparency Notice** for approved employee-facing AI workflows."
>
> **AI Governance Board member:** "Does the data leave the **Company-Controlled Environment**?"
> **Domain expert:** "That boundary determines the level of vendor, legal, and client-contract review."
>
> **AI Governance Board member:** "Is GDPR enough for this review?"
> **Domain expert:** "No — the **Privacy and Confidentiality Baseline** also includes client confidentiality, financial-sector expectations, contracts, and security controls."
>
> **AI Governance Board member:** "Is AI in deployment tooling just part of software delivery?"
> **Domain expert:** "No — **Delivery Pipeline Systems** are reviewed separately because they can expose code, tickets, build logs, deployment settings, and internal environments."
>
> **AI Governance Board member:** "Can we allow pipeline AI when no personal data is present?"
> **Domain expert:** "Not automatically — **Delivery Pipeline Systems** remain a **Restricted-by-Default Archetype** because sensitivity is broader than personal data."
>
> **AI Governance Board member:** "Can we combine the research, briefing, and policy into one document?"
> **Domain expert:** "No — the **Board Briefing**, **Research Dossier**, and **Operational Policy Draft** serve different audiences and must be maintained as separate but aligned outputs."
>
> **AI Governance Board member:** "How do we keep a policy rule connected to the research that justified it?"
> **Domain expert:** "Reference the same entry in the **Evidence Register**, including its **Evidence Classification**."
>
> **AI Governance Board member:** "How far ahead can we call something near-term?"
> **Domain expert:** "A **Near-Term Development** must be expected within six months and supported by concrete evidence."
>
> **AI Governance Board member:** "Can we approve a workflow because a vendor says a control is coming someday?"
> **Domain expert:** "No — that is **Speculation** unless it is a concrete **Near-Term Development** with evidence."
>
> **AI Governance Board member:** "Can we base a policy rule on an analyst article?"
> **Domain expert:** "Only if the **Source Hierarchy** supports it; commentary can explain context, but primary law, regulators, and authoritative vendor terms carry the conclusion."
>
> **AI Governance Board member:** "Is reviewing OpenAI's model terms enough if the service runs through Azure?"
> **Domain expert:** "No — the **Provider Stack** must identify the **AI Model Provider**, **AI Infrastructure Provider**, and any other contractual layer that can affect data handling."
>
> **AI Governance Board member:** "Does it matter where a model actually runs?"
> **Domain expert:** "Yes — the **AI Compute Provider** and **Processing Location** determine which technical safeguards, legal terms, and transfer risks must be reviewed."
>
> **AI Governance Board member:** "Can we require a provider to process data only through a specific platform or geography?"
> **Domain expert:** "That is a **Provider Routing Constraint**, and the research must show whether it is available, enforceable, and what it costs."
>
> **AI Governance Board member:** "Can we avoid privacy risk by running a model locally?"
> **Domain expert:** "A **Self-Hosted AI Option** can reduce provider disclosure, but it still has security, model, hardware, and **Operational Ownership Cost** that must be assessed."
>
> **AI Governance Board member:** "Is a dedicated cloud-hosted model the same as running it ourselves?"
> **Domain expert:** "No — distinguish a **Company-Operated Self-Hosted Option** from a **Managed Private Deployment** because the provider chain and ownership costs differ."
>
> **AI Governance Board member:** "How do we turn research into a board decision?"
> **Domain expert:** "Use the **Recommendation Matrix** to assign a **Governance Status** with rationale and evidence references."
>
> **AI Governance Board member:** "Are we comparing the whole AI market?"
> **Domain expert:** "No — the **Provider Comparison Scope** bounds the first pass to realistic providers and deployment options."
>
> **AI Governance Board member:** "How do we start using AI without approving everything?"
> **Domain expert:** "Use **Adoption Phases** so low-risk workflows can proceed while sensitive workflows remain gated."
>
> **AI Governance Board member:** "How does a team get a new AI workflow reviewed?"
> **Domain expert:** "They submit an **AI Use Case Intake** before using non-public data or connecting AI to controlled systems."
>
> **AI Governance Board member:** "How does an employee know which AI tool is allowed?"
> **Domain expert:** "They check the **Approved AI Tool Registry** for the permitted use cases, data classes, and required controls."
>
> **AI Governance Board member:** "Is AI drafting a ticket comment the same as AI changing deployment settings?"
> **Domain expert:** "No — the **AI Output Use Level** is different, and **Automated Action** requires stronger approval."
>
> **AI Governance Board member:** "Can AI ever trigger deployments or infrastructure changes?"
> **Domain expert:** "Yes, but only as a **Technically Gated Action** with enforceable controls."
>
> **AI Governance Board member:** "Are all risky AI uses prohibited?"
> **Domain expert:** "No — distinguish a **Red Line** from a **Gated Exception**."
>
> **AI Governance Board member:** "How do we know whether a risky AI workflow can be controlled?"
> **Domain expert:** "Map the workflow to required **Technical Control Patterns**."
>
> **AI Governance Board member:** "Where do unresolved policy choices go?"
> **Domain expert:** "They belong in the **Decision Backlog** with owners, status, due dates, and evidence references."
>
> **AI Governance Board member:** "Can we ask AI to read the client contract to check whether AI use is allowed?"
> **Domain expert:** "No — the **Contract Non-Ingestion Rule** applies; the **Client Contract Compatibility Check** is human-led unless policy later permits otherwise."
>
> **AI Governance Board member:** "If the input is non-confidential, is the workflow low-risk?"
> **Domain expert:** "Not necessarily — **Output Data Risk** must still be assessed separately from **Input Data Risk**."

## Flagged ambiguities

- "customer data" was used broadly; resolved: use **Client Confidential Data** when referring to confidential information received from financial-sector clients.
- "employee monitoring" was too narrow; resolved: use **Employee AI Privacy** for privacy and labor-rights concerns created by AI processing of employee-related data.
- "employee disclosure" was clarified; resolved: use **Employee AI Transparency Notice** for approved tool, logging, access, and usage disclosures.
- "internal" was too vague; resolved: use **Company-Controlled Environment** for systems and vendor configurations where the company controls access, retention, security policy, and contractual safeguards.
- "privacy" was too narrow on its own; resolved: use **Privacy and Confidentiality Baseline** when referring to the full governance frame for AI use with financial-sector client material.
- "CI/CD" was too narrow for the intended scope; resolved: use **Delivery Pipeline Systems** for source-control, work-item, build, release, deployment, and internal-environment tooling.
- "high sensitivity" was clarified; resolved: use **Restricted-by-Default Archetype** for AI workflow categories that require explicit governance approval before use.
- "document output" was split; resolved: maintain separate **Board Briefing**, **Research Dossier**, and **Operational Policy Draft** outputs.
- "source appendix" was too passive; resolved: use an **Evidence Register** with stable entries and an **Evidence Classification** for current facts, near-term developments, and speculation.
- "near-term" was scoped; resolved: use **Near-Term Development** for evidence-backed developments expected within six months.
- "speculation" was scoped; resolved: use **Speculation** for plausible claims beyond six months or lacking authoritative support.
- "sources" was clarified; resolved: use a **Source Hierarchy** that prioritizes primary law, regulators, and authoritative vendor terms over commentary.
- "jurisdiction" was scoped; resolved: the first version uses the **Jurisdictional Scope** of the European Union, Austria, and Germany.
- "AI provider" was too broad; resolved: distinguish **AI Model Provider**, **AI Infrastructure Provider**, and the full **Provider Stack**.
- "SpacexAI" was clarified; resolved: network connectivity is out of scope, but AI compute arrangements are in scope when they affect where model workloads run or where **Client Confidential Data** is processed.
- "run on AWS" was clarified; resolved: treat this as a **Provider Routing Constraint** and verify whether the relevant option is AWS-operated, Anthropic-operated, or merely AWS-billed.
- "cost" was clarified; resolved: use **Cost Profile** rather than simple list price.
- "local model" was clarified; resolved: use **Self-Hosted AI Option** for company-operated model runtimes and include **Operational Ownership Cost**.
- "self-hosted" was split; resolved: distinguish **Company-Operated Self-Hosted Option** and **Managed Private Deployment**.
- "recommendation" was clarified; resolved: use a **Recommendation Matrix** with a **Governance Status** of allowed, restricted, prohibited, or needs decision.
- "provider comparison" was bounded; resolved: use **Provider Comparison Scope** for the first-pass provider and deployment option set.
- "adoption path" was clarified; resolved: use **Adoption Phase** for staged AI adoption with explicit data, tool, control, and approval boundaries.
- "approval form" was clarified; resolved: use **AI Use Case Intake** for the required review record before AI use with non-public data or controlled systems.
- "approved tools" was clarified; resolved: use **Approved AI Tool Registry** as the operational list of permitted tools and conditions.
- "AI output use" was clarified; resolved: use **AI Output Use Level** with draft assistance, decision support, and **Automated Action**.
- "automated deployment" was refined; resolved: treat automated delivery, release, and infrastructure changes as **Technically Gated Action**, not categorically prohibited.
- "prohibited use" was split; resolved: distinguish **Red Line** and **Gated Exception**.
- "technical safeguards" was clarified; resolved: use **Technical Control Pattern** for repeatable AI workflow safeguards.
- "open questions" was clarified; resolved: use **Decision Backlog** for unresolved AI governance decisions.
- "contract review" was clarified; resolved: keep the **Client Contract Compatibility Check** human-led under the **Contract Non-Ingestion Rule** until policy permits otherwise.
- "AI risk" was split; resolved: assess **Input Data Risk** and **Output Data Risk** separately.

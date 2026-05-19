# Decision Packet: Delivery Pipeline Systems And Technically Gated Actions

Status: board-ready draft for DEC-005. This packet defines which AI-assisted actions in Delivery Pipeline Systems may be allowed and which remain prohibited unless separately approved.

## Decision Requested

The board should decide which AI-assisted Delivery Pipeline Systems actions are acceptable as **Technically Gated Actions**.

## Recommended Board Resolution

Approve the following position:

- Delivery Pipeline Systems remain a Restricted-by-Default Archetype because they can expose source code, tickets, build logs, deployment configuration, secrets-adjacent metadata, internal environments, and production access paths.
- AI may assist Delivery Pipeline Systems only through approved tools, approved data classes, and enforceable technical gates.
- AI-generated recommendations, code changes, workflow edits, deployment plans, infrastructure plans, and rollback plans must be reviewed before execution.
- AI must not hold standing production credentials, bypass branch protections, bypass required reviewers, bypass deployment approvals, or directly push to protected branches.
- Production-impacting actions require human approval, scoped temporary credentials, protected environments, policy-as-code checks, audit logs, rollback plans, and separation of duties.
- Unreviewed code must not run in CI jobs with access to production secrets or sensitive deployment environments.

## Action Classification

| Action Type | Examples | Recommended Status | Required Gates |
| --- | --- | --- | --- |
| Read-only delivery assistance | Summarize CI failure, explain test logs, draft release notes, identify likely flaky tests | Allowed in approved tools | No secrets in prompts/logs; approved data class; employee transparency if user telemetry is logged. |
| Draft-only change proposal | Generate patch, workflow YAML suggestion, Terraform plan explanation, rollback checklist | Restricted | Pull request required; human review; secret scanning; no direct write to protected branches. |
| Non-production validation | Run tests, lint, static analysis, dependency scan, policy checks in sandbox | Restricted | Ephemeral runner; least-privilege token; no production secrets; logs retained and reviewed. |
| Pull request creation | Open PR with generated code or pipeline config | Restricted | Branch protection, required checks, CODEOWNERS/reviewer rule, signed commit where required. |
| Pipeline configuration change | Modify CI/CD workflow, deployment job, runner config, approval gate, or secret access | Restricted high-assurance | Security/code-owner review; protected branch; no self-approval; policy-as-code validation; audit log. |
| Non-production deployment | Deploy to dev/test/sandbox environment | Restricted | Environment-specific credentials; deployment approval where needed; no production data; rollback path. |
| Production deployment | Deploy application, infrastructure, database migration, or release flag to production | Restricted high-assurance | Required reviewer; protected environment; separation of duties; temporary scoped credentials; policy checks; rollback; incident owner. |
| Automated rollback | Revert deployment or infrastructure change after health failure | Restricted high-assurance | Pre-approved rollback playbook; bounded action; telemetry trigger; human notification; post-action review. |
| Secret, credential, or access change | Rotate, create, grant, or expose credentials/permissions | Prohibited by default | Separate Security approval; no AI direct action; break-glass process only. |
| Direct autonomous production change | AI directly changes production without human gate | Prohibited | Board exception required. |

## Minimum Technical Gates

Every Technically Gated Action in Delivery Pipeline Systems must have:

1. **Registered workflow**: recorded in the AI Use Case Intake and Approved AI Tool Registry.
2. **Approved data class**: no Client Confidential Data unless the route is separately approved.
3. **Scoped identity**: AI/tool identity separate from human users, with least privilege and no standing broad production credentials.
4. **Temporary credentials**: prefer OIDC or equivalent short-lived credentials over long-lived secrets.
5. **Protected branches**: no direct push to protected branches; required reviews and required status checks for merges.
6. **Protected environments**: deployment approvals, branch/environment restrictions, and no self-approval for sensitive environments.
7. **Pipeline isolation**: unreviewed code runs in isolated jobs without production secrets.
8. **Policy-as-code**: enforceable checks for deployment target, region, secrets, privileged permissions, artifact integrity, and change type.
9. **Artifact integrity**: signed artifacts, provenance, digest pinning, or equivalent validation for production releases.
10. **Logging and evidence**: prompt, decision, tool call, workflow run, approval, artifact, deployment, and rollback evidence retained.
11. **Rollback path**: documented and tested rollback for production-impacting actions.
12. **Separation of duties**: requester, reviewer, and production approver cannot collapse into one unchecked AI-mediated action.

## DEC-005 Options

| Option | Description | Pros | Risks | Recommendation |
| --- | --- | --- | --- | --- |
| A | Prohibit all AI involvement in Delivery Pipeline Systems. | Simple and maximally cautious. | Blocks useful diagnosis, documentation, and safe draft assistance. | Not recommended. |
| B | Allow read-only and draft assistance only. | Low operational risk. | Does not capture value from safe automation or gated non-prod actions. | Good minimum baseline. |
| C | Allow Technically Gated Actions with strict controls. | Enables useful automation while preserving human accountability and auditability. | Requires engineering work and ongoing control ownership. | Recommended. |
| D | Allow AI agents to deploy independently in approved repositories. | Fastest automation path. | Too much risk: production access, secret exposure, policy bypass, and unclear accountability. | Not recommended. |

## Immediate Red Lines

- No AI direct push to protected branches.
- No AI bypass of pull request review, required checks, deployment approvals, or branch/environment protection.
- No AI access to broad standing production credentials.
- No unreviewed fork/PR code running with production secrets.
- No AI-created or AI-modified CI/CD workflow becoming active without code-owner and Security review.
- No autonomous production deployment or infrastructure change without a human approval gate.
- No secrets or production tokens in prompts, chat logs, generated patches, or artifacts.

## Recommended Approval Wording

> The board approves Technically Gated Actions as the only permitted path for AI-assisted Delivery Pipeline Systems automation. Read-only assistance and draft-only change proposals may proceed in approved tools. Non-production actions, pull request creation, pipeline configuration changes, production deployments, and rollbacks require enforceable technical gates, including least privilege, temporary credentials, protected branches and environments, policy-as-code, artifact integrity validation, logging, rollback, and separation of duties. Direct autonomous production changes, secret or credential changes, and bypass of required reviews or deployment approvals remain prohibited unless the board approves a specific exception.

## Follow-On Implementation Work

- Update Approved AI Tool Registry entries with exact Delivery Pipeline Systems permissions.
- Define CI/CD policy-as-code checks for protected branches, environments, credentials, artifacts, and deployment targets.
- Build a standard AI-assisted PR workflow for draft-only changes.
- Add pipeline-specific fields to the AI Use Case Intake where needed.
- Assign owners for policy-as-code, runner isolation, deployment approvals, and audit evidence.

## Evidence References

- CLAIM-055 through CLAIM-061.
- CLAIM-007 and CLAIM-008 for financial-sector and NIS2/DORA-style ICT risk context.

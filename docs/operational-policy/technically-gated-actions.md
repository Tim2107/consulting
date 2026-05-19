# Technically Gated Actions For Delivery Pipeline Systems

Status: operational draft. Use this with the AI Use Case Intake, Approved AI Tool Registry, Data-Class Routing Policy, and repository-specific engineering standards.

## Purpose

Technically Gated Actions allow AI-assisted automation in Delivery Pipeline Systems only when the action is constrained by enforceable technical controls. A policy statement alone is not sufficient.

## Allowed Action Levels

| Level | Description | Examples | Default Status |
| --- | --- | --- | --- |
| TGA-0 | Read-only assistance | Explain failed tests, summarize logs, draft release notes | Allowed in approved tools |
| TGA-1 | Draft-only proposal | Generate patch, workflow suggestion, Terraform plan explanation | Restricted |
| TGA-2 | Sandbox validation | Run tests, lint, static analysis, policy checks in isolated environment | Restricted |
| TGA-3 | Pull request creation | Create PR with generated code or configuration | Restricted |
| TGA-4 | Non-production action | Deploy to dev/test, update sandbox config, run test migration | Restricted high-assurance |
| TGA-5 | Production-impacting action | Production deployment, infrastructure apply, migration, feature-flag change, rollback | Restricted high-assurance |
| TGA-X | Prohibited direct action | Direct production change without human gate, broad credential change, bypass of approvals | Prohibited |

## Required Controls By Level

| Control | TGA-0 | TGA-1 | TGA-2 | TGA-3 | TGA-4 | TGA-5 |
| --- | --- | --- | --- | --- | --- | --- |
| Approved tool/route | Required | Required | Required | Required | Required | Required |
| Data classification | Required | Required | Required | Required | Required | Required |
| Secret filtering | Required | Required | Required | Required | Required | Required |
| Human review | Recommended | Required | Required | Required | Required | Required |
| Branch protection | N/A | Required for merge | Required for merge | Required | Required | Required |
| Environment protection | N/A | N/A | Recommended | Recommended | Required | Required |
| Least-privilege token | N/A | Required if tool writes | Required | Required | Required | Required |
| Temporary credentials/OIDC | N/A | Recommended | Required where cloud access exists | Required where cloud access exists | Required | Required |
| Runner isolation | N/A | Recommended | Required | Required | Required | Required |
| Policy-as-code | N/A | Recommended | Required | Required | Required | Required |
| Artifact integrity/provenance | N/A | Recommended | Recommended | Required for release artifacts | Required | Required |
| Rollback plan | N/A | N/A | N/A | Recommended | Required | Required |
| Audit evidence | Required | Required | Required | Required | Required | Required |
| Separation of duties | N/A | Recommended | Recommended | Required for sensitive repos | Required | Required |

## Baseline Engineering Requirements

- AI tools must use a distinct service identity or app identity where they write to repositories, issue trackers, package registries, cloud accounts, or deployment systems.
- AI-generated changes must enter through pull requests, not direct pushes to protected branches.
- Pipeline configuration changes require CODEOWNERS or equivalent owner review plus Security review.
- Unreviewed code from forks or pull requests must not run with production secrets or privileged cloud credentials.
- Workflow tokens must be read-only by default and elevated only per job or environment.
- Cloud access should use OIDC or equivalent short-lived credentials rather than static secrets.
- Production deployments must use protected environments, required reviewers, deployment branch/tag restrictions, and no self-approval.
- Production artifacts must be tied to approved source and build evidence, using signatures, provenance, digest pinning, or equivalent controls.
- AI-generated infrastructure plans must be reviewed before apply.
- Automated rollbacks must be bounded to pre-approved rollback playbooks and must notify accountable humans.
- Prompt/output/tool-call logs and workflow evidence must be retained according to the registry row and incident-response needs.

## Prohibited Patterns

- AI agent has admin access to source control, CI/CD, cloud accounts, or package registries.
- AI agent can approve its own pull request or deployment.
- AI can push directly to `main`, release branches, or protected environment configuration.
- AI can edit workflow files that grant itself broader permissions without owner and Security review.
- AI can read or print production secrets in prompts, generated code, console logs, artifacts, or summaries.
- AI can run unreviewed code with production credentials.
- AI can deploy to production without a human gate and rollback path.
- AI can change IAM, secrets, network policy, or production data stores without separate Security approval.

## Evidence To Retain

For each TGA-3 through TGA-5 workflow, retain:

- Intake ID and registry route.
- Prompt or instruction summary.
- Tool identity and human requester.
- Pull request, diff, and review evidence.
- Policy-as-code results.
- Test/security scan results.
- Artifact digest, signature, provenance, or release manifest.
- Deployment approval and environment.
- Runtime/deployment logs.
- Rollback record or rollback test evidence.
- Post-action review for production-impacting actions.

## Operational Owners

- Platform Engineering: runner isolation, deployment environments, artifact integrity, rollback tooling.
- Security: secrets policy, token scopes, policy-as-code, incident response, audit review.
- Delivery Lead: workflow purpose, business approval, release readiness, post-action review.
- Repository Owners: CODEOWNERS, branch protections, review rules, workflow ownership.
- Legal/Data Protection: client-contract compatibility and Employee AI Transparency Notice where needed.

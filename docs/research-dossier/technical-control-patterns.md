# Technical Control Patterns

This document maps repeatable technical safeguards to AI workflow risks.

## Control Pattern Template

### Control Name

- Purpose:
- Applies to:
- Risk addressed:
- Required for:
- Implementation examples:
- Evidence references:
- Limitations:
- Operational owner:

## Initial Control Pattern List

- Data classification and prompt or upload controls
- SSO, SCIM, MFA, RBAC, and least privilege
- Tenant isolation and private networking
- Logging, audit trails, and SIEM integration
- Retention controls and zero-data-retention options
- Provider routing constraints and region restrictions
- Secret scanning and prompt filtering
- DLP for uploads, browser extensions, and desktop agents
- Sandboxing and environment isolation
- Human approval gates
- Policy-as-code for CI/CD actions
- Rollback and change-management integration
- Output validation and source citation requirements

## Delivery Pipeline Systems Control Patterns

### Protected Branch And Pull Request Gate

- Purpose: prevent AI-generated or AI-mediated changes from bypassing human review.
- Applies to: code, workflow files, infrastructure-as-code, release configuration, deployment manifests.
- Risk addressed: unauthorized source changes, poisoned pipeline execution, unreviewed deployment logic.
- Required for: TGA-1 and above.
- Implementation examples: protected branches, required pull request reviews, required status checks, CODEOWNERS, no direct pushes.
- Evidence references: CLAIM-057, CLAIM-058, CLAIM-060.
- Limitations: review quality still depends on reviewer competence and scope.
- Operational owner: repository owner and Security.

### Isolated Runner And Secret Boundary

- Purpose: keep unreviewed or AI-generated code away from production secrets and sensitive environments.
- Applies to: CI jobs, PR validation, fork builds, generated code validation.
- Risk addressed: poisoned pipeline execution and credential exfiltration.
- Required for: TGA-2 and above.
- Implementation examples: ephemeral runners, no production secrets in PR jobs, separate validation and deployment workflows, minimal job permissions.
- Evidence references: CLAIM-056, CLAIM-057, CLAIM-058, CLAIM-059.
- Limitations: isolation must include caches, artifacts, network access, and self-hosted runner state.
- Operational owner: Platform Engineering and Security.

### Temporary Scoped Credentials

- Purpose: avoid standing broad credentials in AI-assisted workflows.
- Applies to: cloud access, package registries, deployment systems, source-control automation.
- Risk addressed: credential theft, overprivileged tokens, impossible attribution.
- Required for: TGA-2 through TGA-5 where privileged access exists.
- Implementation examples: OIDC federation, short-lived credentials, job-specific permissions, environment-scoped secrets, credential rotation.
- Evidence references: CLAIM-059, CLAIM-060.
- Limitations: temporary credentials still need precise scopes and audience restrictions.
- Operational owner: Security and Platform Engineering.

### Protected Deployment Environment

- Purpose: ensure deployments require environment-specific approval and constraints.
- Applies to: dev, test, staging, production, client environments.
- Risk addressed: accidental or unauthorized deployment, environment drift, self-approval.
- Required for: TGA-4 and TGA-5.
- Implementation examples: required reviewers, environment branch rules, custom deployment protection rules, no self-review, deployment history.
- Evidence references: CLAIM-060.
- Limitations: approval gates can become rubber stamps unless approvers have useful evidence.
- Operational owner: Platform Engineering and release owner.

### Policy-As-Code Gate

- Purpose: make deployment and infrastructure rules machine-enforceable.
- Applies to: infrastructure-as-code, Kubernetes manifests, CI/CD workflow configuration, deployment plans.
- Risk addressed: policy bypass, unsafe regions, privileged permissions, missing controls.
- Required for: TGA-2 and above; mandatory for TGA-4 and TGA-5.
- Implementation examples: OPA/Rego, admission controls, CI policy checks, deployment target allowlists, region allowlists.
- Evidence references: CLAIM-061.
- Limitations: policy coverage must be tested; policy engines can be misconfigured.
- Operational owner: Security and Platform Engineering.

### Artifact Integrity And Provenance Gate

- Purpose: tie production deployments to reviewed source and trusted build evidence.
- Applies to: packages, containers, release bundles, deployment manifests.
- Risk addressed: artifact tampering, dependency chain abuse, improper artifact integrity validation.
- Required for: TGA-3 release artifacts and all TGA-5 production deployments.
- Implementation examples: signed artifacts, SLSA provenance, digest pinning, SBOM/attestation checks.
- Evidence references: CLAIM-056, CLAIM-057.
- Limitations: provenance does not prove the source is safe; it proves how the artifact was built.
- Operational owner: Platform Engineering and Security.

# Change Management Policy

**Document Owner:** VP Engineering
**Approved By:** CISO
**Classification:** Internal
**ISO/IEC 27001:2022 Reference:** Controls A.8.32, A.8.9, A.8.31, A.8.19, A.5.8
**Review Cycle:** Annual

## 1. Purpose

Ensures that changes to production systems, infrastructure, and application code are authorized, tested, peer-reviewed, and traceable, minimizing the risk of unauthorized or defective changes disrupting service or introducing vulnerabilities.

## 2. Scope

Applies to all changes to production infrastructure (AWS), application source code (GitHub Enterprise), and CI/CD pipeline configuration (GitHub Actions) within ISMS scope.

## 3. Change Classification

| Type | Definition | Approval Path |
|---|---|---|
| Standard | Pre-approved, low-risk, routine (e.g., dependency patch, config value) | Standard PR review (1 approver) |
| Normal | Application feature or infrastructure change with moderate risk | PR review (1 approver, 2 for payments/auth code paths) + passing CI |
| Emergency | Production incident hotfix | Expedited review, retrospective full review within 24 hours |

## 4. Source Control and Peer Review (Control A.8.32)

1. All production code changes are made via pull request (PR) in GitHub Enterprise. Direct commits to protected branches (`main`, `release/*`) are disabled at the branch-protection level.
2. Every PR requires at least one approval from a reviewer who is not the author before merge. Changes touching payment processing, authentication, or authorization logic require two approvals, at least one from a designated senior engineer.
3. Branch protection rules enforce: required status checks (build, unit tests, SAST scan) passing, up-to-date branch before merge, and no force-push to protected branches.
4. Approval and merge events are logged and retained in GitHub's audit log, exportable as evidence (see `Technical_Evidence_Samples/github-pr-approval-logs.json`).

## 5. Environment Segregation (Control A.8.31)

1. Development, staging, and production environments are logically and technically separated: distinct AWS accounts per environment, distinct IAM roles, no shared credentials.
2. Production data is not used in development or staging environments except where irreversibly anonymized/synthesized; the use of production PII in lower environments is prohibited under the Information Classification Policy.

## 6. CI/CD Pipeline Controls (Control A.8.9, A.8.19)

1. Infrastructure changes are managed as code (Terraform) and go through the same PR/review process as application code.
2. CI/CD pipelines run static application security testing (SAST) and dependency vulnerability scanning on every PR; a critical/high finding blocks merge pending remediation or a documented risk acceptance.
3. Deployment to production requires a successful pipeline run and is executed via automated CD (no manual `kubectl`/console deploys to production), with all deploys logged with commit SHA, actor, and timestamp.
4. Software installation on production systems outside the CI/CD pipeline is prohibited; ECS task definitions are immutable and rebuilt through the pipeline, not patched in place.

## 7. Change Advisory and Emergency Changes

1. Normal changes with customer-facing impact (e.g., scheduled maintenance) are communicated to affected customers per the incident/change communication runbook.
2. Emergency changes may bypass the standard two-reviewer requirement for payments/auth code only with sign-off from the on-call engineering lead, and must receive full retrospective review and be logged in the change register within 24 hours.

## 8. Rollback and Testing

1. All production changes must have a documented rollback plan (automated rollback via CD tooling preferred).
2. Changes affecting the payroll calculation engine require a parallel-run/regression test against a reference dataset before promotion to production.

## 9. Revision History

| Version | Date | Change | Author |
|---|---|---|---|
| 1.0 | 2025-02-15 | Initial issuance | VP Engineering |
| 1.1 | 2025-10-01 | Added two-approver requirement for payments/auth code paths | VP Engineering |

# Access Control Policy

**Document Owner:** Head of IT/Security
**Approved By:** CISO
**Classification:** Internal
**ISO/IEC 27001:2022 Reference:** Controls A.5.15, A.5.16, A.5.17, A.5.18, A.8.2, A.8.3, A.8.5
**Review Cycle:** Annual

## 1. Purpose

Defines how PayBridges grants, reviews, and revokes access to information systems and data, ensuring access is limited to what is necessary for an individual's role (least privilege) and that all access is attributable to a uniquely identified person.

## 2. Scope

Applies to all access to AWS infrastructure, GitHub, Okta-federated applications, and any system processing PayBridges customer data.

## 3. Identity Management (Control A.5.16)

1. Okta is the single source of truth for workforce identity. Every employee and contractor is provisioned exactly one Okta identity tied to their corporate email.
2. Shared or generic accounts are prohibited in production systems except for documented service accounts, which must be owned by a named individual and inventoried in the asset register.
3. Identity lifecycle (joiner/mover/leaver) is triggered from the HRIS system of record and provisioned/deprovisioned through Okta Lifecycle Management workflows.

## 4. Authentication (Control A.5.17, A.8.5)

1. Multi-factor authentication (MFA) is mandatory for all Okta-federated access, without exception, including break-glass accounts.
2. Phishing-resistant MFA factors (Okta Verify push with number matching, or FIDO2/WebAuthn) are required for access to AWS production accounts, GitHub org-owner roles, and any system in-scope for the ISMS.
3. Passwords, where still used as a factor, must meet a minimum of 14 characters and are checked against known-breached-password lists at set time. No mandatory periodic rotation is enforced for passwords meeting this strength (aligned to NIST 800-63B); rotation is event-driven (suspected compromise, role change).
4. Service-to-service authentication uses short-lived credentials issued via AWS IAM roles / STS, not long-lived static keys, except where a documented exception exists.

## 5. Access Provisioning and Role-Based Access Control (Control A.5.15, A.8.3)

1. Access is granted on a role-based access control (RBAC) model. Standard roles (Engineer, DevOps, Support-Tier1, Support-Tier2, People-Ops, Finance) map to pre-defined AWS IAM policies, GitHub team memberships, and Okta application assignments.
2. Access requests outside standard role templates require manager approval and, for production data access, data owner approval, logged in the ticketing system.
3. Access to production customer data (payroll/PII) is restricted to roles with an explicit, documented business need; engineering access to production databases is access-restricted and time-boxed by default.

## 6. Privileged Access Management (Control A.8.2)

1. Privileged access (AWS root, IAM admin, GitHub org-owner, production database admin) is limited to a named, minimal set of individuals, reviewed quarterly.
2. Just-in-time (JIT) elevation is used for production infrastructure access: engineers request time-boxed elevated AWS IAM permissions (default: 4-hour session) through the internal access-request tool, approved by an on-call lead, and automatically revoked at session expiry.
3. All privileged sessions are logged to CloudTrail and retained per the Logging control (A.8.15).

## 7. Access Review (Control A.5.18)

1. Standard user access is reviewed quarterly by system/data owners; privileged access is reviewed monthly.
2. Access for terminated employees is revoked within 24 hours of the termination effective date, and immediately for involuntary terminations (Control A.6.5).
3. Access reviews and their evidence (sign-off, exceptions remediated) are retained for a minimum of 2 years to support audit sampling.

## 8. Exceptions

Any deviation from this policy (e.g., a legacy static credential still in use) must be documented in the exception register with a compensating control, owner, and remediation target date, and approved by the CISO.

## 9. Revision History

| Version | Date | Change | Author |
|---|---|---|---|
| 1.0 | 2025-02-01 | Initial issuance | Head of IT/Security |
| 1.1 | 2025-09-10 | Added JIT elevation requirement following risk register finding RR-04 | Head of IT/Security |

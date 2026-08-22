# Executive Summary & Business Context

## Purpose of This Document

This document establishes the business context for PayBridges' Information Security Management System (ISMS) implementation and ISO/IEC 27001:2022 certification readiness program. It is the reference point every other artifact in this repository — the risk register, the Statement of Applicability, the audit workpapers, and the remediation log — is built against.

## Organization Overview

**PayBridges** is a cloud-native B2B SaaS platform providing automated global payroll processing and employee records management for mid-market and enterprise customers. The platform ingests and processes some of the most sensitive categories of personal data an organization can hold: government identifiers, banking and direct-deposit details, compensation history, and immigration/work-authorization records.

| Attribute | Detail |
|---|---|
| Industry | Cloud-native Fintech / HR Technology |
| Core product | Automated payroll processing, HRIS, benefits administration |
| Headcount | ~120 employees (55% Engineering & DevOps) |
| Infrastructure | 100% AWS (RDS, S3, ECS, KMS), Okta SSO, GitHub Enterprise CI/CD |
| Customer base | 140+ enterprise customers across US, UK, and EU |
| Data processed | Employee PII, banking/payment details, payroll and tax records |

## Business Drivers for ISO/IEC 27001:2022 Certification

1. **Enterprise sales friction.** PayBridges' pipeline is increasingly gated by security questionnaires (CAIQ, SIG Lite) and direct requests for ISO 27001 or SOC 2 Type II evidence before contract signature. Two enterprise deals in the last two quarters stalled specifically on the absence of a certified ISMS.
2. **SOC 2 Type II alignment.** PayBridges already undergoes an annual SOC 2 Type II audit. Rather than run two disconnected compliance programs, the ISMS is designed so the Statement of Applicability cross-maps directly to the AICPA Trust Services Criteria, reducing duplicate evidence collection.
3. **Regulatory and contractual exposure.** As a processor of PII and financial data across multiple jurisdictions (GDPR-applicable EU customers, UK Data Protection Act, various US state privacy laws), PayBridges carries contractual data protection obligations that a certified ISMS demonstrates conformance to.
4. **Investor and board expectations.** Following a Series B raise, the board requested a formal security governance program as part of the company's risk oversight function.

## Engagement Scope

This engagement, led by the Technology Risk Advisory function, covers:

- Design and documentation of the ISMS governance framework (Clause 4–10 requirements)
- ISO/IEC 27005-aligned risk assessment across the cloud-native technology stack
- Statement of Applicability across all 93 Annex A controls, cross-mapped to SOC 2 Trust Services Criteria
- Independent testing of control design (Test of Design) and operating effectiveness (Test of Operating Effectiveness) for a representative control sample
- Documented findings and a Corrective Action / Preventive Action (CAPA) plan for identified deficiencies

## Out of Scope

- Physical security assessment of employee home offices (remote-first workforce; addressed via policy, not on-site testing)
- Penetration testing / red-team exercises (covered under a separate technical security engagement)
- Legal review of customer contracts and DPAs (referred to PayBridges' external counsel)

## Key Stakeholders

| Role | Function |
|---|---|
| CISO (Executive Sponsor) | Accountable for ISMS, chairs the Information Security Steering Committee |
| VP Engineering | Owns AWS infrastructure, CI/CD pipeline, and technical control implementation |
| Head of People | Owns HR-lifecycle controls (onboarding, offboarding, screening) |
| Head of Legal & Compliance | Owns supplier contracts, regulatory mapping, DPAs |
| Lead Technology Risk Advisory Consultant | Independent assessor — risk assessment, SoA, audit workpapers, CAPA |

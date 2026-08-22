# ISMS Boundary & Scope Statement

## Scope Statement (Clause 4.3)

The Information Security Management System (ISMS) of PayBridges covers the people, processes, and technology involved in the design, development, delivery, and support of the PayBridges cloud-native payroll and HR SaaS platform, including all associated customer data processing activities.

> **Formal scope statement:** "The ISMS covers the design, development, hosting, and operation of the PayBridges SaaS platform on Amazon Web Services, including the software development lifecycle, cloud infrastructure, identity and access management, and the corporate systems used to support these functions, in delivery of payroll and HR services to PayBridges' customers."

## In-Scope Boundaries

### Organizational Boundary
- All PayBridges employees and contractors with access to production systems, source code, or customer data
- Engineering, DevOps/SRE, Product, Customer Support (tiers with data access), People/HR, Legal & Compliance, Executive Leadership

### Technical Boundary

| Layer | In-Scope Components |
|---|---|
| Cloud Infrastructure | AWS account(s) hosting production and staging: ECS (containers), RDS (PostgreSQL), S3 (object storage), KMS (key management), VPC networking |
| Identity & Access | Okta (workforce SSO/IdP), AWS IAM, GitHub org-level access controls |
| CI/CD & SDLC | GitHub Enterprise (source control, PR/code review, Actions pipelines), artifact registry |
| Application | PayBridges microservices platform (payroll engine, HRIS module, employee self-service portal, customer admin console) |
| Data | Employee PII, banking/direct-deposit data, compensation and tax records, authentication credentials |
| Corporate IT | Employee endpoints (laptops), corporate SaaS (Google Workspace, Slack, Jira) to the extent they touch customer data or ISMS records |

### Physical Boundary

PayBridges is a remote-first organization with a single leased office (Islamabad hub, non-customer-data-bearing). No company-owned data centers exist; all production infrastructure is hosted in AWS facilities under the AWS shared responsibility model (see `AWS_Shared_Responsibility_Matrix.md`).

## Out-of-Scope

- AWS's physical data center security and hardware lifecycle (AWS's responsibility as CSP; addressed via AWS's own ISO 27001/SOC 2 attestations, referenced but not independently tested)
- Customer-side systems and customer employee endpoints
- Sub-processors' internal ISMS (addressed via vendor due diligence under `Access_Control_Policy` and supplier controls in the SoA, not directly audited)
- Marketing website and non-production demo environments containing only synthetic data

## Interfaces and Dependencies

| Interface | Description | Risk Treatment Owner |
|---|---|---|
| AWS (IaaS/PaaS) | Compute, storage, networking, KMS | VP Engineering, per AWS Shared Responsibility Matrix |
| Okta | Workforce identity provider, SSO, MFA enforcement | Head of IT/Security |
| GitHub Enterprise | Source code, CI/CD, secrets in Actions | VP Engineering |
| Payroll banking rails (ACH/SEPA partners) | Third-party payment processors | Head of Legal & Compliance (contractual), VP Engineering (technical integration) |
| Sub-processors (email delivery, error monitoring, analytics) | Data processors under DPAs | Head of Legal & Compliance |

## Justification for Scope Boundaries

The scope is drawn around every system that stores, processes, or transmits PayBridges customer data, consistent with ISO/IEC 27001:2022 Clause 4.3's requirement to consider external/internal issues (Clause 4.1), interested party requirements (Clause 4.2), and interfaces/dependencies. Corporate-only systems with no data-bearing role (e.g., internal wiki, expense software) are excluded from ISMS certification scope but remain subject to the Acceptable Use and Information Classification policies as a baseline hygiene control.

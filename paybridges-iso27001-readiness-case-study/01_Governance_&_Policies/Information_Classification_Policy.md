# Information Classification Policy

**Document Owner:** CISO
**Approved By:** Information Security Steering Committee
**Classification:** Internal
**ISO/IEC 27001:2022 Reference:** Controls A.5.12, A.5.13, A.5.9, A.5.10, A.5.11, A.5.14
**Review Cycle:** Annual

## 1. Purpose

Establishes a consistent classification scheme so that information assets receive a level of protection proportionate to their sensitivity and the business impact of their loss, disclosure, or alteration.

## 2. Classification Levels

| Level | Definition | Examples at PayBridges |
|---|---|---|
| **Public** | Approved for unrestricted external release | Marketing site content, published blog posts, job postings |
| **Internal** | Not for external release, low sensitivity if disclosed | Internal wikis, non-sensitive Slack channels, general process docs |
| **Confidential** | Disclosure would cause material harm to PayBridges or customers | Source code, customer contracts, architecture diagrams, internal financials |
| **Restricted** | Highest sensitivity — regulatory, contractual, or severe harm if disclosed | Employee/customer-employee PII, banking and direct-deposit data, tax records, authentication credentials, encryption keys |

## 3. Labelling Requirements (Control A.5.13)

1. Restricted and Confidential data must be labelled at the point of creation or ingestion — in document metadata for files, in schema/column comments for databases, and in S3 bucket tags for object storage.
2. Automated data classification tagging (AWS Macie for S3, custom tagging for RDS) is used to detect and flag PII/Restricted data that lacks a label.

## 4. Handling Requirements by Classification

| Requirement | Public | Internal | Confidential | Restricted |
|---|---|---|---|---|
| Encryption at rest | Not required | Recommended | Required (AES-256, AWS KMS) | Required (AES-256, AWS KMS, customer-managed keys where contractually required) |
| Encryption in transit | Not required | TLS 1.2+ | TLS 1.2+ | TLS 1.2+, mutual TLS for service-to-service where feasible |
| Access | Anyone | All employees | Named roles / need-to-know | Named roles, explicit approval, logged access |
| Storage location | Any | Corporate SaaS | Approved corporate/production systems only | Production AWS environment only; no local copies, no third-party SaaS uploads without DPA |
| Retention | Per marketing policy | 3 years default | Per data type / contract | Per statutory requirement (tax: 7 years; PII: contract-defined, deleted at contract termination + grace period) |

## 5. Information Transfer (Control A.5.14)

1. Restricted data may only be transmitted through approved, encrypted channels (application APIs over TLS, SFTP for banking file transfers with PGP encryption at the file level).
2. Restricted data must never be sent via unencrypted email, personal messaging apps, or unapproved file-sharing tools.
3. Cross-border transfers of Restricted data (e.g., EU employee data processed in US-region AWS infrastructure) require a documented transfer mechanism (Standard Contractual Clauses) tracked by Legal & Compliance.

## 6. Asset Inventory and Ownership (Control A.5.9, A.5.10, A.5.11)

1. Every information asset (database, S3 bucket, repository) has a designated business owner recorded in the asset register (see `Asset_Management_Policy.md`).
2. Acceptable Use rules for Confidential/Restricted assets are documented in the onboarding security training and acknowledged annually by all staff.
3. Upon termination or role change, all Restricted/Confidential assets and access must be returned or revoked per the Access Control Policy.

## 7. Revision History

| Version | Date | Change | Author |
|---|---|---|---|
| 1.0 | 2025-02-01 | Initial issuance | CISO |

# Asset Management Policy

**Document Owner:** VP Engineering
**Approved By:** CISO
**Classification:** Internal
**ISO/IEC 27001:2022 Reference:** Controls A.5.9, A.5.10, A.5.11, A.7.9, A.7.14, A.8.1
**Review Cycle:** Annual

## 1. Purpose

Ensures PayBridges maintains an accurate, current inventory of information assets — cloud infrastructure, source code repositories, and endpoint devices — each with a designated owner accountable for its security.

## 2. Scope

Covers all AWS cloud resources, GitHub repositories, SaaS applications processing PayBridges or customer data, and employee endpoint devices within ISMS scope.

## 3. Asset Inventory (Control A.5.9)

1. Cloud infrastructure assets (VPCs, RDS instances, S3 buckets, ECS clusters, KMS keys) are inventoried automatically via AWS Config and tagged with: `owner`, `environment`, `data-classification`, `cost-center`.
2. Untagged resources are flagged by a scheduled AWS Config rule and remediated within 5 business days; resources that cannot be attributed to an owner within 30 days are escalated for decommissioning review.
3. Source code repositories are inventoried in the GitHub organization with each repo assigned a designated owning team and a `CODEOWNERS` file.
4. The asset inventory is reconciled quarterly by the VP Engineering function and reviewed by the CISO.

## 4. Asset Ownership (Control A.5.9)

Every in-scope asset has a named or role-based owner accountable for:
- Confirming the asset's data classification
- Approving access requests to the asset
- Ensuring the asset is included in vulnerability scanning and patching cadence
- Decommissioning the asset securely when no longer needed

## 5. Acceptable Use (Control A.5.10)

1. Company-issued endpoints (laptops) are the only devices authorized to access production systems; personal device access ("BYOD") to production AWS or GitHub is prohibited.
2. Endpoints are enrolled in MDM (mobile device management) with enforced full-disk encryption, screen-lock timeout, and remote-wipe capability.
3. Removable media (USB storage) is disabled by default on managed endpoints; exceptions require CISO approval.

## 6. Asset Return (Control A.5.11)

1. Upon termination, all company-issued equipment must be returned within 5 business days (or immediately for involuntary terminations), tracked via the offboarding checklist in Jira (see `Technical_Evidence_Samples/offboarding-jira-evidence.pdf`).
2. IT confirms device wipe and re-provisioning status before an asset is returned to inventory or disposed of.

## 7. Secure Disposal (Control A.7.14)

1. Decommissioned cloud storage (EBS volumes, RDS snapshots) is deleted through AWS-native secure deletion; because all Restricted data is encrypted at rest via KMS, deletion of the encryption key material is treated as an acceptable cryptographic erasure method for decommissioned encrypted volumes.
2. Physical endpoint disposal is handled through a certified e-waste/data destruction vendor, with destruction certificates retained as evidence.

## 8. Assets Off-Premises (Control A.7.9)

Remote-first workforce means the default working posture is off-premises. Endpoint protection (MDM enrollment, disk encryption, EDR agent) is required regardless of location; no differentiated "office-only" control set exists.

## 9. Revision History

| Version | Date | Change | Author |
|---|---|---|---|
| 1.0 | 2025-02-15 | Initial issuance | VP Engineering |

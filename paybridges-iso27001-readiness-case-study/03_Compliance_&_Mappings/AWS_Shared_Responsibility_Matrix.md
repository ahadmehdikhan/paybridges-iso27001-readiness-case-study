# AWS Shared Responsibility Matrix

**Document Owner:** VP Engineering
**Purpose:** Delineates which Annex A controls are owned by PayBridges ("Security *in* the Cloud") versus inherited from AWS ("Security *of* the Cloud"), per the AWS Shared Responsibility Model. This matrix directly informs the "Not Applicable" and "N/A - AWS Responsibility" determinations in the Statement of Applicability.

## 1. Model Overview

| Layer | Responsibility |
|---|---|
| Physical data centers, hardware, host OS virtualization, network infrastructure, environmental controls | **AWS** |
| Guest OS configuration, identity and access management, network/firewall configuration, application-layer security, data encryption (client-side and server-side), customer data classification | **PayBridges** |

AWS's own conformance to ISO/IEC 27001, SOC 2, and other frameworks for the infrastructure layer is evidenced via AWS's publicly available certifications and AWS Artifact reports, referenced as third-party assurance rather than independently re-tested by this engagement.

## 2. Service-by-Service Breakdown

| AWS Service | AWS Responsibility | PayBridges Responsibility |
|---|---|---|
| **RDS (PostgreSQL)** | Underlying host patching, storage-layer durability, physical security of underlying hardware | Database access control (IAM auth), encryption-at-rest key management (KMS), backup retention configuration, network access rules (security groups), query-layer authorization |
| **S3** | Storage durability/availability, physical media, hardware-level encryption support | Bucket policies, public-access-block configuration, object-level encryption (KMS), lifecycle/retention policy, access logging |
| **ECS (containers)** | Underlying EC2/Fargate host security, container runtime patching (Fargate) | Container image content and vulnerability management, task IAM roles, network segmentation (VPC/security groups), secrets management |
| **KMS** | HSM-backed key storage infrastructure, physical key material protection | Key policy configuration, key rotation cadence, access grants to keys, CMK vs. AWS-managed key decisions |
| **VPC / Networking** | Physical network infrastructure, hypervisor-level network isolation | Subnet design, security group/NACL rules, VPC peering and endpoint configuration, network segmentation between environments |
| **IAM** | Underlying service availability and integrity | Policy design (least privilege), MFA enforcement, role trust relationships, credential rotation |
| **CloudTrail / CloudWatch** | Log delivery infrastructure availability | Log retention configuration, alerting rules, log integrity validation, SIEM integration |

## 3. Mapping to Statement of Applicability "N/A - AWS Responsibility" Determinations

The following Annex A controls are marked **N/A - AWS Responsibility** in the SoA because PayBridges operates no physical infrastructure and these controls are fully inherited from AWS's own ISO 27001/SOC 2 certified environment:

| Control | Rationale |
|---|---|
| A.7.5 – Protecting against physical and environmental threats | AWS data center fire suppression, climate control, flood protection |
| A.7.8 – Equipment siting and protection | No PayBridges-owned server hardware exists |
| A.7.11 – Supporting utilities | AWS-managed power/cooling redundancy |
| A.7.12 – Cabling security | AWS-managed data center cabling |

PayBridges retains responsibility for reviewing AWS's own third-party attestations (SOC 2 Type II, ISO 27001 certificate) annually via AWS Artifact and recording the review in the supplier monitoring log (Control A.5.22), since reliance on a sub-processor's control environment does not remove PayBridges' accountability for the outcome.

## 4. Residual Risk Note

Even where a control is inherited, PayBridges retains responsibility for *configuring* AWS services securely (e.g., a correctly encrypted KMS key protects data regardless of AWS's physical security, but a misconfigured S3 bucket policy — a PayBridges responsibility — can expose that same data publicly, as modeled in risk scenario RR-02). The shared responsibility model reduces PayBridges' physical/infrastructure control burden; it does not reduce its configuration or access-control burden.

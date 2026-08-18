# PayBridges ISO 27001:2022 Readiness & Audit Case Study

### Client Context: PayBridges SaaS (Fictional Cloud-Native Global HR & Payroll Platform)

> **Role:** Lead Technology Risk Advisory Consultant (Tech Advisory)  
> **Target Frameworks:** ISO/IEC 27001:2022, ISO/IEC 27005, SOC 2 Type II (Trust Services Criteria)  
> **Environment:** 100% Cloud-Native (AWS / GitHub / Okta / Microservices)  
> **License:** MIT License  

---

## Executive Summary

This repository contains an audit-grade **ISMS Implementation & Security Readiness Case Study** for **PayBridges**, a fast-growing B2B SaaS platform handling sensitive enterprise employee PII, banking records, and payroll data. 

As the Lead Technology Risk Advisory Consultant, I executed an end-to-end ISO 27001:2022 readiness assessment, designed control governance policies, conducted technical risk scoring, constructed Big 4-style audit workpapers, and developed remediation plans (CAPA) for control deficiencies.

---

## Target Organization Profile: PayBridges SaaS

* **Industry:** Cloud-Native Fintech / HR Technology
* **Core Product:** Automated global payroll processing and employee records management (HR Platform)
* **Headcount:** ~120 Employees (55% Engineering & DevOps)
* **Infrastructure:** 100% AWS (Amazon RDS, S3, ECS Containers, AWS KMS), Okta SSO, Enterprise GitHub CI/CD pipelines
* **Compliance Drivers:** Enterprise customer security questionnaires, SOC 2 Type II alignment, and ISO/IEC 27001:2022 certification readiness

---

## Repository Directory Structure

```text
paybridges-iso27001-readiness-case-study/
│
├── README.md                              # Main Repo Documentation & Executive Overview
├── LICENSE                                # MIT License
│
├── docs/                                  # Executive Context & Framework Scope
│   ├── 00_Executive_Summary_&_Context.md   # Business drivers and background
│   └── 01_ISMS_Boundary_&_Scope.md        # ISMS scope definition & cloud boundaries
│
├── 01_Governance_&_Policies/              # Formal Governance Policy Suite
│   ├── Information_Security_Policy.md     # Top-level ISMS policy (Clause 5.2)
│   ├── Access_Control_Policy.md           # RBAC, MFA, JIT, & Okta guidelines
│   ├── Information_Classification_Policy.md# Public, Internal, Confidential, Restricted
│   ├── Change_Management_Policy.md        # GitHub PR peer-review & CI/CD pipeline controls
│   └── Asset_Management_Policy.md         # AWS cloud asset inventory & owner assignment
│
├── 02_Risk_Management/                    # ISO 27005 Risk Assessment Framework
│   ├── Risk_Assessment_Methodology.md     # Qualitative/Quantitative 5x5 scoring matrix
│   └── PayBridges_ISO27005_Risk_Register.xlsx # 15+ SaaS threat scenarios & mitigations
│
├── 03_Compliance_&_Mappings/              # Framework Control Alignment
│   ├── Statement_of_Applicability_SoA.xlsx# ISO 27001:2022 (93 Controls) + SOC 2 Mapping
│   └── AWS_Shared_Responsibility_Matrix.md# Cloud provider vs. tenant risk boundaries
│
├── 04_Audit_Workpapers/                   # Big 4 Audit Workpaper Package
│   ├── ToD_Test_of_Design_Workpaper.xlsx  # Control design adequacy testing
│   ├── ToE_Test_of_Operating_Effectiveness.xlsx# Control execution & sampling logs
│   └── Technical_Evidence_Samples/        # Redacted execution artifacts
│       ├── github-pr-approval-logs.json   # Enforced code review approvals
│       ├── aws-iam-least-privilege.json   # IAM policy config samples
│       └── offboarding-jira-evidence.pdf  # Offboarding ticket timestamp evidence
│
└── 05_Remediation_&_CAPA/                 # Audit Findings & Corrective Action
    └── Control_Deficiency_Log_and_CAPA.xlsx# Simulated audit findings & remediation plans

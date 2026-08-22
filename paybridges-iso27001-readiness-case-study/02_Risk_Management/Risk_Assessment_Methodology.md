# Risk Assessment Methodology

**Document Owner:** CISO
**Framework Reference:** ISO/IEC 27005:2022, ISO/IEC 27001:2022 Clause 6.1.2, 8.2
**Review Cycle:** Annual, or upon material change to risk appetite

## 1. Purpose

Defines a consistent, repeatable methodology for identifying, analyzing, evaluating, and treating information security risks across the PayBridges ISMS scope, producing outputs that satisfy ISO/IEC 27001:2022 Clause 6.1.2 (information security risk assessment) and feed the Statement of Applicability.

## 2. Risk Assessment Process

1. **Asset & Context Identification** — draw threat scenarios against the asset inventory (Asset Management Policy) and ISMS scope boundary.
2. **Threat & Vulnerability Identification** — identify realistic threat sources (external attacker, malicious insider, negligent insider, third-party/supplier failure, environmental) and the vulnerabilities that would allow them to materialize.
3. **Risk Analysis** — score each scenario using the 5x5 Likelihood x Impact matrix below.
4. **Risk Evaluation** — compare the resulting risk rating against PayBridges' risk appetite to determine whether treatment is required.
5. **Risk Treatment** — select a treatment option (Mitigate, Transfer, Avoid, Accept) and, for Mitigate, identify the Annex A control(s) that provide treatment.
6. **Residual Risk Review** — re-score likelihood/impact assuming the treatment/control is operating effectively; residual risk above appetite requires Steering Committee risk acceptance.

## 3. Likelihood Scale (1–5)

| Score | Rating | Definition |
|---|---|---|
| 1 | Rare | Would only occur in exceptional circumstances; no known precedent in the industry |
| 2 | Unlikely | Could occur but not expected; isolated industry precedent |
| 3 | Possible | Might occur at some point; occurs periodically in similar organizations |
| 4 | Likely | Will probably occur; has occurred at PayBridges or close peers before |
| 5 | Almost Certain | Expected to occur, possibly multiple times per year, absent treatment |

## 4. Impact Scale (1–5)

Impact is assessed across confidentiality, integrity, and availability, with the highest applicable score used.

| Score | Rating | Definition (illustrative) |
|---|---|---|
| 1 | Negligible | No customer data exposure; no service disruption; internal-only nuisance |
| 2 | Minor | Limited internal data exposure; brief (<1hr) degraded service; no regulatory trigger |
| 3 | Moderate | Confidential data exposure (non-PII); service disruption 1–4 hrs; internal incident response engaged |
| 4 | Major | Restricted data (PII/banking) exposure for a subset of customers; disruption >4 hrs; breach notification likely required |
| 5 | Severe | Large-scale Restricted data breach; extended platform outage affecting payroll processing/payment (missed pay run); regulatory action, material customer churn, or reportable breach across multiple jurisdictions |

## 5. Risk Matrix and Rating Bands

| Likelihood \ Impact | 1 | 2 | 3 | 4 | 5 |
|---|---|---|---|---|---|
| **5** | 5 (Med) | 10 (Med) | 15 (High) | 20 (Crit) | 25 (Crit) |
| **4** | 4 (Low) | 8 (Med) | 12 (High) | 16 (Crit) | 20 (Crit) |
| **3** | 3 (Low) | 6 (Med) | 9 (High) | 12 (High) | 15 (High) |
| **2** | 2 (Low) | 4 (Low) | 6 (Med) | 8 (Med) | 10 (Med) |
| **1** | 1 (Low) | 2 (Low) | 3 (Low) | 4 (Low) | 5 (Med) |

| Band | Score Range | Response |
|---|---|---|
| Critical | 16–25 | Immediate treatment required; escalate to Steering Committee; target remediation < 30 days |
| High | 9–15 | Treatment required within current quarter; owner assigned; tracked to closure |
| Medium | 5–8 | Treatment planned within the year, or formally accepted with compensating control |
| Low | 1–4 | Monitor; treat opportunistically |

## 6. Risk Appetite Statement

PayBridges' Steering Committee has set risk appetite such that no Critical-rated risk may be accepted without documented Board-level sign-off, and no High-rated risk touching Restricted data (PII/banking) may remain untreated beyond one fiscal quarter without a compensating control and CISO risk acceptance.

## 7. Risk Register Maintenance

- The risk register (`PayBridges_ISO27005_Risk_Register.xlsx`) is reviewed quarterly by the Steering Committee and updated upon: new asset onboarding, architecture changes, incident post-mortems, and external threat intelligence indicating a materially changed likelihood.
- Each risk entry references the Annex A control(s) providing treatment, which ties directly to the Statement of Applicability's implementation status column — a risk cannot be marked "treated" unless its corresponding SoA control is marked "Implemented," creating traceability between the risk register and the control set tested in the audit workpapers.

## 8. Roles

| Role | Responsibility |
|---|---|
| Risk Owner (per risk) | Accountable for treatment implementation and residual risk monitoring |
| CISO | Approves risk ratings, chairs quarterly risk review |
| Steering Committee | Approves risk acceptance for High/Critical risks |
| Technology Risk Advisory (this engagement) | Independent challenge of risk ratings, control effectiveness testing |

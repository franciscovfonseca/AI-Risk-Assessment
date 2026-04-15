# AI Risk Assessment — NorthPoint Financial Services
**Document Type:** Risk Register  
**Classification:** Internal — Restricted  
**Systems Covered:** NP-001 Credit Scoring Engine · NP-002 Fraud Detection System  
**Framework:** ISO 31000 · NIST AI RMF (Map & Measure) · EU AI Act Article 9  
**Prepared by:** AI Governance Office  
**Status:** ✅ Complete — Approved for Board Review

---

## Methodology

This risk assessment follows ISO 31000:2018 risk management guidelines and the NIST AI RMF Map and Measure functions. Risk scenarios were identified through:
- Review of known AI failure modes in financial services
- EU AI Act Annex III obligations and recitals
- NIST AI RMF risk taxonomy
- Operational data and system documentation review

**Risk scoring matrix:**

| | Low Impact | Medium Impact | High Impact | Critical Impact |
|---|---|---|---|---|
| **High Likelihood** | 🟡 Medium | 🟠 High | 🔴 High | 🔴 Critical |
| **Medium Likelihood** | 🟢 Low | 🟡 Medium | 🟠 High | 🔴 High |
| **Low Likelihood** | 🟢 Low | 🟢 Low | 🟡 Medium | 🟡 Medium |

**Likelihood scale:** High = likely to occur within 12 months · Medium = possible within 2 years · Low = unlikely but plausible  
**Impact scale:** Critical = regulatory sanction / significant customer harm · High = material business or reputational impact · Medium = operational disruption · Low = minor internal impact

---

## Part 1 — NP-001: Credit Scoring Engine

**System description:** Automated ML model assessing creditworthiness and determining loan eligibility for NorthPoint retail and SME customers. Outputs a credit score and a binary eligibility decision (approve/decline) with no mandatory human review for standard applications.

**Risk classification:** 🔴 HIGH RISK — EU AI Act Annex III §5(b)

---

### Risk Register — NP-001

---

#### RISK-NP001-01: Demographic Bias in Credit Decisions

| Field | Detail |
|---|---|
| **Risk ID** | RISK-NP001-01 |
| **Category** | Fairness & Discrimination |
| **Description** | The model may produce systematically different approval rates or credit score outputs for applicants from certain demographic groups, resulting in discriminatory outcomes that violate EU AI Act Article 10 and non-discrimination law. |
| **Root Cause** | Training data reflects historical lending decisions made under conditions of structural inequality. Proxy variables (postcode, employment type) may correlate with protected characteristics. |
| **Likelihood** | High |
| **Impact** | Critical |
| **Inherent Risk** | 🔴 Critical |
| **Affected Stakeholders** | Retail and SME loan applicants; NorthPoint compliance and legal teams; regulators |
| **Regulatory Reference** | EU AI Act Articles 9, 10; UK Equality Act 2010; EU Non-Discrimination Directives |

**Mitigation measures:**
1. Commission independent disparate impact audit across protected characteristic groups (race, gender, age, disability)
2. Identify and remove or transform proxy variables correlated with protected characteristics
3. Implement fairness-aware model training with demographic parity and equalised odds constraints
4. Establish monthly automated bias monitoring with threshold alerts to the AI Governance Office
5. Document all bias findings and mitigations in the technical file per Article 11

| **Residual Risk** | 🟡 Medium — bias risk cannot be fully eliminated; ongoing monitoring is the primary control |
|---|---|
| **Owner** | Head of Credit Risk |
| **Review Frequency** | Monthly monitoring; quarterly formal review |
| **Target Completion** | Q2 2025 |

---

#### RISK-NP001-02: Lack of Explainability for Credit Refusals

| Field | Detail |
|---|---|
| **Risk ID** | RISK-NP001-02 |
| **Category** | Transparency & Explainability |
| **Description** | Applicants refused credit receive no meaningful explanation of the factors that drove the decision. This violates EU AI Act Article 13 (transparency) and the right to explanation under GDPR Article 22. |
| **Root Cause** | The current model architecture (gradient boosted ensemble) does not natively produce feature-level explanations accessible to non-technical staff or customers. |
| **Likelihood** | High |
| **Impact** | High |
| **Inherent Risk** | 🔴 High |
| **Affected Stakeholders** | Declined loan applicants; customer service teams; compliance |
| **Regulatory Reference** | EU AI Act Article 13; GDPR Article 22; FCA Consumer Duty |

**Mitigation measures:**
1. Implement SHAP (SHapley Additive exPlanations) or LIME post-hoc explainability layer on model outputs
2. Develop customer-facing refusal letter template with top 3 contributing factors expressed in plain language
3. Train customer-facing staff on how to communicate credit decision explanations
4. Establish internal appeals process with human review for contested decisions

| **Residual Risk** | 🟢 Low — explainability layer addresses core obligation; human appeals pathway provides backstop |
|---|---|
| **Owner** | Head of Credit Risk |
| **Review Frequency** | Quarterly |
| **Target Completion** | Q2 2025 |

---

#### RISK-NP001-03: Training Data Reflecting Historical Discrimination

| Field | Detail |
|---|---|
| **Risk ID** | RISK-NP001-03 |
| **Category** | Data Governance |
| **Description** | Historical lending data used to train NP-001 may encode past discriminatory practices — e.g., redlining, gender-based lending restrictions — perpetuating and automating historical inequities at scale. |
| **Root Cause** | Training data spans 15+ years of lending decisions made under regulatory frameworks that have since changed. Discrimination that was legal or undetected in prior periods is now embedded in model weights. |
| **Likelihood** | Medium |
| **Impact** | Critical |
| **Inherent Risk** | 🔴 High |
| **Affected Stakeholders** | All loan applicants; NorthPoint risk and legal; regulators |
| **Regulatory Reference** | EU AI Act Article 10(2) — training data free of discriminatory effects; Article 10(5) — use of special category data for bias monitoring |

**Mitigation measures:**
1. Conduct full data lineage audit of training dataset — identify data from pre-2010 periods for review
2. Re-weight or re-sample training data to reduce influence of historically biased samples
3. Apply Article 10(5) exemption to use sensitive demographic data for bias detection and correction only
4. Document data governance decisions in technical file with legal basis for any sensitive data processing

| **Residual Risk** | 🟡 Medium — legacy data issues cannot be fully corrected retrospectively; ongoing data refresh programme is primary long-term control |
|---|---|
| **Owner** | Head of Data Governance |
| **Review Frequency** | Annually (data audit); monthly (outcome monitoring) |
| **Target Completion** | Q3 2025 |

---

#### RISK-NP001-04: Model Drift Reducing Accuracy Over Time

| Field | Detail |
|---|---|
| **Risk ID** | RISK-NP001-04 |
| **Category** | Performance & Robustness |
| **Description** | The model's predictive accuracy degrades as economic conditions, customer behaviour, and lending markets evolve — resulting in increasing rates of incorrect approvals (credit losses) or incorrect refusals (missed business and customer harm). |
| **Root Cause** | ML models trained on historical data do not automatically adapt to distribution shift in input features or label relationships. |
| **Likelihood** | Medium |
| **Impact** | High |
| **Inherent Risk** | 🟠 High |
| **Affected Stakeholders** | NorthPoint credit risk team; loan applicants; NorthPoint P&L |
| **Regulatory Reference** | EU AI Act Article 9(7) — post-market monitoring; Article 15 — accuracy and robustness |

**Mitigation measures:**
1. Implement automated model performance monitoring with monthly accuracy, precision and recall reporting
2. Define drift thresholds that trigger mandatory model review — PSI (Population Stability Index) > 0.2
3. Establish 6-monthly model retraining schedule with full re-validation before deployment
4. Maintain challenger model in shadow mode for performance comparison

| **Residual Risk** | 🟢 Low — monitoring and retraining schedule directly addresses drift risk |
|---|---|
| **Owner** | Head of Credit Risk |
| **Review Frequency** | Monthly monitoring; 6-monthly formal review |
| **Target Completion** | Q1 2025 (monitoring); Q3 2025 (first scheduled retrain) |

---

#### RISK-NP001-05: Data Quality Failures in Input Pipeline

| Field | Detail |
|---|---|
| **Risk ID** | RISK-NP001-05 |
| **Category** | Data Governance |
| **Description** | Missing, incorrect, or stale data in the applicant input pipeline produces inaccurate credit scores — resulting in incorrect decisions for individual applicants. |
| **Likelihood** | Low |
| **Impact** | High |
| **Inherent Risk** | 🟡 Medium |
| **Affected Stakeholders** | Individual loan applicants; credit operations team |
| **Regulatory Reference** | EU AI Act Article 10 — data quality requirements |

**Mitigation measures:**
1. Input validation checks at pipeline ingestion (completeness, format, range validation)
2. Automated alerts for missing critical fields — decision suppressed until data quality confirmed
3. Quarterly data quality audit with findings reported to AI Governance Office

| **Residual Risk** | 🟢 Low |
|---|---|
| **Owner** | Head of Data Engineering |
| **Review Frequency** | Quarterly |

---

### NP-001 Risk Summary

| Risk ID | Scenario | Inherent Risk | Residual Risk | Owner |
|---|---|---|---|---|
| RISK-NP001-01 | Demographic bias in credit decisions | 🔴 Critical | 🟡 Medium | Head of Credit Risk |
| RISK-NP001-02 | Lack of explainability for refusals | 🔴 High | 🟢 Low | Head of Credit Risk |
| RISK-NP001-03 | Training data reflecting historical discrimination | 🔴 High | 🟡 Medium | Head of Data Governance |
| RISK-NP001-04 | Model drift reducing accuracy | 🟠 High | 🟢 Low | Head of Credit Risk |
| RISK-NP001-05 | Data quality failures in input pipeline | 🟡 Medium | 🟢 Low | Head of Data Engineering |

---

## Part 2 — NP-002: Fraud Detection System

**System description:** Real-time ML model detecting fraudulent transactions and placing automatic holds on customer accounts or card transactions flagged as suspicious. Decisions are made in milliseconds with no human review at point of decision.

**Risk classification:** 🔴 HIGH RISK — EU AI Act Annex III §5(b)

---

### Risk Register — NP-002

---

#### RISK-NP002-01: High False Positive Rate — Legitimate Transactions Blocked

| Field | Detail |
|---|---|
| **Risk ID** | RISK-NP002-01 |
| **Category** | Performance & Customer Harm |
| **Description** | The model incorrectly flags legitimate transactions as fraudulent, causing customer accounts or cards to be blocked during genuine purchases. This causes direct customer harm, erodes trust, and creates operational burden. |
| **Root Cause** | Precision-recall trade-off: models tuned for high fraud recall inevitably produce false positives. Without regular recalibration, false positive rates creep upward as transaction patterns evolve. |
| **Likelihood** | High |
| **Impact** | High |
| **Inherent Risk** | 🔴 High |
| **Affected Stakeholders** | NorthPoint customers; customer service teams; NorthPoint reputation |
| **Regulatory Reference** | EU AI Act Article 9; FCA Consumer Duty — avoid foreseeable harm |

**Mitigation measures:**
1. Establish false positive rate SLA: target < 0.5% of legitimate transactions incorrectly blocked
2. Implement tiered response — low-confidence flags trigger customer verification (SMS/app) before block
3. Monthly false positive rate monitoring with automated escalation if SLA breached
4. Customer dispute resolution pathway with 24-hour resolution target for incorrect blocks
5. Quarterly model recalibration to maintain precision-recall balance

| **Residual Risk** | 🟡 Medium — some false positives are unavoidable; tiered response and monitoring limit customer harm |
|---|---|
| **Owner** | Head of Financial Crime |
| **Review Frequency** | Monthly |
| **Target Completion** | Q2 2025 |

---

#### RISK-NP002-02: Disproportionate Impact on Specific Customer Segments

| Field | Detail |
|---|---|
| **Risk ID** | RISK-NP002-02 |
| **Category** | Fairness & Discrimination |
| **Description** | The fraud model may generate disproportionately higher false positive rates for specific customer segments — e.g., customers who travel frequently, use international merchants, or have non-standard spending patterns typical of minority communities. This constitutes differential treatment. |
| **Likelihood** | Medium |
| **Impact** | High |
| **Inherent Risk** | 🔴 High |
| **Affected Stakeholders** | Affected customer segments; NorthPoint legal and compliance |
| **Regulatory Reference** | EU AI Act Article 10; UK Equality Act; FCA Consumer Duty |

**Mitigation measures:**
1. Segment-level false positive rate analysis — identify customer groups experiencing >2x average false positive rate
2. Apply fairness constraints during model training and recalibration
3. Establish customer feedback channel for customers to flag repeated incorrect blocks
4. Annual third-party fairness audit

| **Residual Risk** | 🟡 Medium |
|---|---|
| **Owner** | Head of Financial Crime |
| **Review Frequency** | Quarterly |
| **Target Completion** | Q3 2025 |

---

#### RISK-NP002-03: System Unavailability During High-Volume Periods

| Field | Detail |
|---|---|
| **Risk ID** | RISK-NP002-03 |
| **Category** | Operational Resilience |
| **Description** | The fraud detection system becomes unavailable or severely degraded during peak transaction periods (Black Friday, month-end, holiday travel), forcing a choice between processing transactions without fraud screening or stopping all transactions. |
| **Likelihood** | Medium |
| **Impact** | Critical |
| **Inherent Risk** | 🔴 High |
| **Affected Stakeholders** | NorthPoint customers; NorthPoint operations and financial crime teams |
| **Regulatory Reference** | EU AI Act Article 15 — robustness requirements; FCA operational resilience rules |

**Mitigation measures:**
1. Define and test system capacity at 3x peak transaction volume
2. Implement graceful degradation mode — rule-based fallback screening if ML model unavailable
3. Annual business continuity test for fraud detection system outage scenario
4. Cloud auto-scaling configured to pre-empt known high-volume periods

| **Residual Risk** | 🟡 Medium — residual risk from unforeseeable spikes; fallback mode provides adequate baseline protection |
|---|---|
| **Owner** | Head of Technology Operations |
| **Review Frequency** | Annually (BCP test); monthly (capacity monitoring) |
| **Target Completion** | Q2 2025 |

---

#### RISK-NP002-04: Model Drift as Fraud Patterns Evolve

| Field | Detail |
|---|---|
| **Risk ID** | RISK-NP002-04 |
| **Category** | Performance & Robustness |
| **Description** | Fraud techniques evolve continuously. A model trained on historical fraud patterns will degrade in detection effectiveness as adversaries adapt — resulting in increasing fraud losses. |
| **Likelihood** | High |
| **Impact** | Medium |
| **Inherent Risk** | 🟡 Medium |
| **Affected Stakeholders** | NorthPoint financial crime team; NorthPoint P&L |
| **Regulatory Reference** | EU AI Act Article 9(7) — continuous risk management; Article 15 |

**Mitigation measures:**
1. Monthly fraud detection rate monitoring — alert if detection rate drops > 5% month-on-month
2. Quarterly model retraining on rolling 90-day fraud data window
3. Threat intelligence feed integration — incorporate emerging fraud typologies into feature engineering

| **Residual Risk** | 🟢 Low |
|---|---|
| **Owner** | Head of Financial Crime |
| **Review Frequency** | Monthly |

---

#### RISK-NP002-05: Insufficient Logging for Dispute Resolution

| Field | Detail |
|---|---|
| **Risk ID** | RISK-NP002-05 |
| **Category** | Transparency & Accountability |
| **Description** | If decision logs are incomplete or not retained, NorthPoint cannot reconstruct why a specific transaction was blocked — making it impossible to resolve customer disputes, respond to regulatory enquiries, or conduct post-incident analysis. |
| **Likelihood** | Low |
| **Impact** | High |
| **Inherent Risk** | 🟡 Medium |
| **Affected Stakeholders** | Customers disputing blocked transactions; compliance and legal; regulators |
| **Regulatory Reference** | EU AI Act Article 12 — record-keeping; GDPR data retention obligations |

**Mitigation measures:**
1. Log all model inputs, output score, decision outcome, and timestamp for every transaction assessed
2. Retain logs for minimum 3 years per EU AI Act Article 12 requirements
3. Implement structured log format accessible to non-technical compliance staff for dispute investigation

| **Residual Risk** | 🟢 Low |
|---|---|
| **Owner** | Head of Technology Operations |
| **Review Frequency** | Annually |

---

### NP-002 Risk Summary

| Risk ID | Scenario | Inherent Risk | Residual Risk | Owner |
|---|---|---|---|---|
| RISK-NP002-01 | High false positive rate | 🔴 High | 🟡 Medium | Head of Financial Crime |
| RISK-NP002-02 | Disproportionate impact on customer segments | 🔴 High | 🟡 Medium | Head of Financial Crime |
| RISK-NP002-03 | System unavailability — high volume periods | 🔴 High | 🟡 Medium | Head of Technology Operations |
| RISK-NP002-04 | Model drift as fraud patterns evolve | 🟡 Medium | 🟢 Low | Head of Financial Crime |
| RISK-NP002-05 | Insufficient logging for dispute resolution | 🟡 Medium | 🟢 Low | Head of Technology Operations |

---

*Document prepared by the AI Governance Office, NorthPoint Financial Services.*  
*Next review: Q2 2025. Approved for distribution to Board Risk Committee.*

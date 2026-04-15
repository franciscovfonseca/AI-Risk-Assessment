# Bias & Fairness Assessment — NP-001 Credit Scoring Engine
**Document Type:** Bias & Fairness Assessment  
**Classification:** Internal — Restricted  
**System:** NP-001 Credit Scoring Engine  
**Framework:** EU AI Act Articles 9, 10 · NIST AI RMF · IEEE 7003 Algorithmic Bias Considerations  
**Prepared by:** AI Governance Office  
**Status:** ✅ Complete — Pending Bias Audit Implementation

---

## Purpose

This document assesses the bias and fairness risks of NorthPoint Financial Services' Credit Scoring Engine (NP-001). As an automated system determining loan eligibility, NP-001 presents the highest fairness risk of any system in NorthPoint's AI portfolio.

Under EU AI Act Article 10, HIGH RISK AI systems must use training data that is sufficiently representative, free of errors, and complete — with specific attention to possible biases that could affect fundamental rights. This assessment identifies where NP-001 may fall short of this requirement and recommends corrective action.

---

## 1. System Context

| Field | Detail |
|---|---|
| **System** | NP-001 Credit Scoring Engine |
| **Decision type** | Binary: Approve / Decline loan application |
| **Automation level** | Fully automated — no mandatory human review for standard applications |
| **Annual decisions** | ~48,000 loan applications per year |
| **Decision consequence** | Access to credit — material impact on financial inclusion and individual welfare |
| **Regulatory classification** | HIGH RISK — EU AI Act Annex III §5(b) |

---

## 2. Fairness Framework

This assessment applies three established fairness criteria. No single criterion is universally correct — the appropriate standard depends on the decision context and the values NorthPoint wishes to uphold.

| Fairness Criterion | Definition | Application to NP-001 |
|---|---|---|
| **Demographic Parity** | Approval rates should be equal across demographic groups | Primary criterion — equal access to credit is a regulatory and ethical baseline |
| **Equalised Odds** | True positive and false positive rates should be equal across groups | Secondary criterion — ensures neither group bears disproportionate burden of incorrect decisions |
| **Individual Fairness** | Similar applicants should receive similar outcomes regardless of group membership | Operational criterion — informs model explainability requirements |

---

## 3. Protected Characteristics Assessment

The following protected characteristics were assessed for bias risk under UK Equality Act 2010 and EU non-discrimination law.

---

### 3.1 Race and Ethnicity

| Assessment Field | Detail |
|---|---|
| **Risk Level** | 🔴 High |
| **Bias Pathway** | Postcode and geographic data used as input features correlate with ethnicity due to historical residential segregation patterns. The model has not been explicitly tested for racial differential impact. |
| **Evidence Base** | Research on credit scoring bias consistently identifies geographic proxies as primary vectors for racial bias (Federal Reserve, 2019; Bank of England, 2021). NorthPoint's use of postcode as an input feature presents equivalent risk. |
| **Potential Impact** | Applicants from minority ethnic backgrounds may face systematically lower approval rates or lower credit scores, independent of their actual creditworthiness. |
| **Current Controls** | None formalised |
| **Required Actions** | 1. Commission disparate impact analysis across ethnic groups using Article 10(5) exemption for sensitive data processing for bias detection purposes 2. Audit postcode and geographic features for proxy correlation with ethnicity 3. Implement fairness-constrained model training if disparate impact confirmed |

---

### 3.2 Gender

| Assessment Field | Detail |
|---|---|
| **Risk Level** | 🟡 Medium |
| **Bias Pathway** | Historical credit data reflects a period when women had lower average incomes, lower credit histories, and less access to financial products. Training data spanning 15+ years may encode these historical patterns. |
| **Evidence Base** | Gender gaps in credit access have narrowed significantly since 2010, but training data from earlier periods may still weight historical patterns. |
| **Potential Impact** | Female applicants, particularly those with career gaps or part-time employment patterns, may face lower approval rates than equivalent male applicants. |
| **Current Controls** | Gender is not used as a direct input feature |
| **Required Actions** | 1. Test for gender-based disparate impact in approval rates and score distribution 2. Assess whether employment type and income features act as gender proxies 3. Monitor outcomes by gender on an ongoing basis |

---

### 3.3 Age

| Assessment Field | Detail |
|---|---|
| **Risk Level** | 🟡 Medium |
| **Bias Pathway** | Younger applicants have shorter credit histories and less established income patterns — two features heavily weighted in credit scoring models. This is partly legitimate (less data to assess) but may over-penalise young applicants relative to their actual default risk. |
| **Evidence Base** | Age-based credit disadvantage is well-documented in consumer credit literature. NorthPoint's thin-file problem disproportionately affects applicants under 25. |
| **Potential Impact** | Applicants under 25 may face higher decline rates or lower scores that do not accurately reflect their credit risk. |
| **Current Controls** | None formalised |
| **Required Actions** | 1. Implement age-stratified performance benchmarks — assess approval rates and default rates by age band 2. Explore alternative data sources for thin-file applicants (e.g., rental payment history, utility payments) |

---

### 3.4 Disability

| Assessment Field | Detail |
|---|---|
| **Risk Level** | 🟡 Medium |
| **Bias Pathway** | Applicants receiving disability benefits have income patterns that differ significantly from salary-based applicants. Models trained primarily on salary-income data may treat disability benefits as a negative signal, despite their being a stable, government-guaranteed income source. |
| **Evidence Base** | FCA Financial Lives Survey (2022) identifies disabled adults as significantly more likely to be in financially vulnerable circumstances, including restricted credit access. |
| **Potential Impact** | Disabled applicants relying on benefits income may face disproportionate decline rates. |
| **Current Controls** | None formalised |
| **Required Actions** | 1. Review income feature engineering — ensure disability benefits are treated equivalently to other stable income sources 2. Establish manual review pathway for applications where disability income is the primary income source |

---

## 4. Proxy Variable Analysis

Proxy variables are input features that appear neutral but correlate with protected characteristics, allowing indirect discrimination to occur even when protected attributes are excluded from the model.

| Feature | Protected Characteristic Risk | Action Required |
|---|---|---|
| Postcode / Geographic area | Race/Ethnicity (residential segregation) | 🔴 Audit and test for disparate impact |
| Employment type | Gender (part-time, career gaps) | 🟡 Monitor; consider feature transformation |
| Income level | Gender, Disability, Age | 🟡 Normalise against cost-of-living; review benefit income handling |
| Credit history length | Age | 🟡 Supplement with alternative data for thin-file applicants |
| Previous defaults | Socioeconomic status | 🟡 Weight recency; consider rehabilitation window |

---

## 5. Bias Monitoring Framework

Following implementation of initial mitigations, NorthPoint should establish ongoing bias monitoring:

| Metric | Target | Monitoring Frequency | Alert Threshold |
|---|---|---|---|
| Approval rate parity across ethnic groups | < 5% differential | Monthly | > 5% triggers review |
| Approval rate parity across gender | < 3% differential | Monthly | > 3% triggers review |
| False positive rate parity across all groups | < 2% differential | Monthly | > 2% triggers review |
| Age-stratified approval vs. default rate correlation | Positive correlation | Quarterly | Negative correlation triggers model review |
| Disability benefit income — approval rate vs. salary income | Within 10% | Quarterly | > 10% differential triggers review |

---

## 6. EU AI Act Compliance Summary

| Article | Requirement | Current Status | Action Required |
|---|---|---|---|
| Article 10(2) | Training data free of errors and representative of the population | ⚠️ Partial — historical data not audited for bias | Commission training data bias audit |
| Article 10(3) | Examine data for possible biases that could affect fundamental rights | ❌ Not yet completed | Complete disparate impact analysis |
| Article 10(4) | Address data gaps and deficiencies | ❌ Not yet completed | Implement thin-file alternative data programme |
| Article 10(5) | Use of sensitive categories for bias detection (with safeguards) | ✅ Legal basis available under Art. 10(5) | Invoke exemption for bias audit |
| Article 9(2)(b) | Identify and analyse known and foreseeable risks | ✅ Complete — this document | Ongoing |

---

## 7. Recommended Actions — Priority Order

| Priority | Action | Owner | Target Date |
|---|---|---|---|
| 🔴 1 | Commission independent disparate impact audit across race, gender, age, disability | Head of Credit Risk | Q2 2025 |
| 🔴 2 | Audit proxy variables — postcode and employment type — for protected characteristic correlation | Head of Data Governance | Q2 2025 |
| 🔴 3 | Implement fairness-constrained model retraining if disparate impact confirmed | Head of Credit Risk | Q3 2025 |
| 🟡 4 | Establish ongoing bias monitoring dashboard with threshold alerts | Head of Credit Risk | Q2 2025 |
| 🟡 5 | Develop manual review pathway for edge cases (disability income, thin-file applicants) | Head of Credit Operations | Q3 2025 |
| 🟢 6 | Explore alternative data sources for thin-file applicants | Head of Data Engineering | Q4 2025 |

---

*Document prepared by the AI Governance Office, NorthPoint Financial Services.*  
*This assessment should be reviewed following each model retraining event and annually at minimum.*

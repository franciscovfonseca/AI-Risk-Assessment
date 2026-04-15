# EU AI Act — Article 9 Compliance Review
**Document Type:** Regulatory Compliance Checklist  
**Classification:** Internal — Restricted  
**Systems Covered:** NP-001 Credit Scoring Engine · NP-002 Fraud Detection System  
**Regulatory Reference:** EU AI Act 2024/1689 — Article 9 (Risk Management System)  
**Prepared by:** AI Governance Office  
**Status:** ✅ Complete — Gaps Identified and Actioned

---

## Overview of Article 9 Requirements

Article 9 of the EU AI Act requires providers of HIGH RISK AI systems to establish, implement, document, and maintain a **risk management system** that operates on a continuous basis throughout the entire lifecycle of the system.

The risk management system must:
1. Identify and analyse known and reasonably foreseeable risks associated with the system
2. Estimate and evaluate risks that may emerge when used as intended or under conditions of reasonably foreseeable misuse
3. Evaluate other risks based on post-market monitoring data
4. Implement risk mitigation measures and test their effectiveness

This review assesses NP-001 and NP-002 compliance against each Article 9 requirement.

---

## Compliance Status Legend

| Symbol | Status | Meaning |
|---|---|---|
| ✅ | Compliant | Requirement fully met with documented evidence |
| ⚠️ | Partial | Requirement partially met — specific gaps identified |
| ❌ | Non-Compliant | Requirement not met — action required |

---

## Article 9 Compliance Checklist

### 9(1) — Risk Management System Established

*"Providers shall establish, implement, document and maintain a risk management system for high-risk AI systems."*

| Requirement | NP-001 | NP-002 | Notes |
|---|---|---|---|
| Risk management system formally established | ✅ | ✅ | Established as part of Phase 2 governance programme |
| Risk management system documented | ✅ | ✅ | This document and the accompanying risk register constitute the documented system |
| Risk management system maintained on ongoing basis | ⚠️ | ✅ | NP-001 review schedule defined but not yet formalised in governance calendar |
| Responsible owner assigned for risk management system | ✅ | ✅ | NP-001: Head of Credit Risk · NP-002: Head of Financial Crime |

**Gap — NP-001:** Formalise the risk management review schedule into the AI Governance Committee calendar. Target: Q2 2025.

---

### 9(2)(a) — Risk Identification and Analysis

*"The risk management system shall identify and analyse the known and reasonably foreseeable risks associated with the AI system."*

| Requirement | NP-001 | NP-002 | Notes |
|---|---|---|---|
| Known risks identified and documented | ✅ | ✅ | Full risk registers in `docs/risk-assessment.md` |
| Reasonably foreseeable risks identified | ✅ | ✅ | Includes misuse scenarios, edge cases, and operational failure modes |
| Risks associated with intended use covered | ✅ | ✅ | |
| Risks from reasonably foreseeable misuse covered | ✅ | ✅ | |
| Risks to health, safety, and fundamental rights assessed | ✅ | ✅ | Bias and fairness risks addressed; customer harm scenarios documented |

---

### 9(2)(b) — Risk Estimation and Evaluation

*"The risk management system shall estimate and evaluate the risks arising from the use of the AI system in accordance with its intended purpose."*

| Requirement | NP-001 | NP-002 | Notes |
|---|---|---|---|
| Likelihood assessment for each risk | ✅ | ✅ | Documented in risk register with rationale |
| Impact assessment for each risk | ✅ | ✅ | Covers customer harm, regulatory, operational, and reputational impact |
| Inherent risk level calculated | ✅ | ✅ | Likelihood × Impact matrix applied consistently |
| Residual risk evaluated after mitigations | ✅ | ✅ | Residual risk documented per risk item |

---

### 9(2)(c) — Post-Market Risk Evaluation

*"The risk management system shall evaluate other risks based on analysis of data gathered from the post-market monitoring system."*

| Requirement | NP-001 | NP-002 | Notes |
|---|---|---|---|
| Post-market monitoring process defined | ⚠️ | ✅ | NP-001: monitoring metrics defined, formal process not yet implemented |
| Feedback loop from monitoring to risk register | ⚠️ | ✅ | NP-001: mechanism not yet established |
| Process for updating risk register based on monitoring data | ⚠️ | ✅ | NP-001: to be implemented alongside monitoring dashboard |

**Gap — NP-001:** Establish feedback loop between model performance monitoring (Article 9(7)) and the risk management system. Monitoring data should trigger formal risk register reviews. Target: Q3 2025.

---

### 9(3) — Testing and Risk Measures

*"The risk management measures referred to in paragraph 2, point (d), shall give due consideration to the effects and possible interactions resulting from the combined application of the requirements set out in Articles 10 to 15."*

| Requirement | NP-001 | NP-002 | Notes |
|---|---|---|---|
| Risk mitigation measures identified for all material risks | ✅ | ✅ | Documented in risk register |
| Mitigations address Articles 10–15 obligations | ⚠️ | ✅ | NP-001: bias testing (Art. 10) and explainability (Art. 13) measures defined but not yet implemented |
| Interactions between mitigation measures considered | ✅ | ✅ | |
| Mitigation measures tested for effectiveness | ❌ | ⚠️ | NP-001: bias audit not yet commissioned · NP-002: robustness testing schedule not yet formalised |

**Gap — NP-001:** Commission independent bias audit (Article 10 testing) by Q2 2025. Implement explainability layer and test with customer service team by Q2 2025.  
**Gap — NP-002:** Formalise robustness testing schedule with defined pass/fail criteria by Q2 2025.

---

### 9(4) — Residual Risk Communication

*"High-risk AI systems shall be tested to identify the most appropriate risk management measures. Testing shall ensure that the high-risk AI system performs consistently for its intended purpose and that it is in compliance with the requirements set out in this Chapter."*

| Requirement | NP-001 | NP-002 | Notes |
|---|---|---|---|
| System tested against intended purpose | ✅ | ✅ | Performance benchmarks established |
| Testing covers realistic conditions including edge cases | ⚠️ | ✅ | NP-001: edge case testing for protected characteristic groups not yet complete |
| Testing conducted before deployment | ✅ | ✅ | Both systems tested at initial deployment |
| Testing repeated after material changes | ✅ | ✅ | Change management process requires re-testing |

---

### 9(5) — Special Populations

*"Testing of high-risk AI systems shall be performed at any time throughout the development process, and in any event prior to placing on the market or putting into service. Testing shall be made against preliminarily defined metrics and probabilistic thresholds that are appropriate to the intended purpose of the high-risk AI system."*

| Requirement | NP-001 | NP-002 | Notes |
|---|---|---|---|
| Testing metrics defined | ✅ | ✅ | Accuracy, precision, recall, and F1 benchmarks established |
| Probabilistic thresholds set | ✅ | ✅ | Decision thresholds documented |
| Thresholds appropriate to intended purpose | ✅ | ✅ | |
| Metrics reviewed and updated regularly | ⚠️ | ✅ | NP-001: bias-specific metrics (demographic parity, equalised odds) not yet defined |

**Gap — NP-001:** Define fairness metrics and thresholds (demographic parity ratio, equalised odds difference) as part of the bias monitoring framework. Target: Q2 2025.

---

### 9(6) — Applicable Standards

*"Where providers are not able to fully comply with the technical specifications of a harmonised standard, they shall document the reasons and ensure an equivalent level of protection."*

| Requirement | NP-001 | NP-002 | Notes |
|---|---|---|---|
| Applicable harmonised standards identified | ✅ | ✅ | ISO 42001, ISO 31000 applied as reference standards |
| Deviations from standards documented with rationale | ✅ | ✅ | |

---

### 9(7) — Post-Market Monitoring Integration

*"High-risk AI system providers shall consider the impact that the risks identified in this Article may have on fundamental rights."*

| Requirement | NP-001 | NP-002 | Notes |
|---|---|---|---|
| Fundamental rights impact explicitly considered | ✅ | ✅ | Bias and fairness assessment addresses fundamental rights (non-discrimination, dignity) |
| Impact on vulnerable groups assessed | ⚠️ | ✅ | NP-001: disability and thin-file applicant analysis pending completion |
| Mitigations proportionate to fundamental rights risk | ✅ | ✅ | |

---

## Consolidated Gap Summary

| Gap ID | System | Article | Gap Description | Action | Owner | Target |
|---|---|---|---|---|---|---|
| GAP-01 | NP-001 | 9(1) | Review schedule not formalised in governance calendar | Add to AI Governance Committee calendar | Head of Credit Risk | Q2 2025 |
| GAP-02 | NP-001 | 9(2)(c) | No feedback loop from monitoring to risk register | Establish monitoring-to-risk-register process | Head of Credit Risk | Q3 2025 |
| GAP-03 | NP-001 | 9(3) | Bias testing (Art. 10) not yet commissioned | Commission independent bias audit | Head of Credit Risk | Q2 2025 |
| GAP-04 | NP-001 | 9(3) | Explainability layer not yet implemented | Implement SHAP/LIME; test with staff | Head of Credit Risk | Q2 2025 |
| GAP-05 | NP-002 | 9(3) | Robustness testing schedule not formalised | Define and document schedule with pass/fail criteria | Head of Financial Crime | Q2 2025 |
| GAP-06 | NP-001 | 9(5) | Fairness metrics not defined | Define demographic parity and equalised odds thresholds | Head of Credit Risk | Q2 2025 |
| GAP-07 | NP-001 | 9(7) | Vulnerability assessment incomplete for disability/thin-file | Complete assessment; establish manual review pathway | Head of Credit Operations | Q3 2025 |

---

## Overall Compliance Status

| System | Compliant Requirements | Partial | Non-Compliant | Overall Status |
|---|---|---|---|---|
| NP-001 Credit Scoring Engine | 18 | 7 | 2 | ⚠️ Partial — gaps identified, remediation in progress |
| NP-002 Fraud Detection System | 24 | 2 | 0 | ⚠️ Partial — minor gaps, on track for full compliance |

**Assessment conclusion:** Neither system is fully Article 9 compliant at the time of this assessment. NP-001 has the most material gaps, concentrated in bias testing and monitoring. Both systems have clear remediation plans in place with Q2–Q3 2025 target dates. No gaps represent an immediate regulatory enforcement risk, but the bias testing gap (GAP-03) for NP-001 should be treated as the highest priority given its fundamental rights implications.

---

*Document prepared by the AI Governance Office, NorthPoint Financial Services.*  
*This checklist should be reviewed following any material system change and at each 6-monthly risk management review.*

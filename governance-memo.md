# Board Governance Memo — AI Risk Assessment Findings
**STRICTLY CONFIDENTIAL**

---

**TO:** Board Risk Committee · Chief Risk Officer · Chief Compliance Officer  
**FROM:** AI Governance Office  
**DATE:** Q1 2025  
**RE:** Phase 2 AI Risk Assessment — HIGH RISK Systems NP-001 and NP-002  
**Classification:** Board Restricted

---

## Purpose

This memo presents the findings of NorthPoint Financial Services' Phase 2 AI Risk Assessment, covering the two systems classified as HIGH RISK under the EU AI Act in Phase 1: the Credit Scoring Engine (NP-001) and the Fraud Detection System (NP-002).

The Board is asked to note the findings, approve the recommended priority actions, and confirm ownership assignments at the executive level.

---

## Background

In Q4 2024, NorthPoint completed Phase 1 of its AI Governance Programme — a structured inventory and classification of all production AI systems. That exercise identified four systems, of which two were classified HIGH RISK under EU AI Act Annex III: NP-001 (Credit Scoring Engine) and NP-002 (Fraud Detection System).

The EU AI Act, which entered into force in August 2024, requires HIGH RISK AI systems to have a documented, ongoing risk management system in place (Article 9). Non-compliance carries enforcement risk including fines of up to €30 million or 6% of global annual turnover, whichever is higher. Phase 2 delivers that risk management system.

---

## Key Findings

### Finding 1 — NP-001 presents material bias risk requiring urgent action

The Credit Scoring Engine makes approximately 48,000 automated lending decisions per year. Our risk assessment identified **demographic bias as a Critical risk** — the highest severity category.

The model uses postcode and geographic data as input features. These features are known to correlate with race and ethnicity due to historical residential segregation patterns. The model has not been tested for differential impact across protected characteristic groups. This means NorthPoint cannot currently demonstrate that it is not discriminating in its credit decisions — which is a regulatory and legal exposure.

**The business consequence is significant:** If a regulatory audit or customer complaint triggers a disparate impact investigation, NorthPoint would be unable to produce evidence of bias testing. This creates exposure under the EU AI Act, UK Equality Act, and FCA Consumer Duty simultaneously.

**This is not a theoretical risk.** The FCA has signalled that algorithmic bias in consumer credit is an enforcement priority for 2025. Several peer institutions have already received supervisory scrutiny on this issue.

### Finding 2 — NP-001 cannot currently explain its credit refusals

Customers declined for credit receive no explanation of the factors that drove the decision. This is non-compliant with EU AI Act Article 13 and GDPR Article 22, both of which give individuals the right to a meaningful explanation of automated decisions affecting them.

Beyond the regulatory obligation, this is a customer experience and reputational risk. A declined customer who cannot understand why they were refused cannot seek to improve their position — and is more likely to escalate to the FCA or a consumer body.

### Finding 3 — NP-002 false positive rate requires a service standard

The Fraud Detection System places automatic holds on customer accounts when transactions are flagged as suspicious. Our assessment found that the false positive rate — legitimate transactions incorrectly blocked — lacks a formal service level agreement and is not monitored against a defined target.

This is a customer harm risk under FCA Consumer Duty. Customers who are unable to access their funds due to incorrect fraud flags suffer real harm, particularly in time-sensitive situations. Without a defined and monitored SLA, NorthPoint has no mechanism to identify or respond to deteriorating performance.

### Finding 4 — Overall Article 9 compliance is partial for both systems

Neither NP-001 nor NP-002 is fully compliant with EU AI Act Article 9 at the time of this assessment. NP-001 has seven gaps, including two non-compliant requirements. NP-002 has two partial gaps. Full remediation plans are in place, targeting Q2–Q3 2025.

---

## Recommendations

The Board Risk Committee is asked to approve the following four actions:

---

**Recommendation 1 — Commission independent bias audit for NP-001**  
*Priority: Critical · Owner: Head of Credit Risk · Target: Q2 2025*

Commission an independent third-party audit of the Credit Scoring Engine for disparate impact across race, gender, age, and disability. This audit should use Article 10(5) exemption to access sensitive demographic data for bias detection purposes only. Results should be reported to this Committee within 90 days.

Until the audit is complete, the AI Governance Office recommends implementing a manual review pathway for any credit refusal where the applicant's profile suggests elevated bias risk — specifically thin-file applicants and applicants with postcode data flagged as high-correlation with protected characteristics.

*Estimated cost: £40,000–£80,000 for independent audit engagement*

---

**Recommendation 2 — Implement credit refusal explanations for NP-001**  
*Priority: High · Owner: Head of Credit Risk · Target: Q2 2025*

Implement a post-hoc explainability layer (SHAP or equivalent) on NP-001 outputs. Develop customer-facing refusal communication templates that present the top three factors contributing to a decline in plain, accessible language. Train customer service teams to discuss these explanations with applicants.

This resolves the EU AI Act Article 13 and GDPR Article 22 compliance gaps and directly improves the customer experience for declined applicants.

*Estimated cost: £15,000–£25,000 for technical implementation*

---

**Recommendation 3 — Establish false positive SLA for NP-002**  
*Priority: High · Owner: Head of Financial Crime · Target: Q2 2025*

Define a false positive rate SLA for the Fraud Detection System (recommended target: < 0.5% of legitimate transactions incorrectly blocked). Implement automated monitoring against this SLA with monthly reporting to the AI Governance Committee and escalation to the CRO if the threshold is breached. Establish a 24-hour resolution target for customers disputing an incorrect block.

This directly addresses the FCA Consumer Duty harm avoidance obligation and provides NorthPoint with a defensible position in the event of a customer complaint or regulatory enquiry.

*Estimated cost: £5,000–£10,000 for monitoring infrastructure*

---

**Recommendation 4 — Formalise Article 9 review schedule for both systems**  
*Priority: Medium · Owner: Chief Risk Officer · Target: Q2 2025*

Add both NP-001 and NP-002 Article 9 risk management reviews to the AI Governance Committee calendar — NP-001 every 6 months, NP-002 every 3 months. Assign the AI Governance Office as responsible for preparing review materials, with sign-off required from the relevant system owner.

This formalises the ongoing nature of the Article 9 obligation and ensures NorthPoint maintains a continuously updated, audit-ready risk management record for both systems.

*Cost: Internal resource only*

---

## Financial Summary

| Action | Estimated Cost | Risk Addressed | Regulatory Exposure Avoided |
|---|---|---|---|
| Independent bias audit — NP-001 | £40,000–£80,000 | Demographic bias (Critical) | EU AI Act fines; FCA Consumer Duty enforcement; Equality Act litigation |
| Explainability layer — NP-001 | £15,000–£25,000 | Lack of explanation (High) | EU AI Act Article 13; GDPR Article 22 |
| False positive SLA — NP-002 | £5,000–£10,000 | Customer harm (High) | FCA Consumer Duty |
| Review schedule formalisation | Internal resource | Ongoing compliance | Regulatory readiness |
| **Total estimated investment** | **£60,000–£115,000** | | **Up to €30M / 6% turnover fine risk** |

The investment is proportionate. The maximum EU AI Act fine for non-compliance is €30 million or 6% of global annual turnover. The estimated remediation cost represents a small fraction of this exposure.

---

## Next Steps

Subject to Board approval of these recommendations:

1. AI Governance Office to procure independent bias audit provider by end of Q1 2025
2. Technology team to begin explainability layer implementation by start of Q2 2025
3. Head of Financial Crime to define false positive SLA and monitoring specification by end of Q1 2025
4. CRO to add AI Governance Committee review dates to board calendar by end of Q1 2025

Phase 3 of the AI Governance Programme — AI Controls & Remediation Framework — will begin in Q3 2025, covering the implementation and testing of the controls identified in this assessment.

---

*This memo and its attachments are strictly confidential and prepared for the sole use of the NorthPoint Financial Services Board Risk Committee.*  
*Prepared by the AI Governance Office. Queries: AI Governance Office, NorthPoint Financial Services.*

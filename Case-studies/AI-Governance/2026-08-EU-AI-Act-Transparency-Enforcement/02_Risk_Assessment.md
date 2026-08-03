# Risk Assessment
## 2026-08-EU-AI-Act-Transparency-Enforcement

## Risk Scoring
| Method | Score | Rating |
|---|---|---|
| Likelihood × Impact Matrix | 5 × 4 = 20 | Critical |
| CVSS Base Score | Not applicable — regulatory/compliance finding, not a technical vulnerability | N/A |
| FAIR Qualitative | High loss exposure for non-compliant EU-facing AI deployments (fines up to 3% global turnover); certain (not probabilistic) triggering event | High |

## Risk Narrative
Likelihood is scored at the maximum (5) because this is not a theoretical or probabilistic risk — enforcement began 2026-08-02 and is now an active, ongoing legal obligation rather than a future contingency. Impact is scored at 4 (not 5) because the penalty tier for Article 50 transparency non-compliance (up to €15M or 3% global turnover) is meaningful but sits below the Act's top tier (€35M / 7%, reserved for prohibited AI practices under Article 5) and because enforcement in the initial period typically emphasizes guidance and correction over maximum-penalty action. The most probable "attack path" here is not adversarial but administrative: an organization with an EU-facing chatbot, AI customer-service agent, or generative content tool that has not implemented disclosure banners, deepfake labeling, or machine-readable AI-content watermarking is now out of compliance by default, and exposure surfaces through user complaints, competitor reporting, or routine market-surveillance-authority review rather than through any single triggering incident.

## Framework Control Gaps
- **NIST AI RMF GOVERN function:** Organizations without a documented AI governance program that tracks regulatory applicability by jurisdiction and AI use case have no mechanism to have caught this deadline systematically.
- **ISO 42001 Clause 8.4 (AI system impact assessment):** AI system impact assessments should explicitly evaluate transparency/disclosure obligations as part of the assessment, not only technical/ethical risk.
- **NIST 800-53 PT-5 (Privacy Notice) — analog control:** The transparency-notice discipline required for privacy programs is directly transferable to AI-interaction disclosure; organizations with mature PT-5 practices are better positioned to extend that pattern to AI disclosure banners.
- **EU AI Act Article 50 itself:** The primary compliance gap is the absence of technical implementation — disclosure UI/UX for chatbots, watermarking pipelines for generative content — not merely a documentation gap.

## Residual Risk Statement
Organizations that implement clear, conspicuous AI-interaction disclosures, deepfake labeling at first point of exposure, and machine-readable watermarking on generative AI outputs reduce residual risk to Low. Organizations relying on the Digital Omnibus's delay of high-risk system obligations (to December 2027) as a reason to delay Article 50 compliance are conflating two separate deadlines — Article 50 transparency obligations are in force now, independent of an AI system's high-risk classification status.

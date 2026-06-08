# Risk Assessment
## Case: EU AI Act — Draft High-Risk AI Classification Guidelines (Public Consultation, Closes 2026-06-23)
**Risk ID:** RR-009 | **Date:** 2026-06-08 | **Analyst:** Blaise Kingko

---

### 1. Risk Statement
Organizations that deploy or develop AI systems affecting EU residents — including internal enterprise LLM tools, HR/recruitment AI, and biometric or decision-support systems — face compliance risk if they have not formally classified those systems against the EU AI Act's evolving high-risk criteria before the criteria solidify and the (extended but real) 2027/2028 enforcement milestones approach.

### 2. Likelihood Assessment — **3 (Technically feasible / regulatory certainty high, organizational gap likely)**
This is not a "may happen" technical threat — the regulation is in force and the classification guidance is actively being finalized. The "likelihood" in this context reflects the probability that an organization's *current* AI inventory and classification practice has a material gap relative to the emerging criteria — which, based on industry surveys cited in the Commission's own consultation rationale, is common among organizations that have not yet run a formal Annex III mapping exercise.

### 3. Impact Assessment — **3 (Service disruption / compliance remediation burden)**
Failure to classify correctly does not produce an immediate breach-style impact, but it creates compounding compliance debt: retroactive conformity assessments, technical documentation backfilling, EU database registration under compressed timelines, and potential regulatory engagement — all of which disrupt product roadmaps and consume significant compliance and engineering resources if discovered late rather than addressed proactively.

### 4. Risk Score & Rating
**Likelihood (3) × Impact (3) = 9 → Medium**

### 5. Inherent Risk
Medium-High — any organization with EU-facing AI systems and no current formal Annex III classification exercise carries latent compliance exposure that compounds the longer it goes unaddressed.

### 6. Current Controls (Baseline)
- Existing ISO 42001 AI management-system processes (where implemented) already require AI risk and impact assessment (Clauses 6.1.2, 8.4) — these can be directly leveraged for EU AI Act classification.
- NIST AI RMF MAP function practices (where adopted) provide a structured methodology for characterizing AI system context, intended use, and impact — directly transferable to Annex III analysis.
- General counsel / regulatory affairs monitoring of EU AI Act developments (assumed standard practice for organizations with EU exposure).

### 7. Residual Risk (Post-Classification Exercise)
**Low (Score ≈ 4)** — once a formal, evidenced AI-system inventory and Annex III classification mapping exists (and is kept current), residual compliance risk drops to standard regulatory-monitoring baseline, with the organization positioned to respond quickly as final guidance is published.

### 8. Framework Mapping
- **NIST AI RMF:** GOVERN (policy and accountability for classification process ownership); **MAP** (1.1 — context established; 5.1 — impact characterized)
- **ISO/IEC 42001:2023:** Clause 6.1.2 (AI risk assessment), Clause 8.4 (AI system impact assessment), Clause 4.1 (understanding organizational context)
- **EU AI Act:** Article 6 (Classification rules), Annex III (High-risk use case list)

### 9. Recommended Remediation
1. Compile or refresh a complete inventory of all AI/ML systems in use or development that are accessible to, or produce outputs affecting, EU-resident individuals.
2. Map each system against the draft Annex III classification criteria; document the classification rationale as formal evidence (dual-purpose: EU AI Act readiness + ISO 42001 Clause 8.4 impact-assessment evidence).
3. For systems in genuine classification ambiguity, consider submitting structured feedback to the Commission's public consultation (closes 2026-06-23) — this is a rare opportunity to influence binding interpretive guidance before finalization.
4. Establish a recurring (at minimum semi-annual) AI-inventory review cadence tied to the GOVERN function, ensuring new AI deployments are classified at design time rather than retroactively.

### 10. Owner / Status / Due Date
**Owner:** AI Governance Lead / GRC (Blaise Kingko), in coordination with Legal & Regulatory Affairs | **Status:** Open — proactive/advisory | **Due Date:** 2026-06-23 (consultation deadline) for initial classification pass; ongoing thereafter

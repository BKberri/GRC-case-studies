# Business Impact Analysis (BIA)
## Case: EU AI Act — Draft High-Risk AI Classification Guidelines (Public Consultation)

---

### 1. Process / Asset Criticality
**Affected Asset Class:** AI/ML systems and the AI governance program supporting EU-market product compliance, internal LLM deployments, HR/recruitment tooling, and any biometric or decision-support AI accessible to or affecting EU residents.
**Criticality Tier:** Tier 2 — strategic/regulatory criticality (not an immediate operational-availability concern, but a compounding compliance-debt and market-access risk).

### 2. Impact Categories

**Operational Impact**
A late or incorrect classification exercise forces compressed-timeline remediation: rapid technical-documentation production, conformity-assessment scheduling, and EU database registration — diverting engineering and compliance resources from planned roadmap work on short notice.

**Financial Impact**
EU AI Act penalties for high-risk system non-compliance can reach up to **€15 million or 3% of global annual turnover** (whichever is higher) for serious violations, with lower-but-still-material tiers for lesser infractions. Proactive classification cost: modest (compliance/legal analyst time over several weeks); reactive remediation cost under regulatory scrutiny: substantially higher, plus potential market-access restriction for non-compliant systems.

**Reputational Impact**
Being identified as non-compliant with a high-profile, globally-watched AI regulation would materially undermine credibility with EU customers, partners, and — for a security/GRC consulting portfolio specifically — would directly contradict the value proposition of demonstrated AI-governance expertise.

**Regulatory / Legal Impact**
Direct exposure under the EU AI Act itself; secondary exposure where AI systems also process personal data (GDPR overlap — Article 35 DPIA requirements closely parallel AI Act impact-assessment obligations, creating an opportunity for combined evidence packages).

### 3. Recovery Objectives
Not an availability-style BIA — "recovery" here means time-to-compliance. Target: complete initial Annex III classification mapping within the current consultation window (by 2026-06-23) to allow time for any necessary remediation before the December 2027 / August 2028 enforcement milestones.

### 4. Maximum Tolerable Delay
Recommend no more than **90 days** from this identification date before a documented, evidenced classification inventory exists — providing roughly 18 months of runway before the earliest (December 2027) enforcement milestone to remediate any systems found to be high-risk.

### 5. Dependencies
- Legal & Regulatory Affairs engagement to interpret final guidance as it's published
- Existing ISO 42001 risk-assessment artifacts (if a management system is in place) as a foundation for the classification exercise
- Engineering/product teams to provide accurate AI-system inventories and intended-use documentation

### 6. BIA Conclusion
This is a **proactive regulatory-readiness** scenario, not a reactive incident. The business impact of inaction compounds quietly over the next 18 months — the cost of acting now (a structured inventory and classification exercise, potentially paired with consultation feedback) is a fraction of the cost of reactive remediation under regulatory scrutiny or, worse, formal enforcement action after the December 2027 milestone arrives.

---

## Update — 2026-06-29

| Impact Type | Assessment |
|---|---|
| Confidentiality | Not applicable — regulatory timeline change, not a technical vulnerability |
| Integrity | Low — governance documentation and roadmap artifacts require updating to reflect revised deadlines |
| Availability | Not applicable |
| Regulatory / Compliance | Medium — affects compliance program sequencing; ultimate obligation unchanged |
| Reputational | Low-Medium — any external-facing statements that referenced the original deadline should be reviewed |

**Recovery framing:** Not applicable in the technical RTO/RPO sense. Recommend updating the AI governance program roadmap and board reporting materials within the current reporting cycle.

**Dependency note:** Any vendor contracts, customer commitments, or internal SLAs that referenced the original EU AI Act deadline should be reviewed and updated — with care not to over-communicate timeline relief in a way stakeholders could mistake for obligation relief.

**Conclusion:** The Section 4 Maximum Tolerable Delay (90 days from original identification) and the financial-exposure modeling in Section 2 remain valid and unchanged — this update affects program *sequencing*, not the magnitude of underlying exposure.

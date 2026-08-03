# Business Impact Analysis
## 2026-08-EU-AI-Act-Transparency-Enforcement

## Illustrative Organization Profile
A US-headquartered SaaS company offering a customer-support platform with an AI-powered chatbot and an AI content-generation feature (auto-drafted email responses and marketing copy), serving both US and EU-based enterprise customers and their end users.

## Impact Assessment
| Impact Category | Description | Severity |
|---|---|---|
| Operational | Requires near-term product changes: disclosure UI for chatbot interactions, watermarking pipeline for AI-generated content, deployer-facing configuration for deepfake labeling | Medium |
| Financial | Fines up to €15M or 3% of global annual turnover for non-compliance; also product-engineering cost to implement disclosure/watermarking features | High |
| Reputational | EU enterprise customers increasingly require AI Act compliance attestations in procurement/vendor-security reviews; non-compliance risks deal friction and customer churn independent of any regulatory action | Medium-High |
| Regulatory/Legal | Direct EU AI Act Article 50/99 exposure; overlapping obligations with California SB 942 for the same product surface serving US users, creating a need for a harmonized (not jurisdiction-by-jurisdiction) disclosure and watermarking implementation | High |
| Data | Not a data-breach scenario — this is a disclosure/labeling obligation, not a data-protection incident; GDPR obligations remain separately applicable to the same AI systems | N/A (see regulatory) |

## Recovery Objectives
Not applicable in the traditional incident-recovery sense — this is a compliance implementation timeline rather than an incident requiring RTO/RPO/MTTR. The equivalent operational target is time-to-compliance:

| Objective | Target |
|---|---|
| Time to conspicuous AI-disclosure UI (chatbot) | 30 days from gap identification |
| Time to generative-content watermarking implementation | 60–90 days (dependent on engineering capacity and vendor tooling, e.g., C2PA-compliant marking) |
| Time to documented compliance attestation for enterprise customer procurement requests | 30 days |

## Regulatory Exposure
Article 99 Tier 2 applies: fines up to €15,000,000 or 3% of total worldwide annual turnover for the preceding financial year, whichever is higher (SMEs pay the lower of the two amounts). Because this organization also serves California users with the same AI-generated-content features, California's SB 942 (as amended by AB 853) creates a parallel, partially overlapping disclosure/watermarking obligation with its own phased timeline through January 1, 2027 — the compliance program should design a single disclosure/watermarking implementation that satisfies both regimes rather than building jurisdiction-specific point solutions.

## Business Continuity Considerations
No continuity-of-operations risk exists from this finding — products continue to function without interruption. The relevant "continuity" consideration is contractual and commercial: EU enterprise customers may begin requiring AI Act Article 50 compliance attestations as a condition of contract renewal, making this a sales-continuity risk if not addressed on the timelines above.

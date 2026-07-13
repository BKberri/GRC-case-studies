# Control / Framework Mapping Matrix
## Case: EU AI Act — Draft High-Risk AI Classification Guidelines (Public Consultation)

| Framework | Reference | Element | Application to This Case |
|---|---|---|---|
| NIST AI RMF | GOVERN 1.1 / 1.2 | Legal and regulatory requirements involving AI are understood, managed, and documented; characteristics of trustworthy AI are integrated into organizational policies | Establishes ownership and policy basis for the classification exercise |
| NIST AI RMF | MAP 1.1 | Context (intended purposes, potentially beneficial uses, context-specific laws) is established and understood | Directly supports determining whether a system falls under Annex III |
| NIST AI RMF | MAP 5.1 | Likelihood and magnitude of each identified impact are assessed | Mirrors the EU's high-risk impact-based classification logic |
| ISO/IEC 42001:2023 | Clause 6.1.2 | AI risk assessment | Provides the structured methodology to perform and evidence the classification exercise |
| ISO/IEC 42001:2023 | Clause 8.4 | AI system impact assessment | Direct evidentiary overlap with EU AI Act high-risk determination criteria |
| ISO/IEC 42001:2023 | Clause 4.1 | Understanding the organization and its context | Frames why and where EU exposure exists (markets, users, data subjects) |
| EU AI Act | Article 6 | Classification rules for high-risk AI systems | The regulatory provision the draft guidelines interpret |
| EU AI Act | Annex III | List of high-risk AI use cases | The classification checklist against which the AI inventory must be mapped |
| GDPR (cross-reference) | Article 35 | Data Protection Impact Assessment (DPIA) | Significant evidentiary overlap — combine DPIA and AI Act impact-assessment workstreams where systems process personal data |

### Mapping Notes
- This case is a strong illustration of the **AI/ML framework track** described in the program's Framework Reference Map: NIST AI RMF (MAP) feeds directly into ISO 42001 (Clause 6.1.2/8.4), which in turn produces the evidence needed for EU AI Act Article 6/Annex III classification — a single evidence chain serving three frameworks.
- Recommend building (or updating) a combined "AI System Classification & Impact Assessment" template that satisfies NIST AI RMF MAP documentation, ISO 42001 Clause 8.4 evidentiary requirements, EU AI Act Annex III classification rationale, and GDPR Article 35 DPIA needs in a single artifact — reducing duplicated compliance effort across all four.

---

## Update — 2026-06-29

Framework mapping above is unchanged — Annex III classification criteria were not altered by this update. The only mapping addition concerns governance-process controls:

| Framework | Control/Clause | Application to This Update |
|---|---|---|
| NIST AI RMF | GOVERN 1.1 / 1.3 | Update regulatory tracking and re-baseline program timeline to reflect revised deadline |
| ISO/IEC 42001:2023 | Clause 6.1 | Reassess AI management system implementation roadmap against revised deadline |
| ISO/IEC 42001:2023 | Clause 9.3 (Management review) | Brief leadership on revised timeline at next scheduled review |
| EU AI Act | Annex III | Unchanged — no reclassification required |

**Gap assessment:** No control gap introduced by this regulatory update. Recommend a documentation-control SLA (e.g., 30 days) for updating internal compliance tracking artifacts whenever a regulatory deadline change of this nature occurs, to prevent stale compliance documentation.

# Control Mapping
## 2026-08-EU-AI-Act-Transparency-Enforcement

## Applicable Frameworks
NIST AI RMF and ISO 42001 as the primary AI governance framework track for this case category, with the EU AI Act itself as the binding regulatory instrument; NIST 800-53 PT-family controls referenced by analogy for transparency/notice discipline.

## Control Mapping Table
| Framework | Control ID | Control Name | Applicability | Gap / Status |
|---|---|---|---|---|
| NIST AI RMF | GOVERN 1.1 | Legal and regulatory requirements involving AI are understood, managed, and documented | Requires an active process for tracking AI-specific regulatory deadlines by jurisdiction | Partial |
| NIST AI RMF | MAP 1.1 | Context and purpose of AI system use is established and understood | Chatbot/generative-content use cases must be mapped against Article 50 triggers | Partial |
| NIST AI RMF | MANAGE 4.1 | Post-deployment monitoring for AI system risk, including regulatory compliance drift | Ongoing monitoring as jurisdictions add AI transparency requirements | Gap |
| ISO 42001 | Clause 8.4 | AI system impact assessment | Should explicitly assess transparency/disclosure obligations, not only ethical/technical risk | Gap |
| ISO 42001 | Clause 6.1.3 | AI risk treatment | Disclosure UI and watermarking implementation are risk-treatment actions for this finding | Open (in progress) |
| EU AI Act | Article 50 | Transparency Obligations for Providers and Deployers | Direct, binding requirement; primary compliance driver for this case | Gap (pending implementation) |
| NIST 800-53 (analog) | PT-5 | Privacy Notice | Transferable discipline for designing clear, conspicuous AI-interaction disclosures | Partial |

## Control Narrative
This case sits at the intersection of AI governance and product compliance rather than technical security control, so the controls above are primarily governance (GOVERN 1.1, Clause 8.4) and detective/monitoring (MANAGE 4.1) in nature, with the actual risk treatment being a product-engineering deliverable: conspicuous AI-interaction disclosure UI, deepfake labeling at first exposure, and machine-readable watermarking on generative outputs (commonly implemented via C2PA Content Credentials or comparable provenance-marking standards).

A mature AI governance program treats regulatory-deadline tracking as a standing GOVERN-function activity — maintaining a live map of AI use cases against applicable jurisdictional requirements (EU AI Act Article 50, California SB 942, Colorado SB 24-205, and emerging state/national AI transparency laws) rather than discovering each deadline reactively. Organizations that had already implemented ISO 42001-aligned AI system impact assessments including disclosure/transparency review were positioned to meet this deadline without a scramble; this case should be used to close that Clause 8.4 process gap for organizations that had not yet built transparency review into their AI impact assessment template.

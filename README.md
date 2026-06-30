# GRC Intelligence & Case Study Portfolio
### Blaise Kingko — Senior Cloud GRC & Security Architect

[![LinkedIn](https://img.shields.io/badge/LinkedIn-berrikingko-blue?style=flat&logo=linkedin)](https://linkedin.com/in/berrikingko)
[![Frameworks](https://img.shields.io/badge/Frameworks-NIST%20%7C%20ISO%20%7C%20CIS%20%7C%20EU%20AI%20Act-navy?style=flat)]()
[![Focus](https://img.shields.io/badge/Focus-Cloud%20GRC%20%7C%20AI%20Governance%20%7C%20Threat%20Intel-2E86C1?style=flat)]()

---

## What This Repository Is

This is a working GRC intelligence program — not a study guide.

Every file here reflects how I approach real-world governance, risk, and compliance work: structured analysis, framework-mapped findings, and outputs built for decision-makers — not just compliance checkboxes.

Seven years of enterprise GRC across FinTech, financial services, and healthcare taught me that the gap between a good security program and a reactive one is almost always an intelligence problem. Organizations that understand their risk posture in real time make better decisions. Those that find out during an audit don't.

This repository is where I apply that thinking continuously — tracking live threat intelligence, running risk assessments against the frameworks that matter, and producing executive-grade outputs that connect technical findings to business risk.

---

## Repository Structure

```
GRC-case-studies/
│
├── Case-studies/                     ← Real-world incidents analyzed through a GRC lens
│   ├── IT-OT-Threats/                ← Infrastructure, ICS/SCADA, network threats
│   ├── Cloud-Security/               ← AWS, Azure, IAM, cloud misconfigurations
│   ├── AI-Governance/                ← LLM risks, EU AI Act, model security
│   ├── Financial-Services/           ← Regulated industry incidents
│   └── (each category includes a TEMPLATE_*.md defining the standard case format)
│
├── Risk_Register/                    ← Live enterprise risk register
│   └── GRC_Intelligence_Risk_Register.xlsx       (versioned weekly snapshots alongside)
│
├── Executive_Reports/                ← Board and CISO-ready reporting
│   ├── Executive_Report_Template.docx
│   └── Weekly-Reports/               ← Dated weekly intelligence reports
│
└── Frameworks/                       ← Framework mapping references
```

---

## Intelligence Program — How It Works

Every week this program runs a structured sweep across the following sources:

| Source | Category | Framework Track |
|---|---|---|
| CISA KEV | Actively exploited vulnerabilities | NIST CSF 2.0, NIST 800-53, CIS Controls |
| US-CERT / CISA Advisories | Threat actor activity | NIST CSF 2.0, ISO 27001 |
| NIST NVD | CVEs CVSS ≥ 7.0 | NIST 800-53, CIS Controls |
| AWS Security Bulletins | Cloud platform threats | NIST 800-53, CIS Control 7 |
| Azure Security Updates | Cloud platform threats | NIST 800-53, CIS Control 7 |
| EU AI Act Updates | AI regulatory developments | NIST AI RMF, ISO 42001, EU AI Act |
| NIST AI RMF Updates | AI governance framework | NIST AI RMF, ISO 42001 |
| MITRE ATT&CK | Threat actor TTPs | NIST CSF 2.0, NIST 800-53 |
| MITRE ATLAS | AI/ML-specific threats | NIST AI RMF, ISO 42001 |

### Dual Framework Track

IT/OT and cloud threats map to:
**NIST CSF 2.0 → ISO 27001 → NIST 800-53 → CIS Controls**

AI/ML and governance threats map to:
**NIST AI RMF → ISO 42001 → EU AI Act**

---

## Risk Register

The live risk register tracks every identified threat through the full lifecycle:

- **Source** — where the intelligence came from
- **Framework mapping** — which controls are implicated
- **Likelihood × Impact scoring** — structured 5×5 methodology
- **Inherent vs residual risk** — before and after controls
- **Remediation** — specific actions with CIS Control references
- **Status tracking** — Open / Mitigating / Closed / Accepted

**Risk Rating Scale:**

| Score | Rating |
|---|---|
| 20–25 | 🔴 Critical |
| 10–19 | 🟠 High |
| 5–9 | 🟡 Medium |
| 1–4 | 🟢 Low |

---

## Case Studies

Each case study follows a standard structure:

1. **Incident Summary** — what happened and when
2. **Technical Analysis** — root cause, attack vector, affected systems
3. **Framework Impact** — which controls failed or were absent
4. **Risk Model Implications** — how this challenges existing risk assumptions
5. **AI / Emerging Threat Angle** — where applicable
6. **Recommended Controls** — specific, framework-referenced remediation
7. **Executive Summary** — board-level takeaway in plain language

### Published Case Studies

20 unique case studies published to date, organized by threat category:

| Category | Case Studies | Frameworks |
|---|---|---|
| [IT-OT-Threats](./Case-studies/IT-OT-Threats) | 15 | NIST CSF, NIST 800-53, CIS Controls, IEC 62443 |
| [Cloud-Security](./Case-studies/Cloud-Security) | 5 | NIST CSF, NIST 800-53, CIS Control 7 |
| [AI-Governance](./Case-studies/AI-Governance) | 2 | NIST AI RMF, ISO 42001, EU AI Act |
| [Financial-Services](./Case-studies/Financial-Services) | 1 | NIST 800-53, GLBA, SOX, SEC Cybersecurity Rules |

*3 cases (Oracle PeopleSoft, LiteLLM AI Gateway, MSRC Patch Tuesday Wormable Kernel) are intentionally cross-filed under two categories per the program's multi-category duplication policy — each carries its own documented rationale rather than being an accidental copy. Folder counts above include both filings; the 20 figure is the unique-case count. New case studies added weekly as part of the intelligence monitoring cycle.*

### Featured Case Studies

| Case Study | Date | Threat Category | Frameworks |
|---|---|---|---|
| [CISA KEV — Oracle PeopleSoft Unauthenticated RCE (Zero-Day)](./Case-studies/Financial-Services/2026-06-CISA-KEV-Oracle-PeopleSoft) | June 2026 | Financial Services — ERP / Regulated Industry | NIST 800-53, SEC 4-day disclosure rule, GLBA |
| [EU AI Act — High-Risk AI System Classification (Draft Guidelines)](./Case-studies/AI-Governance/2026-06-EU-AI-Act-HighRisk-Classification) | June 2026 | AI Governance — Regulatory | NIST AI RMF, ISO 42001, EU AI Act |
| [AWS Bulletin — "Copy.fail" / "DirtyFrag" Linux Kernel LPE Family](./Case-studies/Cloud-Security/2026-06-AWS-Bulletin-Linux-Kernel-CopyFail) | June 2026 | Cloud Security — Platform Vulnerability | NIST CSF, NIST 800-53, CIS Control 7 |
| [Cisco Catalyst SD-WAN Manager — Authenticated Command Injection (root)](./Case-studies/IT-OT-Threats/2026-06-CISA-KEV-Cisco-SDWAN) | June 2026 | IT/OT — Network Infrastructure | NIST CSF, NIST 800-53, CIS Controls |
| [Cisco Catalyst SD-WAN Manager — Path Traversal (Root Escalation)](./Case-studies/IT-OT-Threats/2026-06-CISA-KEV-Cisco-SDWAN-PathTraversal) | June 2026 | IT/OT — Network Infrastructure | NIST CSF, NIST 800-53, CIS Controls |
| [Microsoft Patch Tuesday — Wormable Windows Kernel RCE & HTTP.sys RCE](./Case-studies/IT-OT-Threats/2026-06-MSRC-PatchTuesday-WormableKernel) | June 2026 | IT/OT — Cross-Infrastructure | NIST CSF, NIST 800-53, CIS Controls |

*Full index of all 20 case studies is browsable directly in the [Case-studies](./Case-studies) folder by category.*

---

## Executive Reporting

Weekly intelligence runs produce a structured executive report containing:

- Key Risk Indicators (KRIs) — current week vs prior week
- Top threats with business impact framing
- AI Governance Watch — regulatory and threat developments
- Compliance posture across all mapped frameworks
- Recommended executive actions with owners and timelines

Reports are written for a CISO or board audience — technical findings translated into business risk language.

---

## Frameworks Referenced

| Framework | Domain | Use in This Program |
|---|---|---|
| NIST CSF 2.0 | Cybersecurity | Primary IT/OT control mapping |
| NIST SP 800-53 Rev 5 | Federal / Enterprise Security | Control family mapping for findings |
| ISO 27001:2022 | Information Security | Annex A clause mapping |
| CIS Controls v8 | Hardening / Remediation | Specific safeguard references |
| NIST AI RMF | AI Risk | AI/ML threat governance track |
| ISO 42001 | AI Management Systems | AI governance clause mapping |
| EU AI Act | AI Regulation | Compliance and conformity assessment |
| MITRE ATT&CK | Threat Intelligence | TTP mapping for threat actor activity |
| MITRE ATLAS | AI/ML Threats | Adversarial ML technique mapping |

---

## About the Author

**Blaise Kingko** — Senior Cloud GRC & Security Architect with 7+ years directing security strategy for $1B+ cloud portfolios.

Core expertise: AI Governance (ISO 42001, NIST AI RMF, EU AI Act) · Cloud Security Architecture (AWS, Azure, Zero Trust, CSPM) · Compliance-as-Code (Terraform, AWS Config) · Enterprise GRC (NIST 800-53, FedRAMP, SOC 2, ISO 27001)

Key outcomes: 40% reduction in IAM policy violations · 98% compliance baseline adherence · 60% reduction in manual audit toil · 45→14 day Time-to-Remediate improvement

📧 bkberri52@gmail.com · 🔗 [linkedin.com/in/berrikingko](https://linkedin.com/in/berrikingko)

---

*This repository is actively maintained. Content reflects current threat intelligence and framework guidance as of the date of each commit.*

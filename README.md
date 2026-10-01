# GRC Intelligence & Case Study Portfolio
### Blaise Kingko: Senior Cloud Security & GRC Architect

[![LinkedIn](https://img.shields.io/badge/LinkedIn-bk--lakeville-blue?style=flat&logo=linkedin)](https://linkedin.com/in/bk-lakeville)
[![Frameworks](https://img.shields.io/badge/Frameworks-NIST%20%7C%20ISO%20%7C%20CIS%20%7C%20EU%20AI%20Act-navy?style=flat)]()
[![Focus](https://img.shields.io/badge/Focus-Cloud%20GRC%20%7C%20AI%20Governance%20%7C%20Threat%20Intel-2E86C1?style=flat)]()

---

## Start Here

I run a weekly GRC intelligence sweep and publish the output here: case studies, a risk register, and an executive report. Every case follows the same six-file format and is mapped to framework controls (NIST, ISO, CIS, and for AI cases, the EU AI Act). New cases are added weekly. Three places to start:

- Control mapping: [AWS IAM multi-tenant batch](./Case-studies/Cloud-Security/2026-09-AWS-Bulletin-IAM-MultiTenant-Batch/04_Control_Mapping.md)
- Business-risk framing: [Cisco ISE authentication bypass](./Case-studies/Cloud-Security/2026-09-CISA-KEV-Cisco-ISE-AuthBypass/03_BIA.md)
- AI governance: [EU AI Act Article 50 enforcement](./Case-studies/AI-Governance/2026-08-EU-AI-Act-Transparency-Enforcement/04_Control_Mapping.md)

---

## What This Repository Is

This is a working GRC intelligence program, not a study guide.

Every file here reflects how I approach real-world governance, risk, and compliance work: structured analysis, framework-mapped findings, and outputs built for decision-makers, not just compliance checkboxes.

Ten years of enterprise GRC across FinTech, financial services, and healthcare taught me that the gap between a good security program and a reactive one is almost always an intelligence problem. Organizations that understand their risk posture in real time make better decisions. Those that find out during an audit don't.

This repository is where I apply that thinking continuously: tracking live threat intelligence, running risk assessments against the frameworks that matter, and producing executive-grade outputs that connect technical findings to business risk.

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

## Intelligence Program: How It Works

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

- **Source**: where the intelligence came from
- **Framework mapping**: which controls are implicated
- **Likelihood × Impact scoring**: structured 5×5 methodology
- **Inherent vs residual risk**: before and after controls
- **Remediation**: specific actions with CIS Control references
- **Status tracking**: Open / Mitigating / Closed / Accepted

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

1. **Incident Summary**: what happened and when
2. **Technical Analysis**: root cause, attack vector, affected systems
3. **Framework Impact**: which controls failed or were absent
4. **Risk Model Implications**: how this challenges existing risk assumptions
5. **AI / Emerging Threat Angle**: where applicable
6. **Recommended Controls**: specific, framework-referenced remediation
7. **Executive Summary**: board-level takeaway in plain language

### Published Case Studies

54 unique case studies published as of 2026-09-30, organized by threat category. Some are weekly batches that cover several related CVEs.

| Category | Case Studies | Frameworks |
|---|---|---|
| [IT-OT-Threats](./Case-studies/IT-OT-Threats) | 33 | NIST CSF, NIST 800-53, CIS Controls, IEC 62443 |
| [Cloud-Security](./Case-studies/Cloud-Security) | 21 | NIST CSF, NIST 800-53, CIS Control 7 |
| [AI-Governance](./Case-studies/AI-Governance) | 12 | NIST AI RMF, ISO 42001, EU AI Act |
| [Financial-Services](./Case-studies/Financial-Services) | 1 | NIST 800-53, GLBA, SOX, SEC Cybersecurity Rules |

*13 cases are intentionally cross-filed under two categories per the program's multi-category duplication policy, so the folder counts above add up to 67 while the unique count is 54. The cross-filed cases include Oracle PeopleSoft, LiteLLM AI Gateway, MSRC Patch Tuesday Wormable Kernel, Langflow, Cisco ISE, and the MCP server batches. Each one notes its dual filing in its own README. New case studies are added weekly as part of the intelligence monitoring cycle.*

<!-- Featured Case Studies — last manually reviewed: 2026-09-30 -->
### Featured Case Studies

| Case Study | Date | Threat Category | Frameworks |
|---|---|---|---|
| [NIST NVD: Six MCP Server and AI-Agent Tooling CVEs (CVSS 8.1 to 9.8)](./Case-studies/AI-Governance/2026-09-NIST-NVD-MCP-Server-TrustBoundary-Batch) | September 2026 | AI Governance, Agent Tooling Trust Boundaries | NIST AI RMF, ISO 42001, NIST CSF, NIST 800-53, MITRE ATLAS |
| [AWS Bulletin: SageMaker Python SDK Cleartext HMAC Key Exposure (CVE-2026-83551)](./Case-studies/AI-Governance/2026-09-AWS-Bulletin-SageMaker-HMACKeyExposure) | September 2026 | AI Governance, Multi-Tenant ML Platform | NIST AI RMF, ISO 42001, NIST CSF, NIST 800-53 |
| [EU AI Act: Article 50 Transparency Obligations Enter Active Enforcement](./Case-studies/AI-Governance/2026-08-EU-AI-Act-Transparency-Enforcement) | August 2026 | AI Governance, Regulatory | NIST AI RMF, ISO 42001, EU AI Act |
| [EU AI Act: High-Risk AI System Classification (Draft Guidelines)](./Case-studies/AI-Governance/2026-06-EU-AI-Act-HighRisk-Classification) | June 2026 | AI Governance, Regulatory | NIST AI RMF, ISO 42001, EU AI Act |
| [AWS Bulletin: TEAM Privilege Assignment and EKS Network Policy Agent Isolation Bypass](./Case-studies/Cloud-Security/2026-09-AWS-Bulletin-IAM-MultiTenant-Batch) | September 2026 | Cloud Security, IAM and Multi-Tenant Isolation | NIST CSF, NIST 800-53, ISO 27001, CIS Controls |
| [CISA KEV: Cisco ISE Unauthenticated Administrative Bypass (CVSS 10.0)](./Case-studies/Cloud-Security/2026-09-CISA-KEV-Cisco-ISE-AuthBypass) | September 2026 | Cloud Security, Identity Control Plane | NIST CSF, NIST 800-53, ISO 27001, CIS Controls |
| [MSRC: Azure Cosmos DB Cross-Tenant Escape (CVE-2026-66803)](./Case-studies/Cloud-Security/2026-08-MSRC-Azure-CosmosDB-CrossTenantEscape) | August 2026 | Cloud Security, Azure Platform Vulnerability | NIST CSF, NIST 800-53, ISO 27001, CIS Controls |
| [AWS Bulletin: "Copy.fail" / "DirtyFrag" Linux Kernel LPE Family](./Case-studies/Cloud-Security/2026-06-AWS-Bulletin-Linux-Kernel-CopyFail) | June 2026 | Cloud Security, Platform Vulnerability | NIST CSF, NIST 800-53, CIS Control 7 |

*Every case study is browsable in the [Case-studies](./Case-studies) folder by category.*

---

## Executive Reporting

Weekly intelligence runs produce a structured executive report containing:

- Key Risk Indicators (KRIs): current week vs prior week
- Top threats with business impact framing
- AI Governance Watch: regulatory and threat developments
- Compliance posture across all mapped frameworks
- Recommended executive actions with owners and timelines

Reports are written for a CISO or board audience, with technical findings translated into business risk language.

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

**Blaise Kingko**, Senior Cloud Security & GRC Architect with 10 years securing regulated environments across Tier-1 banking, fintech, and federal and healthcare consulting.

Core expertise: AI Governance (ISO 42001, NIST AI RMF, EU AI Act readiness) · Cloud Security Architecture (AWS, Azure, Zero Trust, CSPM) · Compliance-as-Code (Terraform, AWS Config) · Enterprise GRC (NIST 800-53, FedRAMP readiness, SOC 2, ISO 27001)

Key outcomes: 40% reduction in IAM policy violations across 500+ AWS accounts · 98% baseline adherence · 60% reduction in manual audit toil · critical time-to-remediate cut from 45 days to 14

bkberri52@gmail.com · [linkedin.com/in/bk-lakeville](https://linkedin.com/in/bk-lakeville)

---

*Updated weekly. Each case reflects threat intelligence and framework guidance as of its listed date. README last reviewed 2026-09-30.*

# Framework Reference Map
### Blaise Kingko — GRC Intelligence Program

This document maps every framework used in this GRC intelligence program to its domain, 
use case, and how it applies to the case studies and risk assessments in this repository.

---

## Framework Tracks

This program uses two parallel framework tracks depending on the threat category:

```
IT / OT / Cloud Threats          AI / ML Threats
─────────────────────            ───────────────────────
NIST CSF 2.0                     NIST AI RMF
    ↓                                ↓
ISO 27001:2022                   ISO 42001
    ↓                                ↓
NIST SP 800-53 Rev 5             EU AI Act
    ↓                                ↓
CIS Controls v8                  MITRE ATLAS
```

---

## IT / OT / Cloud Frameworks

### NIST Cybersecurity Framework 2.0 (NIST CSF 2.0)
| Field | Details |
|---|---|
| **Issuing Body** | National Institute of Standards and Technology (NIST) |
| **Current Version** | CSF 2.0 — Released February 2024 |
| **URL** | https://www.nist.gov/cyberframework |
| **Domain** | Enterprise cybersecurity risk management |
| **Structure** | 6 Functions: GOVERN, IDENTIFY, PROTECT, DETECT, RESPOND, RECOVER |
| **Use in This Program** | Primary mapping framework for all IT/OT and cloud threat findings |
| **Who Uses It** | Organizations of all sizes across all sectors — US and global |

**Key Change in CSF 2.0:** Added GOVERN as a new function, elevating cybersecurity to 
an organizational governance and risk management discipline — not just a technical one.

---

### NIST Special Publication 800-53 Rev 5
| Field | Details |
|---|---|
| **Issuing Body** | NIST |
| **Current Version** | Revision 5 — September 2020 |
| **URL** | https://csrc.nist.gov/publications/detail/sp/800-53/rev-5/final |
| **Domain** | Security and privacy controls for federal and enterprise systems |
| **Structure** | 20 control families, 1,000+ individual controls |
| **Use in This Program** | Specific control mapping for all findings and remediation recommendations |
| **Who Uses It** | Federal agencies (mandatory), financial services, healthcare, defense contractors |

**Key Control Families Referenced:**
- AC — Access Control
- AU — Audit and Accountability  
- CM — Configuration Management
- IA — Identification and Authentication
- IR — Incident Response
- RA — Risk Assessment
- SC — System and Communications Protection
- SI — System and Information Integrity
- SR — Supply Chain Risk Management

---

### ISO/IEC 27001:2022
| Field | Details |
|---|---|
| **Issuing Body** | International Organization for Standardization (ISO) |
| **Current Version** | ISO 27001:2022 — Updated October 2022 |
| **URL** | https://www.iso.org/standard/27001 |
| **Domain** | Information Security Management Systems (ISMS) |
| **Structure** | 10 clauses + Annex A (93 controls across 4 themes) |
| **Use in This Program** | Annex A control mapping for all findings |
| **Who Uses It** | Global organizations seeking certification — especially multinational, financial, technology |

**Annex A Themes:**
- Organizational Controls (A.5) — 37 controls
- People Controls (A.6) — 8 controls
- Physical Controls (A.7) — 14 controls
- Technological Controls (A.8) — 34 controls

---

### CIS Controls v8
| Field | Details |
|---|---|
| **Issuing Body** | Center for Internet Security (CIS) |
| **Current Version** | v8 — May 2021 |
| **URL** | https://www.cisecurity.org/controls |
| **Domain** | Prioritized cybersecurity best practices and safeguards |
| **Structure** | 18 controls with 153 safeguards, organized by Implementation Groups (IG1/2/3) |
| **Use in This Program** | Specific remediation safeguard references for all findings |
| **Who Uses It** | Organizations of all sizes — particularly useful for prioritizing remediation |

**Key Controls Referenced:**
- Control 1 — Inventory and Control of Enterprise Assets
- Control 2 — Inventory and Control of Software Assets
- Control 4 — Secure Configuration of Enterprise Assets
- Control 5 — Account Management
- Control 6 — Access Control Management
- Control 7 — Continuous Vulnerability Management
- Control 8 — Audit Log Management
- Control 12 — Network Infrastructure Management
- Control 13 — Network Monitoring and Defense
- Control 17 — Incident Response Management

---

### FedRAMP
| Field | Details |
|---|---|
| **Issuing Body** | General Services Administration (GSA) / Joint Authorization Board |
| **Current Version** | FedRAMP Rev 5 — aligned to NIST 800-53 Rev 5 |
| **URL** | https://www.fedramp.gov |
| **Domain** | Cloud service security authorization for US federal government |
| **Structure** | Low / Moderate / High impact baselines derived from NIST 800-53 |
| **Use in This Program** | Referenced for cloud findings affecting federal or regulated environments |
| **Who Uses It** | Cloud service providers seeking federal authorization; federal agencies |

---

### CMMC 2.0
| Field | Details |
|---|---|
| **Issuing Body** | US Department of Defense (DoD) |
| **Current Version** | CMMC 2.0 — Final rule November 2024 |
| **URL** | https://www.acq.osd.mil/cmmc |
| **Domain** | Cybersecurity maturity for defense industrial base (DIB) contractors |
| **Structure** | 3 levels — Foundational (L1), Advanced (L2), Expert (L3) |
| **Use in This Program** | Referenced for findings affecting defense contractors or OT environments |
| **Who Uses It** | DoD contractors and subcontractors handling CUI |

---

### IEC 62443
| Field | Details |
|---|---|
| **Issuing Body** | International Electrotechnical Commission (IEC) |
| **Current Version** | Multiple parts — ongoing updates |
| **URL** | https://www.iec.ch/iec62443 |
| **Domain** | Industrial Automation and Control Systems (IACS) security |
| **Structure** | Zone/Conduit model, Security Levels (SL 1–4), Component/System/Program requirements |
| **Use in This Program** | Referenced in IT/OT case studies for OT-specific control requirements |
| **Who Uses It** | Industrial manufacturers, energy, water, transportation, critical infrastructure |

---

## AI / ML Governance Frameworks

### NIST AI Risk Management Framework (NIST AI RMF)
| Field | Details |
|---|---|
| **Issuing Body** | NIST |
| **Current Version** | AI RMF 1.0 — January 2023 + Generative AI Profile (NIST AI 600-1) |
| **URL** | https://www.nist.gov/artificial-intelligence |
| **Domain** | AI risk identification, assessment, and management |
| **Structure** | 4 functions: GOVERN, MAP, MEASURE, MANAGE |
| **Use in This Program** | Primary mapping framework for all AI/ML threat findings |
| **Who Uses It** | Organizations developing or deploying AI systems — US focus, global adoption |

**Core Functions:**
- **GOVERN** — Establish organizational AI risk culture, policies, and accountability
- **MAP** — Identify and categorize AI risks in context
- **MEASURE** — Analyze and assess AI risks quantitatively and qualitatively
- **MANAGE** — Prioritize and treat AI risks with appropriate responses

---

### ISO/IEC 42001:2023
| Field | Details |
|---|---|
| **Issuing Body** | ISO/IEC |
| **Current Version** | ISO 42001:2023 — December 2023 |
| **URL** | https://www.iso.org/standard/81230.html |
| **Domain** | Artificial Intelligence Management Systems (AIMS) |
| **Structure** | 10 clauses aligned to ISO high-level structure (same as ISO 27001) |
| **Use in This Program** | Clause-level mapping for AI governance findings |
| **Who Uses It** | Organizations seeking AI management system certification — global applicability |

**Key Clauses:**
- 4.1 — Understanding the organization and its context
- 6.1.2 — AI risk assessment
- 6.1.3 — AI risk treatment
- 8.4 — AI system impact assessment
- 9.1 — Monitoring, measurement, analysis, and evaluation

---

### EU AI Act
| Field | Details |
|---|---|
| **Issuing Body** | European Parliament and Council |
| **Current Version** | Regulation (EU) 2024/1689 — Entered into force August 2024 |
| **URL** | https://artificialintelligenceact.eu |
| **Domain** | AI regulation and governance — risk-based approach |
| **Structure** | Risk tiers: Unacceptable / High / Limited / Minimal risk |
| **Use in This Program** | Regulatory mapping for AI findings — especially high-risk system classification |
| **Who Uses It** | Any organization deploying AI systems affecting EU residents |

**Key Timelines:**
- February 2025 — Prohibited AI practices banned
- August 2025 — GPAI model obligations apply
- August 2026 — High-risk AI system obligations fully apply

**High-Risk Categories (Annex III):**
Critical infrastructure, education, employment, essential services, law enforcement, 
migration, administration of justice, democratic processes

---

### MITRE ATLAS
| Field | Details |
|---|---|
| **Issuing Body** | MITRE Corporation |
| **Current Version** | Ongoing — community maintained |
| **URL** | https://atlas.mitre.org |
| **Domain** | Adversarial Tactics, Techniques, and Case Studies for AI/ML systems |
| **Structure** | Tactics and techniques mirroring MITRE ATT&CK but for ML attack surface |
| **Use in This Program** | TTP mapping for AI/ML-specific threat case studies |
| **Who Uses It** | AI security researchers, red teams, AI governance teams |

**Key Tactics:**
- Reconnaissance — Learning about the ML system
- ML Attack Staging — Preparing adversarial attacks
- ML Model Access — Gaining access to model internals
- Exfiltration — Extracting training data or model weights
- Impact — Manipulating model behavior

---

## Threat Intelligence Frameworks

### MITRE ATT&CK
| Field | Details |
|---|---|
| **Issuing Body** | MITRE Corporation |
| **Current Version** | v15 — ongoing updates |
| **URL** | https://attack.mitre.org |
| **Domain** | Adversary tactics, techniques, and procedures (TTPs) |
| **Structure** | Enterprise / Mobile / ICS matrices with tactics and techniques |
| **Use in This Program** | TTP mapping in all case study attack chain sections |
| **Who Uses It** | SOC teams, threat hunters, red teams, GRC analysts globally |

---

## Financial Services Frameworks

### Key Regulatory References

| Regulation | Jurisdiction | Domain | URL |
|---|---|---|---|
| Gramm-Leach-Bliley Act (GLBA) | US Federal | Financial data privacy and safeguards | https://www.ftc.gov/glba |
| SOX Section 404 | US Federal | Internal controls over financial reporting | https://pcaobus.org |
| PCI-DSS v4.0 | Global | Payment card data security | https://www.pcisecuritystandards.org |
| NYDFS Part 500 | New York State | Cybersecurity for financial services | https://www.dfs.ny.gov |
| SEC Cybersecurity Rules | US Federal | Material incident disclosure — 4-day rule | https://www.sec.gov |
| DORA | European Union | Digital operational resilience for finance | https://www.eba.europa.eu/dora |
| OCC Guidelines | US Federal | Safety and soundness for national banks | https://www.occ.gov |
| Federal Reserve SR 11-7 | US Federal | Model risk management | https://www.federalreserve.gov |
| FFIEC CAT | US Federal | Cybersecurity assessment for financial institutions | https://www.ffiec.gov |

---

## Payment & Retail Compliance Frameworks

### PCI-DSS v4.0
| Field | Details |
|---|---|
| **Issuing Body** | PCI Security Standards Council |
| **Current Version** | v4.0 — fully effective March 2025 |
| **URL** | https://www.pcisecuritystandards.org |
| **Domain** | Payment card data security for any organization storing, processing, or transmitting cardholder data |
| **Structure** | 12 core requirements organized into 6 control objectives |
| **Use in This Program** | Cross-referenced for cloud/e-commerce findings that intersect with payment-card-data scope |
| **Who Uses It** | Merchants, payment processors, service providers, and any entity in the card-payment ecosystem |

**Key Requirements Referenced:**
- Requirement 6.3.3 — Patch and update critical/high-severity vulnerabilities within defined timeframes
- Requirement 11.3 — Perform internal and external vulnerability scanning

**Added to this program:** 2026-06-08 — first referenced in the *2026-06-CISA-KEV-Magento-Mirasvit* case study (Cloud-Security), where an actively exploited unauthenticated RCE in a Magento/Adobe Commerce extension placed payment-card-scoped infrastructure at risk. PCI-DSS was mapped alongside the standard NIST/ISO/CIS stack to demonstrate that e-commerce-platform findings carry payment-industry compliance obligations the core IT/OT framework track does not capture on its own — and to provide audit-ready evidence for any QSA inquiry into the incident-response and patch-management timeline.

---

## Framework Relationship Map

```
GOVERNANCE LAYER
─────────────────────────────────────────────────────────
NIST CSF 2.0 (GOVERN)  ←→  ISO 27001 (Clause 5–6)
NIST AI RMF (GOVERN)   ←→  ISO 42001 (Clause 5–6)
EU AI Act               ←→  ISO 42001 (Conformity)

CONTROL LAYER
─────────────────────────────────────────────────────────
NIST 800-53 Rev 5  →  Specific controls for findings
CIS Controls v8    →  Prioritized remediation safeguards
IEC 62443          →  OT/ICS-specific controls

THREAT INTELLIGENCE LAYER
─────────────────────────────────────────────────────────
MITRE ATT&CK  →  IT/OT/Cloud TTP mapping
MITRE ATLAS   →  AI/ML TTP mapping
CISA KEV      →  Actively exploited vulnerabilities
```

---

*Framework Reference Map v1.0 — Blaise Kingko GRC Intelligence Program*  
*Last Updated: May 2026*

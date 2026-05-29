# [INCIDENT TITLE] — Financial Services GRC Case Study
> **Example title format:** `SEC Cybersecurity Disclosure Failure — Governance and Regulatory Risk Analysis`

---

## Case Study Metadata

| Field | Details |
|---|---|
| **Case Study ID** | CS-FIN-[YYYY-MM-###] |
| **Date Published** | [YYYY-MM-DD] |
| **Incident Date** | [YYYY-MM-DD or Month YYYY] |
| **Author** | Blaise Kingko |
| **Threat Category** | Financial Services — [Fraud / Ransomware / Data Breach / Regulatory / Third-Party / Insider Threat] |
| **CVE / Advisory ID** | [If applicable] |
| **Affected Institution Type** | [Tier-1 Bank / Regional Bank / FinTech / Insurance / Investment Firm / Payment Processor] |
| **Regulatory Bodies Involved** | [OCC / Federal Reserve / SEC / FINRA / CFPB / State Regulator] |
| **Intelligence Source** | [Regulatory filing / CISA / News / SEC disclosure / OCC enforcement action] |
| **Financial Impact** | [$X million fine / $X million operational loss / Undisclosed] |

---

## 1. Incident Summary

### 1.1 What Happened
*2–3 sentences. State the facts: what institution, what incident, what regulatory or financial impact. Write for a board-level reader.*

[Insert plain-language summary here]

### 1.2 Why It Matters
*1–2 sentences. Financial services incidents carry regulatory, reputational, and systemic risk implications that other sectors don't. Frame those dimensions here.*

[Insert business impact framing here]

### 1.3 Institutional Context

| Field | Details |
|---|---|
| **Institution Type** | [Bank / FinTech / Insurance / Investment / Payment] |
| **Asset Size / Revenue** | [$X billion AUM / revenue — if disclosed] |
| **Regulatory Classification** | [Systemically important / Regional / Community / Non-bank] |
| **Primary Regulator** | [OCC / Federal Reserve / SEC / State DFS / etc.] |
| **Key Regulations Implicated** | [Gramm-Leach-Bliley / SOX / DORA / PCI-DSS / NYDFS Part 500 / etc.] |
| **Customer Data Affected** | [PII / Financial records / Account credentials / Payment data] |

---

## 2. Technical Analysis

### 2.1 Incident Details

| Field | Details |
|---|---|
| **Incident Type** | [Ransomware / Phishing / Insider / Third-party / API abuse / Social engineering / Regulatory violation] |
| **Initial Access Vector** | [Phishing / Credential theft / Third-party / Unpatched vuln / Insider] |
| **Systems Affected** | [Core banking / Payment rails / Trading systems / Customer portal / Back office] |
| **Data Compromised** | [Type, volume, and sensitivity] |
| **Duration** | [How long before detection and containment] |
| **Detection Method** | [Internal SOC / External notification / Regulatory exam / Customer report] |

### 2.2 Attack Chain
*Map to MITRE ATT&CK Financial Services techniques where applicable.*

1. **Initial Access** — [Entry vector — ATT&CK T####]
2. **Execution / Persistence** — [How attacker maintained foothold — ATT&CK T####]
3. **Lateral Movement** — [How attacker moved through the environment — ATT&CK T####]
4. **Impact** — [Data exfiltration / encryption / fraud / regulatory trigger — ATT&CK T####]

### 2.3 Third-Party Risk Analysis
*Financial services incidents frequently involve third-party or supply chain vectors. Complete this section if applicable.*

- **Third party involved:** [Vendor / partner / processor / cloud provider]
- **Contract coverage:** [Did the contract require adequate security controls?]
- **Due diligence gap:** [Was vendor risk assessed — how and when?]
- **Access scope:** [What access did the third party have to systems and data?]
- **Notification timeline:** [How long before the third party notified the institution?]

### 2.4 Root Cause
*What is the underlying governance, architectural, or process failure?*

[Insert root cause — be specific and connect to both the technical failure and the governance failure that allowed it. Financial services root causes often involve both.]

---

## 3. Framework Impact Analysis

### 3.1 NIST CSF 2.0 Mapping

| CSF Function | Subcategory | Gap or Finding |
|---|---|---|
| **GOVERN** | [e.g., GV.SC-07 — Supply chain risk managed] | [Third-party oversight gap] |
| **IDENTIFY** | [e.g., ID.RA-01 — Vulnerabilities in assets identified] | [Risk assessment gap] |
| **PROTECT** | [e.g., PR.AA-03 — Identities managed] | [Access control gap] |
| **DETECT** | [e.g., DE.AE-04 — Impact of events determined] | [Detection and triage gap] |
| **RESPOND** | [e.g., RS.CO-02 — Incidents reported per regulatory requirements] | [Notification gap] |
| **RECOVER** | [e.g., RC.CO-03 — Recovery activities communicated] | [Recovery communication gap] |

### 3.2 NIST SP 800-53 Control Mapping

| Control Family | Control ID | Control Name | Finding |
|---|---|---|---|
| Access Control | AC-2 | Account Management | [Finding] |
| Audit & Accountability | AU-6 | Audit Record Review | [Finding] |
| Incident Response | IR-6 | Incident Reporting | [Finding] |
| Risk Assessment | RA-3 | Risk Assessment | [Finding] |
| Supply Chain Risk | SR-6 | Supplier Assessments and Reviews | [Finding] |
| System & Comms Protection | SC-7 | Boundary Protection | [Finding] |

### 3.3 ISO 27001:2022 Mapping

| Annex A Clause | Control | Finding |
|---|---|---|
| A.5.19 | Information security in supplier relationships | [Finding] |
| A.5.23 | Information security for use of cloud services | [Finding] |
| A.5.24 | Information security incident management planning | [Finding] |
| A.5.26 | Response to information security incidents | [Finding] |
| A.8.12 | Data leakage prevention | [Finding] |

### 3.4 Financial Services Regulatory Mapping

| Regulation / Standard | Requirement | Finding |
|---|---|---|
| **Gramm-Leach-Bliley Act (GLBA)** | Safeguards Rule — administrative, technical, and physical safeguards | [Finding] |
| **SOX Section 404** | Internal controls over financial reporting | [Finding — if publicly traded] |
| **PCI-DSS v4.0** | Cardholder data environment protection | [Finding — if payment data involved] |
| **NYDFS Part 500** | Cybersecurity requirements for financial services | [Finding — if NY-regulated] |
| **SEC Cybersecurity Rules** | Disclosure of material cybersecurity incidents within 4 days | [Finding — if SEC-registered] |
| **DORA (EU)** | Digital operational resilience for financial entities | [Finding — if EU operations] |
| **OCC Guidelines** | Safety and soundness — technology risk management | [Finding — if OCC-regulated] |
| **Federal Reserve SR 11-7** | Model risk management guidance | [Finding — if model risk involved] |

### 3.5 CIS Controls v8 Mapping

| CIS Control | Safeguard | Finding |
|---|---|---|
| Control 3 | Data Protection | [Finding] |
| Control 6 | Access Control Management | [Finding] |
| Control 14 | Security Awareness | [Finding] |
| Control 15 | Service Provider Management | [Finding] |
| Control 17 | Incident Response Management | [Finding] |

---

## 4. Risk Assessment

### 4.1 Risk Scoring

| Dimension | Score | Rationale |
|---|---|---|
| **Likelihood** | [1–5] | [Threat actor sophistication, targeting pattern, institutional vulnerability profile] |
| **Impact** | [1–5] | [Financial loss, regulatory fine, reputational damage, systemic risk] |
| **Risk Score** | [L × I] | [Calculated] |
| **Risk Rating** | [Critical / High / Medium / Low] | [20-25=Critical, 10-19=High, 5-9=Medium, 1-4=Low] |

### 4.2 Financial Services Risk Dimensions

| Risk Dimension | Rating | Notes |
|---|---|---|
| **Regulatory Fine Exposure** | [Critical/High/Medium/Low] | [Estimated regulatory penalty range] |
| **Operational Disruption** | [Critical/High/Medium/Low] | [Impact on revenue-generating systems] |
| **Customer Trust** | [Critical/High/Medium/Low] | [Reputational and customer attrition risk] |
| **Systemic Risk** | [Critical/High/Medium/Low] | [Contagion risk to financial system] |
| **Litigation Exposure** | [Critical/High/Medium/Low] | [Class action or regulatory lawsuit risk] |
| **Third-Party Concentration** | [Critical/High/Medium/Low] | [Single point of failure in vendor dependencies] |

### 4.3 Regulatory Timeline Risk
*Financial services regulators impose strict notification timelines. Document the regulatory clock:*

| Regulator | Notification Requirement | Timeline Met? | Notes |
|---|---|---|---|
| SEC | Material incident — 8-K within 4 business days | [Yes/No] | [Details] |
| OCC | Safety and soundness notification | [Yes/No] | [Details] |
| NYDFS | 72-hour notification | [Yes/No] | [Details] |
| Federal Reserve | As required by supervisory agreement | [Yes/No] | [Details] |

---

## 5. Risk Model Implications

### 5.1 How This Challenges Traditional Risk Models
*Financial services have the most mature regulatory risk frameworks in any sector — yet incidents still occur. Explain what this incident reveals about the limits of even mature GRC programs.*

[Insert analysis — 2–4 paragraphs. Address: regulatory compliance ≠ security, third-party risk concentration, model risk in automated decision systems, the tension between operational speed and security controls in financial services]

### 5.2 Where Traditional Controls Break Down

- **[Control assumption 1]:** [Why it failed — e.g., "Annual vendor assessments don't detect security posture changes between reviews"]
- **[Control assumption 2]:** [Why it failed]
- **[Control assumption 3]:** [Why it failed]

### 5.3 Regulatory Pattern
*Connect this incident to the broader regulatory enforcement trend.*

[Insert pattern — e.g., increasing SEC enforcement on disclosure timing, OCC focus on third-party concentration risk, NYDFS expanding scope of Part 500, DORA creating new operational resilience requirements for EU financial entities]

---

## 6. Recommended Controls & Remediation

### 6.1 Immediate Actions (0–7 Days)

| Action | Owner | Framework Reference | Priority |
|---|---|---|---|
| [Contain the incident — isolate affected systems] | CISO / SOC | NIST 800-53: IR-4 \| NIST CSF: RS.MI | 🔴 Critical |
| [Notify regulators per applicable timelines] | Legal / Compliance | SEC Rule / NYDFS Part 500 / OCC | 🔴 Critical |
| [Preserve all audit logs — do not alter or delete] | IT / Legal | NIST 800-53: AU-9 | 🔴 Critical |

### 6.2 Short-Term Actions (8–30 Days)

| Action | Owner | Framework Reference | Priority |
|---|---|---|---|
| [Conduct root cause analysis and document findings] | GRC / Security | NIST 800-53: IR-8 \| NIST CSF: RS.AN | 🟠 High |
| [Review and tighten third-party access and contracts] | TPRM / Legal | NIST 800-53: SR-6 \| GLBA Safeguards | 🟠 High |
| [Update incident response plan to reflect lessons learned] | GRC | NIST 800-53: IR-8 | 🟡 Medium |

### 6.3 Strategic Recommendations

| Recommendation | Framework Reference | Business Rationale |
|---|---|---|
| [Continuous third-party monitoring vs point-in-time assessments] | NIST 800-53: SR-6 \| DORA: Article 28 | [Third-party concentration is primary risk vector] |
| [Implement automated regulatory notification workflows] | SEC Rule \| NYDFS Part 500 | [4-day SEC deadline requires pre-built process] |
| [Zero Trust architecture for core banking access] | NIST 800-207 \| OCC Guidelines | [Lateral movement prevention in high-value environments] |

### 6.4 Financial Services Specific Controls
- **Model Risk Management (MRM):** Validate all automated decision models per SR 11-7 — document assumptions, limitations, and ongoing monitoring
- **Operational Resilience:** Test recovery procedures against regulatory RTO/RPO requirements — not just technical capability
- **Regulatory Notification Runbook:** Pre-built playbook for each regulator with notification templates, contact lists, and timeline tracking
- **Third-Party Concentration Risk:** Map critical vendor dependencies — identify single points of failure before an incident creates them
- **Insider Threat Program:** Financial services are high-value targets for insider fraud — behavioral analytics and privileged access monitoring are essential

---

## 7. Executive Summary

*Write last. Maximum one page. Plain English. Board-level reader. Financial services boards are more regulatory-aware than most — connect directly to regulator expectations and enforcement trends.*

### The Situation
[What happened, what institution type, what regulatory and financial exposure was triggered]

### The Regulatory Risk
[Which regulators are involved, what enforcement actions are possible, what precedent cases show]

### The Business Risk
[Revenue impact, customer attrition, reputational damage, systemic risk if applicable]

### What We Are Doing
[Immediate containment, regulatory notification, remediation actions — specific]

### What We Need From Leadership
[Board-level decisions: disclosure strategy, regulatory response posture, resource allocation for remediation]

---

## 8. References & Sources

| Source | URL | Date Accessed |
|---|---|---|
| SEC Cybersecurity Disclosure Rules | https://www.sec.gov/rules/final/2023/33-11216.pdf | [Date] |
| OCC Cybersecurity Guidelines | https://www.occ.gov/topics/supervison-and-examination/cybersecurity | [Date] |
| NYDFS Part 500 | https://www.dfs.ny.gov/industry_guidance/cybersecurity | [Date] |
| DORA Regulation | https://www.eba.europa.eu/regulation-and-policy/dora | [Date] |
| FFIEC Cybersecurity Assessment | https://www.ffiec.gov/cyberassessmenttool.htm | [Date] |
| [Incident source / regulatory filing] | [URL] | [Date] |

---

## 9. Revision History

| Version | Date | Author | Changes |
|---|---|---|---|
| 1.0 | [YYYY-MM-DD] | Blaise Kingko | Initial publication |

---

*Case Study Template v1.0 — Blaise Kingko GRC Intelligence Program*
*Framework References: NIST CSF 2.0 | NIST SP 800-53 Rev 5 | ISO 27001:2022 | CIS Controls v8 | GLBA | SOX | PCI-DSS | NYDFS Part 500 | SEC Cybersecurity Rules | DORA*

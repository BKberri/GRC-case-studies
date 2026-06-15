# [INCIDENT TITLE] — IT/OT Infrastructure Case Study
> **Example title format:** `CISA KEV — Siemens S7 PLC Remote Code Execution | ICS/SCADA Risk Analysis`

---

## Case Study Metadata

| Field | Details |
|---|---|
| **Case Study ID** | CS-ITOT-[YYYY-MM-###] |
| **Date Published** | [YYYY-MM-DD] |
| **Incident Date** | [YYYY-MM-DD or Month YYYY] |
| **Author** | Blaise Kingko |
| **Threat Category** | IT/OT — [Network / ICS / SCADA / Endpoint / Industrial] |
| **CVE / Advisory ID** | [CVE-XXXX-XXXXX or CISA Advisory AA-XX-XXX] |
| **CVSS Score** | [X.X — Critical / High / Medium] |
| **Affected Vendor** | [Vendor name] |
| **Affected Product** | [Product name and version] |
| **Intelligence Source** | [CISA KEV / US-CERT / NIST NVD / Internal] |
| **Exploitation Status** | [Actively exploited / PoC available / No known exploit] |

---

## 1. Incident Summary

### 1.1 What Happened
*2–3 sentences. State the facts: what vulnerability or incident, which systems, what impact. No jargon in this section — write for a non-technical reader.*

[Insert plain-language summary here]

### 1.2 Why It Matters
*1–2 sentences connecting this incident to broader risk. Why should a risk leader or CISO care about this specific event?*

[Insert business impact framing here]

### 1.3 Affected Environments
- **IT Systems:** [List affected IT components]
- **OT/ICS Systems:** [List affected OT/ICS/SCADA components]
- **Industries at Risk:** [Manufacturing / Energy / Water / Transportation / Healthcare / etc.]
- **Geographic Scope:** [Global / Regional / Sector-specific]

---

## 2. Technical Analysis

### 2.1 Vulnerability Details
| Field | Details |
|---|---|
| **Vulnerability Type** | [RCE / Privilege Escalation / Auth Bypass / DoS / etc.] |
| **Attack Vector** | [Network / Adjacent / Local / Physical] |
| **Attack Complexity** | [Low / Medium / High] |
| **Privileges Required** | [None / Low / High] |
| **User Interaction** | [None / Required] |
| **Scope** | [Unchanged / Changed] |
| **Confidentiality Impact** | [None / Low / High] |
| **Integrity Impact** | [None / Low / High] |
| **Availability Impact** | [None / Low / High] |

### 2.2 Attack Chain
*Walk through how an attacker would exploit this vulnerability step by step. Reference MITRE ATT&CK technique IDs where applicable.*

1. **Initial Access** — [How attacker gains entry — ATT&CK T####]
2. **Execution** — [How the exploit runs — ATT&CK T####]
3. **Persistence** (if applicable) — [How attacker maintains access — ATT&CK T####]
4. **Impact** — [What the attacker achieves — ATT&CK T####]

### 2.3 IT/OT Convergence Risk
*This section is specific to IT/OT case studies. Explain how this vulnerability bridges the IT and OT environments and why that convergence creates elevated risk.*

[Insert IT/OT convergence analysis here]

### 2.4 Root Cause
*What is the underlying architectural or process failure that allowed this vulnerability to exist or be exploitable?*

[Insert root cause analysis here]

---

## 3. Framework Impact Analysis

### 3.1 NIST CSF 2.0 Mapping

| CSF Function | Subcategory | Gap or Finding |
|---|---|---|
| **GOVERN** | [e.g., GV.OC-01] | [What governance gap does this expose?] |
| **IDENTIFY** | [e.g., ID.AM-02] | [What asset management gap?] |
| **PROTECT** | [e.g., PR.PS-04] | [What protection control failed?] |
| **DETECT** | [e.g., DE.CM-01] | [What detection gap?] |
| **RESPOND** | [e.g., RS.MI-02] | [What response gap?] |
| **RECOVER** | [e.g., RC.RP-01] | [What recovery gap?] |

### 3.2 NIST SP 800-53 Control Mapping

| Control Family | Control ID | Control Name | Finding |
|---|---|---|---|
| Access Control | AC-[X] | [Control name] | [How this control failed or was absent] |
| System Integrity | SI-[X] | [Control name] | [Finding] |
| Configuration Mgmt | CM-[X] | [Control name] | [Finding] |
| Incident Response | IR-[X] | [Control name] | [Finding] |
| Risk Assessment | RA-[X] | [Control name] | [Finding] |

### 3.3 ISO 27001:2022 Mapping

| Annex A Clause | Control | Finding |
|---|---|---|
| A.8.8 | Management of technical vulnerabilities | [Finding] |
| A.8.20 | Networks security | [Finding] |
| A.5.37 | Documented operating procedures | [Finding] |
| [Add others] | [Control name] | [Finding] |

### 3.4 CIS Controls v8 Mapping

| CIS Control | Safeguard | Finding / Remediation |
|---|---|---|
| Control 7 | Continuous Vulnerability Management | [Finding] |
| Control 12 | Network Infrastructure Management | [Finding] |
| Control 13 | Network Monitoring and Defense | [Finding] |
| [Add others] | [Safeguard name] | [Finding] |

---

## 4. Risk Assessment

### 4.1 Risk Scoring

| Dimension | Score | Rationale |
|---|---|---|
| **Likelihood** | [1–5] | [Why this score — exploitation status, attacker capability, prevalence] |
| **Impact** | [1–5] | [Why this score — data sensitivity, operational impact, recovery complexity] |
| **Risk Score** | [L × I] | [Calculated score] |
| **Risk Rating** | [Critical / High / Medium / Low] | [Based on score: 20-25=Critical, 10-19=High, 5-9=Medium, 1-4=Low] |

### 4.2 Inherent vs Residual Risk

| Risk State | Rating | Notes |
|---|---|---|
| **Inherent Risk** | [Rating without controls] | [What the risk looks like with no controls in place] |
| **Residual Risk** | [Rating with current controls] | [What the risk looks like after applying existing controls] |
| **Target Residual Risk** | [Target rating after remediation] | [What risk level is acceptable after full remediation] |

### 4.3 IT/OT Specific Risk Factors
*Factors that elevate risk specifically in IT/OT convergence environments:*

- [ ] Legacy OT systems with no patch support
- [ ] Air gap assumption violated by network connectivity
- [ ] Safety system (SIS) adjacent to affected system
- [ ] Single point of failure in critical process
- [ ] Long patch cycle due to operational continuity requirements
- [ ] No network segmentation between IT and OT zones
- [ ] Remote access enabled on OT systems

---

## 5. Risk Model Implications

### 5.1 How This Challenges Traditional Risk Models
*This is the analytical core of the case study. Explain specifically how this incident exposes gaps in conventional GRC thinking.*

[Insert analysis — 2–4 paragraphs. Be specific. Reference the Purdue Model, IEC 62443, or other OT security frameworks where applicable.]

### 5.2 Where Traditional Controls Break Down
*What controls organizations typically rely on that this incident demonstrates are insufficient?*

- **[Control assumption 1]:** [Why it fails in this scenario]
- **[Control assumption 2]:** [Why it fails]
- **[Control assumption 3]:** [Why it fails]

### 5.3 Emerging Risk Pattern
*Is this incident part of a broader pattern? Connect it to the threat landscape.*

[Insert pattern analysis — e.g., increasing targeting of ICS by nation-state actors, growing IT/OT convergence risk, supply chain vectors into OT environments]

---

## 6. Recommended Controls & Remediation

### 6.1 Immediate Actions (0–7 Days)

| Action | Owner | Framework Reference | Priority |
|---|---|---|---|
| [Specific action — e.g., Apply vendor patch X to affected systems] | [CISO / SOC / OT Team] | NIST 800-53: SI-2 \| CIS Control 7.4 | 🔴 Critical |
| [Specific action] | [Owner] | [Framework ref] | 🔴 Critical |
| [Specific action] | [Owner] | [Framework ref] | 🟠 High |

### 6.2 Short-Term Actions (8–30 Days)

| Action | Owner | Framework Reference | Priority |
|---|---|---|---|
| [Specific action] | [Owner] | [Framework ref] | 🟠 High |
| [Specific action] | [Owner] | [Framework ref] | 🟡 Medium |

### 6.3 Strategic Recommendations (30–90 Days)

| Recommendation | Framework Reference | Business Rationale |
|---|---|---|
| [Strategic architecture or program change] | [Framework ref] | [Why this matters beyond this incident] |
| [Recommendation] | [Framework ref] | [Rationale] |

### 6.4 OT-Specific Controls
*Controls specifically relevant to operational technology environments:*

- **Network Segmentation:** Implement DMZ between IT and OT zones per IEC 62443 Zone/Conduit model
- **Unidirectional Gateways:** Deploy data diodes for one-way data flow from OT to IT where bidirectional is not required
- **OT Asset Inventory:** Maintain real-time OT asset inventory using passive monitoring (active scanning disrupts OT protocols)
- **Patch Management:** Develop OT-specific patch process accounting for operational windows and vendor approval requirements
- **Incident Response:** Maintain separate OT-specific IR playbook with operational continuity procedures

---

## 7. Executive Summary

*Write this section last. Maximum one page. Plain English — no technical jargon. Assume the reader is a board member or C-suite executive with no security background.*

### The Situation
[2–3 sentences: What happened, what systems are affected, what is the business risk]

### The Risk to Us
[2–3 sentences: Why this matters specifically to the organization — revenue, operations, safety, regulatory]

### What We Are Doing
[2–3 sentences: Immediate actions taken or recommended — specific, not vague]

### What We Need From Leadership
[1–2 sentences: Any decisions, resources, or escalations required from the executive team]

---

## 8. References & Sources

| Source | URL | Date Accessed |
|---|---|---|
| CISA KEV Catalog | https://www.cisa.gov/known-exploited-vulnerabilities-catalog | [Date] |
| NIST NVD | https://nvd.nist.gov/vuln/detail/[CVE-ID] | [Date] |
| Vendor Advisory | [URL] | [Date] |
| MITRE ATT&CK | https://attack.mitre.org/techniques/[T####] | [Date] |
| [Additional source] | [URL] | [Date] |

---

## 9. Revision History

| Version | Date | Author | Changes |
|---|---|---|---|
| 1.0 | [YYYY-MM-DD] | Blaise Kingko | Initial publication |
| [X.X] | [Date] | [Author] | [What changed] |

---

*Case Study Template v1.0 — Blaise Kingko GRC Intelligence Program*
*Framework References: NIST CSF 2.0 | NIST SP 800-53 Rev 5 | ISO 27001:2022 | CIS Controls v8 | IEC 62443*

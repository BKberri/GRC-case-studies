# Risk Assessment
## Case: CVE-2026-35273 — Oracle PeopleSoft Enterprise PeopleTools Unauthenticated RCE
**Date:** 2026-06-15 | **Analyst:** Blaise Kingko | **Classification:** Critical

---

## 1. Risk Identification

| Field | Details |
|---|---|
| **Risk ID** | RR-011 |
| **CVE / Advisory ID** | CVE-2026-35273 |
| **Threat Category** | IT-OT-Threats — Enterprise Application Unauthenticated RCE |
| **Affected Asset** | Oracle PeopleSoft ERP (HR, Finance, Student Admin environments) |
| **Affected System** | PeopleTools 8.61, PeopleTools 8.62 (EMHub component) |
| **Threat Actor** | UNC6240 (ShinyHunters) — financially motivated, extortion-focused |
| **Attack Vector** | Network — unauthenticated, no user interaction required |
| **CVSS v3.1 Score** | 9.8 Critical |

---

## 2. Likelihood Assessment

| Factor | Rating | Rationale |
|---|---|---|
| **Likelihood Score** | **5 / 5** | Actively exploited as zero-day from May 27 through June 9, 2026. Exploit code confirmed in use by UNC6240. CVSS network-exploitable, no authentication needed. |
| **Exploit Availability** | Active exploitation (no public PoC required — actor has working exploit) | UNC6240 operated with weaponized exploit pre-disclosure |
| **Attack Complexity** | Low | No special conditions, no privileges, no user interaction |
| **Threat Actor Capability** | High | ShinyHunters is a mature financially motivated group with demonstrated capability |

---

## 3. Impact Assessment

| Factor | Rating | Rationale |
|---|---|---|
| **Impact Score** | **5 / 5** | Full server compromise. PeopleSoft hosts HR data (SSNs, salary, benefits), finance data, student records, and payroll — among the most sensitive data categories. RCE enables data exfiltration, ransomware deployment, and supply chain pivot. |
| **Data Sensitivity** | Critical — PII, financial data, student records, regulated data (FERPA, GLBA, HIPAA depending on sector) | |
| **Business Impact** | Operational disruption, regulatory exposure, reputational damage, extortion payment pressure | |
| **Lateral Movement Risk** | High — PeopleSoft typically has privileged database access and integrations with HR/payroll systems | |

---

## 4. Risk Scoring

| Metric | Value |
|---|---|
| **Likelihood (1–5)** | 5 |
| **Impact (1–5)** | 5 |
| **Risk Score** | 25 |
| **Risk Rating** | **Critical** |
| **Inherent Risk** | Critical |

---

## 5. Existing Controls

| Control | Status | Effectiveness |
|---|---|---|
| Network perimeter firewall | In place | Partial — many orgs expose PeopleSoft portals to internet or partner networks |
| VPN-gated access to PeopleSoft | Variable — some orgs require VPN, others do not | High if implemented |
| Web Application Firewall (WAF) | Variable | Moderate — WAF may block exploit traffic if rules are updated |
| Vulnerability scanning | In place | Low — zero-day; no signature existed until June 11 advisory |
| SIEM / anomaly detection | In place | Moderate — anomalous EMHub API calls may trigger alerts |
| Vendor patch management | In place | Requires out-of-band emergency patch cycle bypass |

---

## 6. Residual Risk

Without patching, residual risk remains **Critical**. Emergency compensating control (restrict PeopleSoft to internal/VPN-only access) reduces likelihood from 5 to 3, bringing residual risk to High (15) but not eliminating it.

---

## 7. Risk Treatment Decision

**TREAT — Emergency remediation required.** Patch all PeopleSoft instances immediately. No acceptable risk tolerance for a CVSS 9.8 zero-day with active extortion campaign.

---

## 8. Framework-Specific Risk Considerations

### NIST RMF
- Step 2 (Categorize): PeopleSoft environments hosting PII/financial data likely categorized HIGH impact across Confidentiality and Integrity
- Step 4 (Implement): Emergency patch constitutes an emergency implementation event — document under CM-3 (Configuration Change Control)
- Step 6 (Monitor): Continuous monitoring programs should have flagged anomalous PeopleSoft API traffic during zero-day window

### Financial Services Regulators
- **SEC Disclosure Rule**: Organizations for whom this constitutes a material breach must file Form 8-K within 4 business days of determining materiality
- **GLBA Safeguards Rule**: Financial institutions must notify customers of unauthorized access to financial data
- **NYDFS Part 500**: Covered entities must notify NYDFS within 72 hours of a cybersecurity event

### Higher Education
- **FERPA**: Universities running PeopleSoft Student Administration face student record exposure; FERPA breach notification obligations apply

---

## 9. Recommended Remediation (Prioritized)

1. **Immediate (0–24 hours):** Restrict all PeopleSoft portal access to VPN/internal networks. Block direct internet exposure of PeopleSoft URLs at the perimeter firewall.
2. **Within 72 hours:** Deploy Oracle's emergency patch for CVE-2026-35273 to all PeopleTools 8.61 and 8.62 instances.
3. **Within 7 days:** Conduct threat hunt for IOCs from Mandiant June 11 report. Review EMHub audit logs from May 20 through June 12 for anomalous API access.
4. **Within 14 days:** Engage PCI Forensic Investigator (PFI) or IR retainer if any indicators of compromise are found.
5. **Within 30 days:** Assess whether any data exposure meets materiality threshold requiring SEC/regulatory disclosure.

---

## 10. CIS Control Reference
- **CIS Control 7.4** — Perform automated application patch management for internet-facing applications
- **CIS Control 12.2** — Establish and maintain a secure network architecture
- **CIS Control 17.4** — Establish and maintain an incident response plan

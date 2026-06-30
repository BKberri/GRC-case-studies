# Business Impact Analysis (BIA)
## Case: CVE-2026-35273 — Oracle PeopleSoft Enterprise PeopleTools Unauthenticated RCE
**Date:** 2026-06-15 | **Analyst:** Blaise Kingko

---

## 1. Executive Summary of Business Impact

CVE-2026-35273 is a CVSS 9.8 unauthenticated remote code execution vulnerability in Oracle PeopleSoft PeopleTools that was actively exploited as a zero-day by the ShinyHunters threat group beginning May 27, 2026. PeopleSoft hosts some of the most sensitive enterprise data — payroll, HR records, financial transactions, and in higher education, student personal records regulated by FERPA. A successful exploit delivers full server-level compromise and direct access to structured databases containing this data, enabling data theft, extortion, and downstream system compromise. The business impact is severe across all affected sectors.

---

## 2. Affected Business Processes

| Business Process | Dependency on PeopleSoft | Impact if Compromised |
|---|---|---|
| Human Resources — Payroll | Direct | Payroll data exfiltration; reputational damage; identity theft exposure for employees |
| Finance — GL, AP, AR | Direct | Financial data exfiltration; potential fraudulent transactions via compromised accounts |
| HR Benefits Administration | Direct | PII exposure; HIPAA crossover risk if benefits include health insurance data |
| Student Administration (Higher Ed) | Direct | FERPA breach; student PII, academic records, financial aid data at risk |
| Procurement / Supply Chain | Integrated | Vendor payment data; procurement contract terms potentially accessible |
| IT Operations — Service Desk | Integrated | PeopleSoft often integrated with AD/LDAP; lateral movement risk to identity infrastructure |

---

## 3. Data at Risk

| Data Category | Classification | Regulatory Exposure |
|---|---|---|
| Employee PII (SSN, DoB, salary, bank accounts) | Confidential | GLBA, state breach notification laws, NYDFS Part 500 |
| Financial records | Confidential | SOX (if public company), SEC Material Incident Disclosure |
| Payment card data (if payroll card programs) | Regulated | PCI-DSS |
| Student records | Confidential | FERPA |
| Health/benefits data | Sensitive | HIPAA crossover if health plan data routed through PeopleSoft Benefits |
| Vendor and contract data | Confidential | Competitive sensitivity, supply chain risk |

---

## 4. Operational Impact Scenarios

### Scenario A — Data Exfiltration Without Ransomware (Most Likely — Consistent with UNC6240 TTPs)
- **Probability:** High (consistent with ShinyHunters pattern)
- **Impact:** Mass PII exfiltration → regulatory breach notifications → class action exposure → reputational damage
- **Financial Impact Estimate:** $5M–$50M range depending on organization size (breach notification + regulatory fines + litigation + identity protection services)
- **Recovery Time:** 3–6 months (regulatory engagement, legal process, notification campaign)

### Scenario B — Ransomware Deployment via PeopleSoft Initial Access
- **Probability:** Medium (escalation from data theft)
- **Impact:** PeopleSoft services offline; HR and payroll operations halted; may cascade to identity infrastructure
- **Financial Impact Estimate:** $10M–$100M+ (ransomware payment + restoration + productivity loss + regulatory fine)
- **Recovery Time:** 2–8 weeks for systems; months for full business recovery

### Scenario C — Identity Infrastructure Pivot
- **Probability:** Medium
- **Impact:** PeopleSoft service accounts with AD/LDAP integration used to move laterally into identity infrastructure; enables broader enterprise compromise
- **Financial Impact Estimate:** Included in Scenario A/B; amplifies total impact significantly if identity provider is compromised

---

## 5. RTO / RPO Assessment

| System | Current RTO | Current RPO | Impact of RCE Compromise |
|---|---|---|---|
| PeopleSoft HR | 24 hours | 4 hours | RTO extended to 5–7 days if threat hunt required before restoration |
| PeopleSoft Finance | 4 hours | 1 hour | Financial reporting halt; potential SOX control failure |
| PeopleSoft Student Admin | 48 hours | 8 hours | Academic operations disruption; FERPA breach notification required |

---

## 6. Regulatory and Legal Impact

| Requirement | Trigger | Timeline |
|---|---|---|
| SEC Form 8-K disclosure | Material cybersecurity incident | 4 business days from materiality determination |
| GLBA data breach notification | Unauthorized access to financial PII | Promptly; NYDFS Part 500 requires 72-hour notification |
| FERPA breach notification | Unauthorized access to student education records | No specific timeline; "without unreasonable delay" |
| State breach notification laws | PII of state residents exposed | 30–72 hours depending on state |
| HIPAA breach notification | PHI exposed via benefits integration | 60 days from discovery (for covered entities) |

---

## 7. Reputational Impact

Organizations with confirmed PeopleSoft breaches in this campaign face significant reputational exposure. ShinyHunters' documented practice of publicly auctioning stolen data means data may appear on criminal markets even if the organization pays an extortion demand. Media coverage of the Mandiant June 11 report means awareness is high. Organizations in higher education and government that rely on public trust face elevated reputational risk.

---

## 8. Financial Exposure Summary

| Category | Low Estimate | High Estimate |
|---|---|---|
| Breach notification (regulatory + affected individuals) | $500K | $5M |
| Legal / litigation | $2M | $20M |
| Regulatory fines | $1M | $25M |
| Business disruption / productivity loss | $500K | $10M |
| IR / forensics retainer costs | $200K | $2M |
| Identity protection services for affected individuals | $500K | $5M |
| **Total Estimated Exposure** | **~$4.7M** | **~$67M** |

---

## 9. Business Continuity Recommendations

1. Activate incident response plan immediately if any IOCs are found during threat hunt
2. Engage external IR retainer (Mandiant, CrowdStrike, or equivalent) if PeopleSoft breach is suspected
3. Prepare breach notification templates now — do not wait for confirmed breach to draft
4. Brief General Counsel and CISO on SEC 4-day disclosure timeline obligations
5. Notify cyber insurance carrier of active exploitation campaign in sector; notify if any indicators found

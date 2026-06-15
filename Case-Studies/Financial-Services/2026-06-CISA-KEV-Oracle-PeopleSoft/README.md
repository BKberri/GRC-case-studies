# Case Study: CVE-2026-35273 — Oracle PeopleSoft Enterprise PeopleTools Unauthenticated RCE
## GRC Intelligence Program — Blaise Kingko
**Category:** IT-OT-Threats | **Sub-Category:** Enterprise Application Infrastructure
**Run Date:** 2026-06-15 | **Report Period:** 2026-06-08 to 2026-06-15
**Multi-Category:** Yes — also filed under Financial-Services (PeopleSoft HR/Finance/ERP exposure)

---

## Case Overview

Oracle PeopleSoft Enterprise PeopleTools (versions 8.61 and 8.62) contains a critical authentication bypass vulnerability (CWE-306: Missing Authentication for Critical Function) in the EMHub component. An unauthenticated remote attacker can exploit this flaw to achieve full remote code execution on the PeopleSoft application server with no privileges and no user interaction required.

The vulnerability was exploited as a **zero-day by UNC6240 (ShinyHunters)** beginning May 27, 2026 — two weeks before Oracle's emergency advisory. Mandiant confirmed an active compromise and extortion campaign. CISA added CVE-2026-35273 to the Known Exploited Vulnerabilities catalog on June 12, 2026 with a federal remediation deadline of July 3, 2026.

Oracle issued an out-of-band emergency patch on June 12, 2026.

**CVSS v3.1:** 9.8 (Critical)
**Risk Rating (this program):** Critical (Likelihood 5 × Impact 5 = 25)

---

## Why This Matters to This Program

PeopleSoft is deployed across enterprise environments including federal agencies, state governments, universities, healthcare organizations, and large financial services firms — all sectors in scope for this GRC intelligence program. The data hosted in PeopleSoft (HR PII, payroll, financial records, student data) represents some of the highest-value targets for financially motivated threat actors.

The active exploitation by ShinyHunters, a group known for publicly selling stolen data, makes this a dual risk: data breach exposure AND reputational/regulatory liability even if ransom is paid.

---

## Artifacts Included

| File | Description |
|---|---|
| `01_Threat_Intelligence.md` | CVE details, TTPs, threat actor attribution, framework mapping, recommended immediate action |
| `02_Risk_Assessment.md` | Likelihood/impact scoring, existing controls assessment, risk treatment decision |
| `03_BIA.md` | Business impact scenarios, data at risk, financial exposure estimates, RTO/RPO analysis |
| `04_Control_Mapping.md` | Cross-framework control mapping (NIST CSF, 800-53, ISO 27001, CIS), regulatory overlay, gap analysis |
| `05_Executive_Summary.md` | Board/CISO-level brief in plain English |
| `06_POAM_Remediation.md` | 10-milestone remediation plan with owners, dates, escalation path |

---

## Risk Register Entry

**Risk ID:** RR-011
**Likelihood:** 5 | **Impact:** 5 | **Risk Score:** 25 | **Rating:** Critical

---

## Key Frameworks Applied

- NIST CSF 2.0 (PR.PS-04, DE.CM-01, RS.AN-03, RS.MI-02)
- NIST SP 800-53 Rev 5 (SI-2, IA-2, AC-3, SI-10, IR-4, AU-6)
- ISO 27001:2022 (A.8.8, A.5.15, A.8.5, A.5.26)
- CIS Controls v8 (Control 7.4, Control 12.2, Control 17.4)
- GLBA Safeguards Rule, SEC Cybersecurity Disclosure Rules, NYDFS Part 500, FERPA, PCI-DSS v4.0

---

## GRC Skills Demonstrated

- Zero-day threat triage and emergency response coordination
- Multi-framework compliance obligation mapping under active incident conditions
- Financial exposure quantification (breach notification, litigation, regulatory fines)
- Executive communication during a live threat scenario
- Threat actor attribution and TTP analysis (UNC6240 / ShinyHunters / MITRE ATT&CK)
- Regulatory breach notification triage (SEC, GLBA, NYDFS, FERPA, state laws)

---

*GRC Intelligence Program v2.1 | Case built: 2026-06-15 | Run: Weekly Monday sweep*

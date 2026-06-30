# Case Study: CISA KEV 2026-03 — Hikvision & Rockwell Automation Dual Listing
## GRC Intelligence Program — Blaise Kingko
**Category:** IT-OT-Threats | **Sub-Category:** OT/IoT Convergence, Physical Security Infrastructure
**Run Date:** 2026-03-10

---

## Case Overview

On March 6, 2026, CISA added two critical (CVSS 9.8) vulnerabilities to the Known Exploited Vulnerabilities catalog in the same listing cycle: CVE-2017-7921, an authentication bypass in Hikvision IP cameras, and CVE-2021-22681, a credential exposure flaw in Rockwell Automation PLCs. Both were confirmed under active exploitation.

This case is the earliest entry in this program and the one that established its OT/IT convergence lens: the root cause enabling both findings to persist for years was not absence of a patch, but an **asset visibility gap** — these devices sat outside the standard IT vulnerability scanning and EDR footprint entirely. The remediation path required exposure management (validating real-world reachability) ahead of, and in addition to, conventional patching.

**CVSS v3.1:** 9.8 (Critical) — both CVEs
**Risk Rating (this program):** Critical

---

## Artifacts Included

| File | Description |
|---|---|
| `01_Threat_Intelligence.md` | CVE details, threat actor profiling, weaponization timeline |
| `02_Risk_Assessment.md` | NIST SP 800-30 risk scoring; per-CVE architectural analysis |
| `03_BIA.md` | Quantified financial impact; life-safety and reputational impact |
| `04_Control_Mapping.md` | NIST 800-53 / ISO 27001 / CIS Controls mapping; asset-visibility gap analysis |
| `05_Executive_Summary.md` | Board/Risk Committee brief; accelerated remediation SLA recommendation |
| `06_POAM_Remediation.md` | 6-milestone remediation plan, asset discovery through closure validation |

---

## Risk Register Reference

This case predates the program's current Risk Register ID scheme (RR-0xx, introduced with later 2026-06 runs) and is tracked narratively in this case study rather than as a numbered register entry.

---

## Key Frameworks Applied

- NIST SP 800-30 Rev. 1 (risk assessment methodology)
- NIST SP 800-53 Rev 5 (RA-5, AC-2, SI-2, SC-7, CM-8, CA-7)
- ISO/IEC 27001:2022 (Annex A.9, A.12, A.13, A.18)
- CIS Controls v8 (Controls 1, 6, 7, 12, 18)
- BOD 22-01 (CISA Known Exploited Vulnerabilities directive)

## GRC Skills Demonstrated

- OT/IT convergence risk analysis
- Asset visibility gap identification (Exposure Management vs. Vulnerability Management)
- Supply chain / geopolitical risk framing (NDAA-relevant vendor considerations)
- Life-safety risk prioritization in industrial control environments
- Cross-framework control mapping and executive risk communication

---

*GRC Intelligence Program | Case built: 2026-03-10*

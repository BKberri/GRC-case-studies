# Case Study: WordPress Core "wp2shell" Unauthenticated RCE Chain (CVE-2026-63030 + CVE-2026-60137)

**Category:** IT-OT-Threats
**Source:** CISA KEV
**CVE IDs:** CVE-2026-63030 (REST API batch-route confusion), CVE-2026-60137 (SQL injection via `author__not_in` in WP_Query)
**KEV Added:** 2026-07-21 | **Federal Due Date:** 2026-07-24 (BOD 26-04, 3-day emergency mandate)
**Risk Rating:** Critical
**Bundle Date:** 2026-07-27

## Summary
WordPress Core — the content management system powering roughly two out of every five websites globally, including a substantial share of enterprise public-facing sites — carries an unauthenticated remote code execution chain nicknamed "wp2shell" by the security research community. CVE-2026-63030 confuses the WordPress REST API's batch-processing route handling; chained with the pre-existing SQL injection at CVE-2026-60137, it allows a completely unauthenticated attacker to perform SQL injection and achieve full remote code execution — described by researchers as the first critical unauthenticated WordPress Core RCE in nearly a decade. Both CVEs were added to the CISA KEV catalog on 2026-07-21, and active exploitation was confirmed within hours of the public disclosure, including mass deployment of persistent PHP webshells disguised as plugins.

## Case Context
Wordfence researchers characterize this as the first critical, unauthenticated WordPress Core RCE in roughly ten years — a meaningful escalation from the plugin-ecosystem vulnerabilities (Joomla extensions, etc.) this program has tracked in prior weeks, because the flaw sits in Core itself rather than a third-party add-on. As of this writing, an independent tracking dashboard reports an 81.6% patch rate across a sample of ~124,580 evaluated sites — meaning roughly one in five sampled sites remained unpatched several days after public disclosure and active exploitation began.

## Artifact Index
| File | Description |
|---|---|
| 01_Threat_Intelligence.md | Full technical threat intelligence report |
| 02_Risk_Assessment.md | Risk scoring and control gap analysis |
| 03_BIA.md | Business impact analysis |
| 04_Control_Mapping.md | Framework control mapping |
| 05_Executive_Summary.md | Board/CISO-level summary |
| 06_POAM_Remediation.md | Plan of Action & Milestones |

## Key Facts
- **CVE/Advisory ID:** CVE-2026-63030, CVE-2026-60137
- **CVSS Score:** 9.8 Critical (CNA/Wordfence/WPScan scoring; NVD's CISA-ADP secondary assessment lists 7.5 — see Risk Assessment for discussion of the scoring divergence)
- **Affected Technology:** WordPress Core 6.8.0–6.8.5, 6.9.0–6.9.4, 7.0.0–7.0.1 (patched in 7.0.2, 6.9.5, 6.8.6)
- **Frameworks Applied:** NIST CSF 2.0, NIST 800-53 Rev 5, ISO 27001, CIS Controls v8
- **Exploitation Status:** Actively exploited — first probing observed 2026-07-17 23:29 UTC, SQL injection attempts 13 minutes later; mass-scanning and webshell deployment ongoing at time of writing
- **CISA Due Date:** 2026-07-24 (BOD 26-04 emergency mandate)

## Related Cases
- `2026-07-CISA-KEV-Joomla-ExtensionFileUpload` (RR-030–033, 2026-07-13) — same class of public-facing CMS unauthenticated file-upload/RCE risk, different CMS ecosystem (Joomla extensions vs. WordPress Core)

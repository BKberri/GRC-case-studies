# 2026-09-CISA-KEV-WSO2-MultiProduct-PathTraversal
**Date:** 2026-09-28 | **Source:** CISA KEV (added 2026-09-24) | **Category:** Cloud-Security | **Risk Rating:** Critical

## Summary
CISA added CVE-2026-5430, cataloged as "WSO2 Multiple Products Path Traversal Vulnerability," to the Known Exploited Vulnerabilities catalog on 2026-09-24, with the federal remediation deadline communicated as 2026-09-27. The flaw affects WSO2 Identity Server, API Manager, Micro Integrator/Enterprise Integrator, and other products named in the KEV entry, platforms most organizations run at the center of their authentication and API-exposure architecture rather than at the edge. CISA classifies this in the path traversal family (CWE-22); some outlets covering the same disclosure described it in authentication-bypass terms, a discrepancy this case study addresses directly rather than resolving without primary-source confirmation. Active exploitation is confirmed by KEV listing criteria alone. CVE-2026-5430 was added in the same batch as CVE-2026-71362, an Adobe Commerce/Magento flaw covered in a sibling case study this week. This is an identity and API-gateway exposure, and it is scored, mapped, and remediated as one.

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
- **CVE/Advisory ID:** CVE-2026-5430
- **CVSS Score:** Reported 10.0 (Critical) per third-party vulnerability intelligence trackers; not independently confirmed against NVD or WSO2's official advisory in this review
- **Affected Technology:** WSO2 Identity Server, API Manager, Micro Integrator/Enterprise Integrator, and other products named in the KEV catalog entry
- **Frameworks Applied:** NIST CSF 2.0, NIST SP 800-53 Rev 5, ISO 27001:2022, CIS Controls v8
- **Exploitation Status:** Actively exploited; CISA KEV addition 2026-09-24
- **CISA Remediation Due Date:** 2026-09-27 (federal civilian agencies, BOD 22-01)

## Related Cases
Tracked as Risk Register row RR-081. Added to the KEV catalog alongside CVE-2026-71362 (Adobe Commerce/Magento) in the same 2026-09-24 batch; see the sibling case study for that entry. This sits in this program's highest-priority category, identity infrastructure and API-gateway exposure, where a single vendor flaw carries organization-wide blast radius.

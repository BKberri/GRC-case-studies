# 2026-09-CISA-KEV-CheckPoint-QuantumGateway-VPNChain
**Date:** 2026-09-28 | **Source:** CISA KEV (added 2026-09-22) | **Category:** IT-OT-Threats | **Risk Rating:** Critical

## Summary
CISA added two Check Point vulnerabilities to the Known Exploited Vulnerabilities catalog on 2026-09-22, both rated CVSS 9.8 and both confirmed under active exploitation. CVE-2026-85102 is an improper certificate validation flaw in the VPN negotiation process of Check Point Quantum Security Gateway. An unauthenticated attacker who defeats that certificate check can execute arbitrary code directly on the gateway. CVE-2026-93616 is a path traversal and arbitrary file upload flaw in Check Point Quantum Security Management and Multi-Domain Security Management. An unauthenticated attacker can use it to upload and run a script on the management server that pushes policy to every gateway it administers. Check Point published its own advisory the same week under the heading "Action Required," and CISA set a three-day federal remediation deadline of 2026-09-25. Read together, the two disclosures describe a worst-case pairing for perimeter architecture: one vulnerability reaches the appliance customers depend on for encrypted remote access, the other reaches the console that controls every one of those appliances.

## Artifact Index
| File | Description |
|---|---|
| 01_Threat_Intelligence.md | Full technical threat intelligence report |
| 02_Risk_Assessment.md | Risk scoring, inherent/residual risk, and risk model implications |
| 03_BIA.md | Business impact analysis |
| 04_Control_Mapping.md | Framework control mapping |
| 05_Executive_Summary.md | Board/CISO-level summary |
| 06_POAM_Remediation.md | Plan of Action & Milestones |

## Key Facts
- **CVE/Advisory ID:** CVE-2026-85102 (VPN gateway certificate validation) and CVE-2026-93616 (management server path traversal)
- **CVSS Score:** Both 9.8 Critical: CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H
- **Affected Technology:** Check Point Quantum Security Gateway (Gaia OS / Gaia Embedded) and Quantum Security Management / Multi-Domain Security Management, R80.x through R82.20 version trains
- **Frameworks Applied:** NIST CSF 2.0, NIST SP 800-53 Rev 5, ISO 27001:2022, CIS Controls v8
- **Exploitation Status:** Actively exploited; CISA KEV addition 2026-09-22
- **CISA Remediation Due Date:** 2026-09-25

## Related Cases
Logged against Risk Register row RR-080, report period 2026-09-21 to 2026-09-28. This case continues the program's recurring pattern of internet-facing VPN and perimeter-appliance KEV entries, alongside the Ivanti Connect Secure, SonicWall SMA1000, and Progress LoadMaster case studies, and it lands in the same reporting week as the sibling Citrix NetScaler zero-day case study. The pattern itself is discussed in Section 5.3 of 02_Risk_Assessment.md.

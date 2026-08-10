# 2026-08-CISA-KEV-Progress-LoadMaster-CommandInjection
**Date:** 2026-08-10 | **Source:** CISA KEV | **Category:** IT-OT-Threats | **Risk Rating:** Critical

## Summary
Progress Kemp LoadMaster application delivery controllers (ADC/load balancers) contain a pre-authentication OS command injection vulnerability (CVE-2026-8037, CVSS 9.6) in the `escape_quotes()` input-sanitization function used by the `/accessv2` API endpoint. A heap-buffer memory-boundary defect allows an attacker to send a crafted, unauthenticated request containing shell metacharacters that are ultimately executed with root privileges. Progress fixed the flaw in LoadMaster GA 7.2.63.2 and LTSF 7.2.54.18 in June 2026. Exploitation activity has been observed since 2026-06-29, and CISA added the CVE to its KEV catalog on 2026-08-07 following continued attack attempts against unpatched appliances.

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
- **CVE/Advisory ID:** CVE-2026-8037
- **CVSS Score:** 9.6 (Critical)
- **Affected Technology:** Progress Kemp LoadMaster GA 7.2.63.1 and earlier; LoadMaster LTSF 7.2.54.17 and earlier (fixed in 7.2.63.2 / 7.2.54.18)
- **Frameworks Applied:** NIST CSF 2.0, NIST 800-53 Rev 5, ISO 27001:2022, CIS Controls v8
- **Exploitation Status:** Actively exploited since 2026-06-29; added to CISA KEV 2026-08-07
- **CISA Due Date:** Confirm against live catalog entry (added 2026-08-07)

## Related Cases
Consistent with this program's recurring pattern of network-perimeter/management-plane appliance KEV entries — see `IT-OT-Threats/2026-08-CISA-KEV-Arista-VeloCloud-CommandInjection` (same vulnerability class, command injection, prior week) and `IT-OT-Threats/2026-08-CISA-KEV-Cisco-FMC-HardcodedPassword`. ADCs/load balancers sit in the same high-value perimeter-infrastructure category as VPN concentrators and SD-WAN orchestrators repeatedly targeted this year.

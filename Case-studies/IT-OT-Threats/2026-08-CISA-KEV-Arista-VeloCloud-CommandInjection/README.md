# 2026-08-CISA-KEV-Arista-VeloCloud-CommandInjection
**Date:** 2026-08-03 | **Source:** CISA KEV | **Category:** IT-OT-Threats | **Risk Rating:** Critical

## Summary
Arista Networks' VeloCloud Orchestrator, the central management plane for on-premises VeloCloud SD-WAN deployments, contains an unauthenticated OS command injection vulnerability (CVE-2026-16812, CVSS 10.0) that is being actively exploited in the wild. CISA added the CVE to its Known Exploited Vulnerabilities catalog on 2026-07-27 with a three-day remediation deadline, reflecting the severity of unauthenticated, no-precondition remote code execution against a system that controls an entire enterprise WAN fabric. NIST CSF 2.0, NIST 800-53, ISO 27001, and CIS Controls v8 all apply. Status: patch and network-isolation remediation in progress per POA&M.

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
- **CVE/Advisory ID:** CVE-2026-16812
- **CVSS Score:** 10.0 (Critical)
- **Affected Technology:** Arista VeloCloud Orchestrator (VCO), on-premises, versions prior to 5.2.3.14 / 6.1.3.4 / 6.4.2.4 / 7.0.0.1
- **Frameworks Applied:** NIST CSF 2.0, NIST 800-53 Rev 5, ISO 27001:2022, CIS Controls v8
- **Exploitation Status:** Actively exploited
- **CISA Due Date:** 2026-07-30

## Related Cases
Related to the broader 2026 pattern of SD-WAN/network-orchestration platform targeting also documented in `IT-OT-Threats/2026-06-CISA-KEV-Cisco-SDWAN` and `IT-OT-Threats/2026-06-CISA-KEV-Cisco-SDWAN-PathTraversal`.

# 2026-08-CISA-KEV-Nable-Ncentral-AuthBypass
**Date:** 2026-08-10 | **Source:** CISA KEV | **Category:** IT-OT-Threats | **Risk Rating:** Critical

## Summary
N-able N-central, a remote monitoring and management (RMM) platform used by MSPs and enterprise IT teams to administer large fleets of endpoints, contains two related authentication-bypass vulnerabilities. CVE-2026-18556 (CVSS 7.4) was fixed in N-central 2026.2, but N-able's remediation was incomplete: attackers found an alternate exploitation path, tracked as CVE-2026-18577 (CVSS 8.1), that bypasses the same authentication logic in builds prior to 2026.3.1.7. CISA added CVE-2026-18577 to the KEV catalog on 2026-08-03 and CVE-2026-18556 on 2026-08-04. Exploitation has been observed since 2026-08-01: attackers gain administrative access to the N-central server and abuse its built-in "Take Control" functionality to remotely access every endpoint the server manages, deploying Cloudflare Tunnel (cloudflared) for persistent access. Because N-central is a management-plane platform for potentially hundreds of downstream client environments (in MSP deployments), this is a supply-chain-multiplier risk, not a single-tenant vulnerability.

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
- **CVE/Advisory ID:** CVE-2026-18556; CVE-2026-18577
- **CVSS Score:** 7.4 (CVE-2026-18556) / 8.1 (CVE-2026-18577)
- **Affected Technology:** N-able N-central — CVE-2026-18556 affects releases through 2026.1; CVE-2026-18577 affects builds prior to 2026.3.1.7 (the incomplete fix for the first CVE)
- **Frameworks Applied:** NIST CSF 2.0, NIST 800-53 Rev 5, ISO 27001:2022, CIS Controls v8
- **Exploitation Status:** Actively exploited since 2026-08-01; both CVEs in CISA KEV
- **CISA Due Date:** Confirm against live catalog entries (added 2026-08-03 and 2026-08-04)

## Related Cases
No direct prior N-able entries in this register. Thematically related to `IT-OT-Threats/2026-08-CISA-KEV-Cisco-FMC-HardcodedPassword` (prior week) as another management-plane/administrative-infrastructure compromise, and notable for the "incomplete vendor fix" pattern also seen in `IT-OT-Threats/2026-06-CISA-KEV-Cisco-SDWAN-PathTraversal` (RR-017, an escalated update over a prior finding).

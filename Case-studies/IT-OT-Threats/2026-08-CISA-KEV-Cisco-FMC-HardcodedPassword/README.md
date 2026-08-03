# 2026-08-CISA-KEV-Cisco-FMC-HardcodedPassword
**Date:** 2026-08-03 | **Source:** CISA KEV | **Category:** IT-OT-Threats | **Risk Rating:** High

## Summary
Cisco Secure Firewall Management Center ships with a hard-coded, low-privileged administrative account (CVE-2026-20316) that remote, unauthenticated attackers are actively exploiting to access the FMC web interface. Cisco rates this High severity (Security Impact Rating 8.9) because the account is chainable with other FMC vulnerabilities toward privilege escalation, and because low-privileged access alone exposes firewall policy, network topology, and event-log data. CISA added the CVE to its KEV catalog on 2026-07-29 with an August 1, 2026 federal remediation deadline. NIST CSF 2.0, NIST 800-53, ISO 27001, and CIS Controls v8 apply; HIPAA Security Rule referenced for the illustrative healthcare BIA. Status: patch and credential-rotation remediation in progress per POA&M.

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
- **CVE/Advisory ID:** CVE-2026-20316
- **CVSS Score:** 8.9 (High, Cisco Security Impact Rating)
- **Affected Technology:** Cisco Secure Firewall Management Center — 6.4.0.13–6.4.0.18, 7.0.x, 7.1.x–7.2.x, 7.3.x–7.4.x
- **Frameworks Applied:** NIST CSF 2.0, NIST 800-53 Rev 5, ISO 27001:2022, CIS Controls v8, HIPAA Security Rule (illustrative)
- **Exploitation Status:** Actively exploited (zero-day)
- **CISA Due Date:** 2026-08-01

## Related Cases
Related to `IT-OT-Threats/2026-07-CISA-KEV-CheckPoint-SmartConsole` (prior week's firewall-management-plane authentication bypass finding) — this case represents a continuation of the 2026 trend of attackers targeting network security management-plane infrastructure directly rather than individual firewall/edge devices.

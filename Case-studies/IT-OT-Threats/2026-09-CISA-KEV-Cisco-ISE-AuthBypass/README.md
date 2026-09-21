# 2026-09-CISA-KEV-Cisco-ISE-AuthBypass
**Date:** 2026-09-21 | **Source:** CISA KEV / Cisco PSIRT | **Category:** IT-OT-Threats (dual: Cloud-Security — IAM) | **Risk Rating:** Critical

## Summary
Cisco disclosed a batch of seven vulnerabilities in Identity Services Engine (ISE) and ISE Passive Identity Connector (ISE-PIC) on 2026-09-16, the platform used by many enterprises as the policy engine for network access control, 802.1X authentication, and posture/identity enforcement across wired, wireless, and VPN access. The headline finding, CVE-2026-76460 (CVSS 10.0), is an incorrect-use-of-privileged-APIs flaw (CWE-648) that lets an unauthenticated remote attacker send a crafted request to a privileged API endpoint and bypass the web-based management interface entirely, gaining unauthorized administrative access to the platform. CISA added CVE-2026-76460 to the Known Exploited Vulnerabilities catalog within roughly 24 hours of Cisco's disclosure, confirming active exploitation in the wild, and set a 3-day remediation deadline (2026-09-19) for federal agencies. Six companion CVEs disclosed in the same advisory — two additional CVSS 10.0 findings (injection, improper access control), a 9.9 credential-protection flaw, two 9.1 findings, and an 8.6 RADIUS denial-of-service — were internally discovered by Cisco and are not confirmed as actively exploited, but materially expand the attack surface on any unpatched ISE deployment.

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
- **CVE/Advisory ID:** CVE-2026-76460 (KEV, primary) — related batch: CVE-2026-20130, CVE-2026-20192, CVE-2026-20234, CVE-2026-20194, CVE-2026-20237, CVE-2026-20352 (Cisco advisory cisco-sa-ISE-ABP-VNSW7Tn5)
- **CVSS Score:** 10.0 (Critical) for CVE-2026-76460 — CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:C/C:H/I:H/A:H
- **Affected Technology:** Cisco Identity Services Engine (ISE) and ISE-PIC, versions 3.1.0 through 3.5 Patch 3 (essentially all supported releases). Fixed: 3.1 Patch 12, 3.2 Patch 11, 3.3 Patch 12, 3.4 Patch 7, 3.5 Patch 4.
- **Frameworks Applied:** NIST CSF 2.0, NIST 800-53 Rev 5, ISO 27001:2022, CIS Controls v8
- **Exploitation Status:** CVE-2026-76460 confirmed actively exploited in the wild (CISA KEV, added 2026-09-16). The six companion CVEs are internally-discovered, vendor-disclosed hardening fixes with no confirmed exploitation as of this sweep.
- **CISA Remediation Due Date:** 2026-09-19 (3-day emergency window)
- **Ransomware campaign use:** Unknown per CISA KEV field (not confirmed either way)

## Related Cases
Cisco ISE governs network access policy and identity enforcement for a large share of enterprise wired/wireless/VPN environments, making this the single highest-priority finding in this run given the program's standing flag on any IAM-governance-affecting vulnerability. Dual-logged to Cloud-Security because ISE functions as an identity and access management control plane even though it is typically deployed on-premises or in a private data center rather than a public cloud account — the isolation and API-authorization failure pattern here (an unauthenticated API bypassing the front-end auth layer) is directly analogous to the IAM API-authorization gaps this program has flagged in cloud-native findings (see `2026-09-AWS-Bulletin-IAM-MultiTenant-Batch`).

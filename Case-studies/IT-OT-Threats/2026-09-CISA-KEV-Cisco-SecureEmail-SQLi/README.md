# 2026-09-CISA-KEV-Cisco-SecureEmail-SQLi
**Date:** 2026-09-21 | **Source:** CISA KEV / Cisco PSIRT | **Category:** IT-OT-Threats | **Risk Rating:** Critical

## Summary
Cisco AsyncOS software for Secure Email Gateway (SEG) contains a SQL injection vulnerability (CVE-2026-76461, CVSS 9.8) in its email-parsing logic that allows a completely unauthenticated remote attacker to send a crafted email message and achieve root-level command execution on the underlying appliance. CISA added the CVE to the Known Exploited Vulnerabilities catalog on 2026-09-14, confirming active exploitation, with a 3-day remediation deadline (2026-09-17, now past due as of this run). Fixed builds are available for all three affected AsyncOS release trains (15.5, 16.0, 16.5).

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
- **CVE/Advisory ID:** CVE-2026-76461
- **CVSS Score:** 9.8 (Critical) — CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H
- **Affected Technology:** Cisco AsyncOS for Secure Email Gateway — 15.5 and earlier, 16.0, 16.5 (pre-fix builds). Fixed: 15.5.5-0141, 16.0.4-302, 16.5.0-780.
- **Frameworks Applied:** NIST CSF 2.0, NIST 800-53 Rev 5, ISO 27001:2022, CIS Controls v8
- **Exploitation Status:** Confirmed actively exploited in the wild (CISA KEV, added 2026-09-14)
- **CISA Remediation Due Date:** 2026-09-17 (already past due — organizations that have not patched are non-compliant with the federal emergency window and carry elevated risk)

## Related Cases
This is one of two Cisco findings logged this run (see also `2026-09-CISA-KEV-Cisco-ISE-AuthBypass`), reflecting a notable concentration of critical, actively-exploited Cisco vulnerabilities disclosed within the same week — worth flagging as a vendor-concentration risk observation for any organization with significant Cisco footprint across both network-identity (ISE) and messaging-security (SEG) infrastructure.

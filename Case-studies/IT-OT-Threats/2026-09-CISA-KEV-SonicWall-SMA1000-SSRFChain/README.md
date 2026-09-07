# 2026-09-CISA-KEV-SonicWall-SMA1000-SSRFChain
**Date:** 2026-09-07 | **Source:** CISA KEV (added 2026-09-02) | **Category:** IT-OT-Threats | **Risk Rating:** Critical

## Summary
SonicWall SMA1000 series secure remote-access appliances (models 6210, 7210, 8200v) contain two chained vulnerabilities under active exploitation. CVE-2026-83548 (CVSS 10.0) is a pre-authentication server-side request forgery in the Appliance Work Place interface that lets an unauthenticated attacker reach sensitive functionality through an unintended alternate access path. CVE-2026-83549 (CVSS 7.8) is an OS command injection in the Appliance Management Console that, on its own, requires authenticated administrator access — but when chained behind the SSRF, allows a remote, unauthenticated attacker to execute arbitrary OS commands with no credentials at all. CISA added both to the KEV catalog on 2026-09-02 with a 3-day remediation deadline (2026-09-05), reflecting confirmed active exploitation. Public reporting has also framed this as the third SonicWall SMA1000 security event of 2026, following a July 2026 configuration-backup incident in which encrypted MFA/credential material was stolen — vendor advisories do not describe a confirmed technical link between that incident and these two new CVEs, but organizations that were exposed in July should treat this disclosure with additional scrutiny rather than assuming the two events are unrelated.

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
- **CVE/Advisory ID:** CVE-2026-83548 (SSRF) and CVE-2026-83549 (OS command injection)
- **CVSS Score:** CVE-2026-83548: 10.0 (Critical); CVE-2026-83549: 7.8 (High)
- **Affected Technology:** SonicWall SMA1000 firmware 12.4.3 build 03453 and earlier (fixed in 03526+); 12.5.0 build 02835 and earlier (fixed in 02952+); models 6210, 7210, 8200v
- **Frameworks Applied:** NIST CSF 2.0, NIST 800-53 Rev 5, ISO 27001:2022, CIS Controls v8
- **Exploitation Status:** Actively exploited; CISA KEV addition 2026-09-02
- **CISA Remediation Due Date:** 2026-09-05

## Related Cases
Continues this program's recurring pattern of perimeter/remote-access appliance KEV entries — see `IT-OT-Threats/2026-05-CISA-KEV-Ivanti-ConnectSecure` (RR-001) and `IT-OT-Threats/2026-08-CISA-KEV-Progress-LoadMaster-CommandInjection` for the same device class (VPN/ADC perimeter appliances repeatedly targeted throughout 2026). SonicWall SMA1000 appliances specifically have now had three separate security events disclosed in 2026 per public reporting, warranting elevated scrutiny of this vendor's remote-access product line in any environment where it is deployed.

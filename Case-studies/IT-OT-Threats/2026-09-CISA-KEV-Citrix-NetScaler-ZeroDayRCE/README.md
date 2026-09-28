# 2026-09-CISA-KEV-Citrix-NetScaler-ZeroDayRCE
**Date:** 2026-09-28 | **Source:** CISA KEV (added 2026-09-27) | **Category:** IT-OT-Threats | **Risk Rating:** Critical

## Summary
On September 27, 2026, CISA issued an alert amplifying Citrix's disclosure of eight new vulnerabilities in Citrix NetScaler ADC and NetScaler Gateway (CVE-2026-88771 through CVE-2026-88778). Two of the eight — CVE-2026-88771 and CVE-2026-88772, both improper input validation (CWE-20) flaws — were added to the CISA KEV Catalog the same day. CISA states both are "critical, zero-day vulnerabilities that can independently enable remote code execution" and confirms it has received reports and partner threat intelligence showing threat actors actively exploiting these vulnerabilities globally, with no authentication or user interaction required. NVD had not published a numeric CVSS base score for CVE-2026-88771 as of this report; this program independently assesses both KEV-listed flaws as Critical severity (9.8–10.0 equivalent) given confirmed unauthenticated RCE on an internet-facing perimeter appliance. CISA set a three-day KEV remediation due date of 2026-09-30. Citrix urges organizations to check for indicators of compromise via NetScaler Console before patching, since patching first can destroy forensic evidence of prior compromise.

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
- **CVE/Advisory ID:** CVE-2026-88771 and CVE-2026-88772 (KEV-listed); CVE-2026-88773–88778 (disclosed same bulletin, not KEV-listed)
- **CVSS Score:** Not yet published by NVD as of report date; assessed Critical (9.8–10.0 equivalent) by this program — flagged for verification once NVD publishes
- **Affected Technology:** Citrix NetScaler ADC and NetScaler Gateway, versions before 14.1-73.37 / 13.1-64.23 (and FIPS/NDcPP builds before 14.1-73.37 FIPS / 13.1.37.279 FIPS and NDcPP)
- **Frameworks Applied:** NIST CSF 2.0, NIST 800-53 Rev 5, ISO 27001:2022, CIS Controls v8 (IEC 62443 assessed as not directly applicable to this finding — see 04_Control_Mapping.md)
- **Exploitation Status:** Actively exploited; confirmed globally by CISA
- **CISA KEV Addition Date:** 2026-09-27
- **CISA Remediation Due Date:** 2026-09-30
- **Risk Register Cross-Reference:** RR-079

## Related Cases
Continues this program's recurring 2026 pattern of perimeter/remote-access appliance KEV entries — see the Ivanti Connect Secure, SonicWall SMA1000, Progress LoadMaster, Cisco ISE, and this same week's Check Point Quantum Gateway case studies for the same device class and risk pattern.

## References & Sources
| Source | URL |
|---|---|
| CISA Alert, "Critical, Zero-Day Vulnerabilities Exploited — Citrix NetScaler ADC/Gateway" (2026-09-27) | https://www.cisa.gov/news-events/alerts/2026/09/27/critical-zero-day-vulnerabilities-exploited-citrix-netscaler-adc-gateway |
| NVD, CVE-2026-88771 | https://nvd.nist.gov/vuln/detail/CVE-2026-88771 |
| CISA Known Exploited Vulnerabilities Catalog | https://www.cisa.gov/known-exploited-vulnerabilities-catalog |
| Citrix Security Bulletin CTX697096 | https://support.citrix.com/support-home/kbsearch/article?articleNumber=CTX697096 |
| Citrix, "Steps to Take if NetScaler ADC is Suspected to be Compromised" (CTX694799) | https://support.citrix.com/external/article/CTX694799/steps-to-take-if-netscaler-adc-is-suspec.html |

# Citrix NetScaler ADC/Gateway Zero-Day RCE Chain — Executive Summary

| Field | Details |
|---|---|
| **Case Study ID** | CS-ITOT-2026-09-001 |
| **Risk Register Cross-Reference** | RR-079 |
| **Report Period** | 2026-09-21 to 2026-09-28 |
| **Date Published** | 2026-09-28 |
| **Author** | Blaise Kingko |
| **Risk Rating** | Critical (25/25) |
| **Audience** | Board / CISO / Executive Leadership |

---

## 7. Executive Summary

### The Situation

On September 27, 2026, CISA issued an alert amplifying Citrix's disclosure of eight new vulnerabilities in NetScaler ADC and NetScaler Gateway — the appliances many organizations use to broker remote workforce access and deliver internet-facing applications. Two of the eight (CVE-2026-88771 and CVE-2026-88772) were added to CISA's Known Exploited Vulnerabilities Catalog the same day, with CISA stating plainly that threat actors are "actively exploiting these vulnerabilities globally." Both flaws allow an attacker with no credentials and no user interaction to run arbitrary commands on the appliance. CISA set a three-day remediation deadline of September 30, 2026 — one of the shortest windows this program tracks in a given quarter.

### The Risk to Us

If we operate NetScaler ADC or Gateway on unpatched firmware (versions before 14.1-73.37 or 13.1-64.23, including FIPS/NDcPP builds), an unauthenticated attacker can already be inside our perimeter today. This isn't a theoretical exposure window — CISA has confirmed active, global exploitation, which means the relevant question for us is not "could this happen" but "has it already happened here." A compromised NetScaler appliance sits at the intersection of remote workforce access and, in some deployments, externally-facing applications, so the potential blast radius spans employee productivity, customer-facing availability, and credential/session exposure in a single incident. Notably, NVD has not yet published a formal CVSS score for this vulnerability as of this report — we are treating it as Critical based on CISA's own characterization and our independent technical assessment, not waiting on a number that may arrive after the remediation deadline has passed.

### What We Are Doing

Per Citrix's own guidance, our first action is to check our NetScaler Console and logs for indicators of compromise **before** applying the patch — patching first can destroy the forensic evidence needed to determine whether we were already breached during the exposure window. In parallel, we are inventorying every NetScaler ADC/Gateway instance we operate, confirming exact firmware versions against the fixed builds, and staging emergency patching to close the full eight-CVE bulletin (CTX697096), not just the two KEV-listed entries. Full remediation milestones, owners, and target dates are tracked in the accompanying Plan of Action & Milestones (06_POAM_Remediation.md).

### What We Need From Leadership

We need authorization to execute an emergency change against internet-facing infrastructure inside the CISA-mandated window, which may require an approved maintenance/downtime window outside normal change-control cadence — Citrix and CISA both note that NetScaler updates can be complex and may require appliance downtime. We also need leadership awareness that this is the latest in a now-established 2026 pattern: perimeter VPN and application-delivery appliances (Ivanti, SonicWall, Progress, Check Point, and now Citrix) have been the most consistently exploited asset class this year. We recommend leadership support a standing pre-approved emergency-change procedure for this asset category, so future instances of this same pattern do not each require a fresh approval cycle under time pressure.

---

## Key Facts (Report Period Cross-Reference)

| Field | Details |
|---|---|
| **CVE / Advisory ID** | CVE-2026-88771, CVE-2026-88772 (KEV-listed); CVE-2026-88773–88778 (disclosed, same bulletin) |
| **CVSS Score** | Not yet published by NVD; assessed Critical (9.8–10.0 equivalent) by this program |
| **Affected Technology** | Citrix NetScaler ADC / Gateway, before 14.1-73.37 / 13.1-64.23 (and FIPS/NDcPP equivalents) |
| **Exploitation Status** | Actively exploited — confirmed globally by CISA |
| **CISA KEV Addition Date** | 2026-09-27 |
| **CISA Remediation Due Date** | 2026-09-30 |
| **Frameworks Applied** | NIST CSF 2.0, NIST SP 800-53 Rev 5, ISO 27001:2022, CIS Controls v8 (IEC 62443 assessed as not directly applicable — see 04_Control_Mapping.md §3.5) |

---

## References & Sources

| Source | URL | Date Accessed |
|---|---|---|
| CISA Alert, "Critical, Zero-Day Vulnerabilities Exploited — Citrix NetScaler ADC/Gateway" | https://www.cisa.gov/news-events/alerts/2026/09/27/critical-zero-day-vulnerabilities-exploited-citrix-netscaler-adc-gateway | 2026-09-28 |
| NVD, CVE-2026-88771 | https://nvd.nist.gov/vuln/detail/CVE-2026-88771 | 2026-09-28 |
| CISA Known Exploited Vulnerabilities Catalog | https://www.cisa.gov/known-exploited-vulnerabilities-catalog | 2026-09-28 |
| Citrix Security Bulletin CTX697096 | https://support.citrix.com/support-home/kbsearch/article?articleNumber=CTX697096 | 2026-09-28 |
| Citrix, "Steps to Take if NetScaler ADC is Suspected to be Compromised" (CTX694799) | https://support.citrix.com/external/article/CTX694799/steps-to-take-if-netscaler-adc-is-suspec.html | 2026-09-28 |

---

## Revision History

| Version | Date | Author | Changes |
|---|---|---|---|
| 1.0 | 2026-09-28 | Blaise Kingko | Initial publication |

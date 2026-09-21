# Threat Intelligence Report
## 2026-09-CISA-KEV-Cisco-ISE-AuthBypass
**Date:** 2026-09-21 | **Source:** Cisco PSIRT Advisory cisco-sa-ISE-ABP-VNSW7Tn5 (published 2026-09-16); CISA KEV (added 2026-09-16/17) | **Severity:** Critical | **Category:** IT-OT-Threats / Cloud-Security (IAM)

## Executive Overview
Cisco Identity Services Engine (ISE) is the policy and identity-enforcement platform many enterprises use to authenticate and authorize devices and users connecting to wired, wireless, and VPN network segments — the software that decides who and what is allowed onto the network and with what level of access. On 2026-09-16, Cisco disclosed seven vulnerabilities affecting ISE and its Passive Identity Connector (ISE-PIC) companion product. The most severe, CVE-2026-76460, allows a completely unauthenticated remote attacker to send a crafted request directly to a privileged API endpoint, bypassing the web-based management interface's authentication layer entirely and obtaining unauthorized administrative access to the platform. CISA confirmed active in-the-wild exploitation and added the CVE to its Known Exploited Vulnerabilities catalog within roughly 24 hours of disclosure — an unusually fast escalation that indicates exploitation began at or before public disclosure.

## Technical Details

### Primary Finding — CVE-2026-76460 (KEV, actively exploited)
- **CVSS Score:** 10.0 (Critical) — CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:C/C:H/I:H/A:H
- **Affected Vendor/Product/Version:** Cisco ISE and ISE-PIC, 3.1.0 through 3.5 Patch 3. Fixed in 3.1 Patch 12, 3.2 Patch 11, 3.3 Patch 12, 3.4 Patch 7, 3.5 Patch 4.
- **Vulnerability Type:** Incorrect Use of Privileged APIs (CWE-648) — an API endpoint lacks sufficient authentication control, allowing a crafted HTTP request to bypass the web management interface's authentication and reach administrative functionality directly.
- **Exploitation Status:** Actively exploited in the wild; added to CISA KEV 2026-09-16/17.
- **Threat Actor Attribution:** Not publicly named in reporting reviewed as of this sweep.
- **MITRE ATT&CK Technique IDs:** T1190 (Exploit Public-Facing Application), T1078.001 (Valid Accounts — obtained via bypass rather than theft, but functionally equivalent post-exploitation)
- **CISA Remediation Due Date:** 2026-09-19

### Companion Findings (same advisory, Cisco-disclosed, not confirmed KEV)
| CVE | CVSS | CWE | Description |
|---|---|---|---|
| CVE-2026-20130 | 10.0 | CWE-74 (Injection) | Improper neutralization of input allowing injection into a privileged code path |
| CVE-2026-20192 | 10.0 | CWE-284 (Improper Access Control) | Access control gap permitting unauthorized action outside intended authorization boundary |
| CVE-2026-20234 | 9.9 | CWE-522 (Insufficiently Protected Credentials) | Credential material not adequately protected in storage or transit within the platform |
| CVE-2026-20194 | 9.1 | CWE-669 (Incorrect Resource Transfer Between Spheres) | Resource/data crosses a trust boundary without adequate re-validation |
| CVE-2026-20237 | 9.1 | CWE-20 (Improper Input Validation) | Insufficient validation of externally supplied input |
| CVE-2026-20352 | 8.6 | CWE-119 (Improper Restriction of Memory Buffer Bounds) | RADIUS protocol handling flaw enabling denial of service |

## Affected Technology Context
ISE sits at a uniquely privileged position in enterprise network architecture: it is the system of record for "who and what is allowed on the network," integrating with Active Directory/LDAP, RADIUS, TACACS+, and 802.1X supplicants to make real-time access-control decisions. Compromise of ISE does not just expose the management plane — it gives an attacker the ability to manipulate network access policy itself, potentially granting rogue devices trusted network segment access or exfiltrating the identity/authentication database ISE maintains. Because ISE is frequently deployed as a centralized, organization-wide control point rather than per-segment, a single compromised ISE instance can have organization-wide blast radius.

## Intelligence Source Links
- Cisco Security Advisory: https://sec.cloudapps.cisco.com/security/center/content/CiscoSecurityAdvisory/cisco-sa-ISE-ABP-VNSW7Tn5
- CISA KEV Catalog: https://www.cisa.gov/known-exploited-vulnerabilities-catalog?field_cve=CVE-2026-76460
- NVD: https://nvd.nist.gov/vuln/detail/CVE-2026-76460
- BleepingComputer: https://www.bleepingcomputer.com/news/security/cisco-warns-of-identity-service-engine-zero-day-exploited-in-attacks/

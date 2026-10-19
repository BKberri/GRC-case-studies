# Threat Intelligence Report, CVE-2026-104935
## Ivanti Connect Secure Authentication Bypass to Unauthenticated Command Execution

**Case ID:** 2026-10-CISA-KEV-Ivanti-ConnectSecure-AuthBypass
**Date Identified:** 2026-10-13
**Analyst:** Blaise Kingko
**Classification:** Critical, Actively Exploited Zero-Day, CISA KEV

---

## 1. Vulnerability Summary

| Field | Detail |
|---|---|
| CVE ID | CVE-2026-104935 |
| Vendor / Product | Ivanti Connect Secure (SSL VPN / remote access gateway) |
| Affected Versions | 25.1.1.1 and prior; 25.1.2.2 and prior; 22.8R2.4 and prior |
| Fixed Versions | 25.1.1.2; 25.1.3.0 or 25.1.3.1; 22.8R2.5 (22.7.x and below unaffected) |
| CVSS Score | 8.6 (CVSSv3.0) |
| CWE | CWE-290, Authentication Bypass by Spoofing |
| CISA KEV Added | 2026-10-13 |
| CISA Remediation Due Date | 2026-10-16 (federal civilian deadline has elapsed as of this report) |
| Exploitation Status | Actively exploited as a zero-day against a limited number of customers prior to vendor disclosure |
| Patch Availability | Vendor patch available; part of the fix shipped in the July 2026 25.1.3.0 release, with Ivanti backporting to other branches when exploitation was detected |

## 2. Technical Description

CVE-2026-104935 allows a remote, unauthenticated attacker to bypass Connect Secure's authentication logic by spoofing trust in a way the appliance's session-validation path does not catch, and to leverage that bypass to run arbitrary commands on the device. Volexity identified the activity in early October 2026 and reported that the attacker chained this flaw with a second, unpatched privilege-escalation weakness that Ivanti intends to remediate in a later release, meaning the authentication-bypass patch alone does not fully close the attack path for an organization that was already compromised. Because Connect Secure is a perimeter SSL VPN appliance, successful exploitation grants an attacker a foothold directly inside the organization's trusted network boundary with no credentials and no user interaction.

## 3. Exploitation Timeline

- **Early October 2026**, Volexity detects in-the-wild exploitation of Connect Secure appliances later attributed to CVE-2026-104935, affecting a limited initial set of customers.
- **2026-10-13**, Ivanti discloses CVE-2026-104935; CISA adds it to the KEV catalog the same day, citing confirmed active exploitation.
- **2026-10-16**, CISA federal civilian remediation deadline passes.
- **As of this report (2026-10-19)**, the companion privilege-escalation flaw used in the observed attack chain remains unpatched, with Ivanti committing to a future fix.

## 4. Framework Mapping

- **NIST CSF 2.0:** PR.AA-02 (Identity/credential binding and authentication), DE.CM-01 (Network Monitoring), RS.MI-02 (Incident Mitigation)
- **NIST SP 800-53 Rev 5:** IA-2 (Identification and Authentication), SI-2 (Flaw Remediation), SC-7 (Boundary Protection), IR-4 (Incident Handling)
- **ISO/IEC 27001:2022:** A.8.5 (Secure Authentication), A.8.8 (Management of Technical Vulnerabilities)
- **CIS Controls v8:** Control 7 (Continuous Vulnerability Management), Control 12 (Network Infrastructure Management)

## 5. Recommended Immediate Action

Apply the vendor-supplied fix (25.1.1.2 / 25.1.3.0 or 25.1.3.1 / 22.8R2.5, selected per the active code branch) outside the normal patch cycle given confirmed pre-disclosure exploitation, and treat every internet-facing Connect Secure appliance as a suspected-compromise candidate until checked against Volexity's published indicators, since Ivanti has not yet published its own reliable indicators of compromise. Because the attacker's full chain includes a second, still-unpatched privilege-escalation weakness, patching alone does not guarantee containment for an appliance exploited before 2026-10-13.

**Risk Rating: Critical**

---
*Sources: Ivanti security advisory; CISA KEV catalog (dateAdded 2026-10-13, dueDate 2026-10-16); Rapid7, "Ivanti Connect Secure zero-day exploited in the wild (CVE-2026-104935)"; CSOonline, "Hackers abuse the Ivanti Connect Secure bug to gain access without accounts"; The Hacker News, "CISA urges immediate Ivanti Connect Secure patching."*

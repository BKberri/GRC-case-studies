# Threat Intelligence Report, CVE-2026-76519
## Cisco Secure Email Gateway Path Traversal to Root Command Execution

**Case ID:** 2026-10-CISA-KEV-Cisco-SecureEmailGateway-PathTraversal
**Date Identified:** 2026-10-14
**Analyst:** Blaise Kingko
**Classification:** Critical, Actively Exploited, CISA KEV, No Workaround

---

## 1. Vulnerability Summary

| Field | Detail |
|---|---|
| CVE ID | CVE-2026-76519 |
| Vendor / Product | Cisco Secure Email Gateway (physical and virtual appliances, AsyncOS) |
| Affected Versions | Vulnerable AsyncOS releases with File Reputation (AMP) enabled on a mail policy, and Content Scanner Tools below 25.3.0.5525 |
| Fixed Versions | Content Scanner Tools 25.3.0.5525+ (no reboot required); AsyncOS 15.5.5-014 (15.5 branch); AsyncOS 16.5.0-780 (16.5 branch, also the target for anything below 16.5); no fixed build exists for 16.0, which must migrate |
| CVSS Score | 9.8 (Critical), CVSS 3.1 vector AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H |
| CWE | CWE-23, Relative Path Traversal |
| CISA KEV Added | 2026-10-14 |
| CISA Remediation Due Date | 2026-10-17 (federal civilian deadline has elapsed as of this report) |
| Exploitation Status | Confirmed active exploitation in the wild; Cisco PSIRT learned of in-the-wild attacks in October 2026 |
| Patch Availability | Vendor patch available; **no workaround exists** |

## 2. Technical Description

A crafted email attachment delivered through ordinary mail flow can exploit a relative path-traversal flaw in how Secure Email Gateway's File Reputation (AMP) scanning handles file paths, allowing an unauthenticated attacker to plant attacker-chosen files on the appliance and execute commands with root privileges. No login and no user interaction beyond normal mail delivery is required; the appliance processes the malicious attachment automatically as part of its security scanning function. Secure Email and Web Manager and Secure Web Appliance are not affected, and Cisco has already deployed the fix for Secure Email Cloud Gateway customers, leaving on-premises physical and virtual appliance deployments as the exposed population.

## 3. Exploitation Timeline

- **October 2026**, Cisco PSIRT becomes aware of in-the-wild exploitation attempts against Secure Email Gateway appliances.
- **2026-10-14**, Cisco discloses CVE-2026-76519 (advisory cisco-sa-esa-afw-zqYJkjxp, internal tracking CSCwu56223); CISA adds the CVE to the KEV catalog the same day.
- **2026-10-17**, CISA federal civilian remediation deadline passes.
- **As of this report (2026-10-19)**, no vendor-acknowledged workaround exists; the fixed Content Scanner Tools build and AsyncOS releases are the only remediation path.

## 4. Framework Mapping

- **NIST CSF 2.0:** PR.PS-06 (Secure software in development and operation), DE.CM-01 (Network Monitoring), RS.MI-02 (Incident Mitigation)
- **NIST SP 800-53 Rev 5:** SI-10 (Information Input Validation), SI-2 (Flaw Remediation), SC-7 (Boundary Protection), IR-4 (Incident Handling)
- **ISO/IEC 27001:2022:** A.8.8 (Management of Technical Vulnerabilities), A.8.26 (Application Security Requirements)
- **CIS Controls v8:** Control 16 (Application Software Security), Control 7 (Continuous Vulnerability Management)

## 5. Recommended Immediate Action

Update Content Scanner Tools to 25.3.0.5525 or later immediately (no reboot or software upgrade required, deployable via the `contentscannerupdate` command if automatic updates are not enabled), and schedule the corresponding AsyncOS upgrade (15.5.5-014 for the 15.5 branch, 16.5.0-780 for 16.5 and below, with 16.0 appliances requiring migration since no fixed 16.0 build exists). Because no workaround exists and exploitation is confirmed, run `grep "System Security" system_logs` on every appliance in a cluster to check for prior compromise, and engage Cisco TAC for any appliance showing forensic indicators.

**Risk Rating: Critical**

---
*Sources: Cisco PSIRT advisory cisco-sa-esa-afw-zqYJkjxp; CISA KEV catalog (dateAdded 2026-10-14, dueDate 2026-10-17); BetaNews, "Cisco Email Gateway CVE-2026-76519 exploited" (2026-10-15).*

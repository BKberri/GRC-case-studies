# Threat Intelligence Report, CVE-2026-76504
## Cisco Catalyst SD-WAN Manager Hex Encoding Authentication Bypass

**Case ID:** 2026-10-CISA-KEV-Cisco-SDWAN-HexEncodingBypass
**Date Identified:** 2026-09-30
**Analyst:** Blaise Kingko
**Classification:** Critical, Actively Exploited, CISA KEV

---

## 1. Vulnerability Summary

| Field | Detail |
|---|---|
| CVE ID | CVE-2026-76504 |
| Vendor / Product | Cisco Catalyst SD-WAN Manager (vManage) |
| CVSS Score | 9.8 (Critical) |
| CWE | CWE-177, Improper Handling of URI Encoding (Hex Encoding) |
| CISA KEV Added | 2026-09-30 |
| CISA Remediation Due Date | 2026-10-03 (federal civilian deadline has elapsed as of this report) |
| Exploitation Status | Active exploitation confirmed, Cisco PSIRT states it became aware of active exploitation in September 2026 |
| Patch Availability | Fixed releases available: 20.9.10.1, 20.12.8.2, 20.15.6.1, 20.18.4.1, 26.1.2.1, 26.2.1. No workaround exists, upgrade is mandatory |

## 2. Technical Description

The flaw allows an unauthenticated, remote attacker to reach SD-WAN Manager's `j_security_check` authentication endpoint using hex-encoded URI characters (e.g., `%6a` for the letter "j"), bypassing the authentication filter that would normally intercept and validate the request. Successful exploitation grants the attacker access to the system with the privileges of the admin user, full administrative control of the SD-WAN management plane, which in turn controls the routing and policy configuration for every SD-WAN edge device in the fabric.

## 3. Exploitation Timeline

- **September 2026**, Cisco PSIRT becomes aware of active exploitation while handling a Technical Assistance Center (TAC) support case; the vulnerability is discovered through real-world incident investigation rather than proactive research.
- **2026-09-30**, Cisco publishes advisory cisco-sa-sdwan-webauth-xr8beuuU; CISA adds CVE-2026-76504 to the KEV catalog the same day.
- **2026-10-03**, CISA federal remediation deadline elapses.

This is the latest in a recurring pattern: Cisco SD-WAN components have been the subject of multiple KEV entries in 2026 (this program has logged Cisco SD-WAN findings in its June 2026 sweeps as well), indicating SD-WAN management infrastructure remains a high-value, recurring target.

## 4. Framework Mapping

- **NIST CSF 2.0:** PR.AA-05 (Access Permissions/Authorizations), DE.CM-01 (Network Monitoring), RS.MI-02 (Incident Mitigation)
- **NIST SP 800-53 Rev 5:** IA-2 (Identification and Authentication), SI-10 (Information Input Validation), AC-3 (Access Enforcement)
- **ISO/IEC 27001:2022:** A.8.5 (Secure Authentication), A.8.26 (Application Security Requirements)
- **CIS Controls v8:** Control 6 (Access Control Management), Control 12 (Network Infrastructure Management)

## 5. Recommended Immediate Action

Upgrade all SD-WAN Manager (vManage) instances to the first fixed release in their current train immediately, no interim workaround exists. Before upgrading, collect admin-tech diagnostic files from every Manager (including cluster members and DR sites) to preserve forensic evidence, then open a Cisco TAC case referencing CVE-2026-76504 for compromise-indicator scanning. Review `/var/log/nms/containers/service_proxy/serviceproxy-access.log` and `/var/log/nms/vmanage-server.log` for evidence of hex-encoded `j_security_check` requests indicating prior exploitation attempts.

**Risk Rating: Critical**

---
*Sources: Cisco Security Advisory cisco-sa-sdwan-webauth-xr8beuuU; Cisco "Remediate Catalyst SD-WAN Security" guidance (September 2026); CISA KEV catalog (dateAdded 2026-09-30, dueDate 2026-10-03); The Hacker News, "Cisco Warns of Attackers Exploiting Critical Authentication Bypass in SD-WAN Manager."*

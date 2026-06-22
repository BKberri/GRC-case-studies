# Control Mapping — CVE-2026-20262 (Cisco Catalyst SD-WAN Manager Path Traversal)

| Framework | Control/Clause | Application to This Case |
|---|---|---|
| **NIST CSF 2.0** | PR.PS-04 — Software is maintained, replaced, and removed | Apply Cisco fixed software to all SD-WAN Manager instances |
| **NIST CSF 2.0** | PR.AA-05 — Access permissions/authorizations managed | Enforce least-privilege and MFA on all vManage accounts |
| **NIST CSF 2.0** | DE.CM-03 — Personnel activity monitored | Forward vManage audit logs to SIEM; alert on file uploads and config changes |
| **NIST 800-53 Rev 5** | SI-2 — Flaw Remediation | Patch deployment tracked to completion by due date |
| **NIST 800-53 Rev 5** | AC-6 — Least Privilege | Remove unnecessary admin accounts; restrict file-upload capability to required roles only |
| **NIST 800-53 Rev 5** | CM-3 — Configuration Change Control | All SD-WAN Manager configuration changes reviewed and logged |
| **NIST 800-53 Rev 5** | AU-9 — Protection of Audit Information | Ensure audit logs are forwarded off-appliance before any attacker could tamper with local logs |
| **ISO/IEC 27001:2022** | A.8.8 — Management of Technical Vulnerabilities | Vulnerability tracked from KEV addition through patch confirmation |
| **ISO/IEC 27001:2022** | A.5.15 — Access Control | Account audit and MFA enforcement |
| **ISO/IEC 27001:2022** | A.8.22 — Segregation of Networks | Restrict vManage management interface to a dedicated, non-internet-routable segment |
| **CIS Controls v8** | Control 5.4 — Restrict Administrator Privileges | Admin account audit on SD-WAN Manager |
| **CIS Controls v8** | Control 7.4 — Manage OS Vulnerabilities | Patch tracking and verification |
| **CIS Controls v8** | Control 12.2 — Establish/Maintain Secure Network Architecture | Management-plane network segmentation |

## Gap Assessment
Organizations relying solely on authentication as a compensating control should note that this vulnerability requires only a valid (not necessarily privileged) account — credential hygiene and MFA enforcement are the primary interim risk-reduction levers pending patch deployment.

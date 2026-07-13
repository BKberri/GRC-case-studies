# Control Mapping — Adobe ColdFusion RDS Path Traversal RCE

| Framework | Control/Clause | Application to This Case |
|---|---|---|
| **NIST CSF 2.0** | PR.PS-04 — Software/firmware kept up to date | Apply Adobe patch (ColdFusion 2025 Update 10 / 2023 Update 21) |
| **NIST CSF 2.0** | DE.CM-01 — Networks/network services monitored | Monitor for exploitation indicators and unauthorized web-shell files |
| **NIST CSF 2.0** | RS.AN-03 — Analysis performed to determine incident scope | Forensic sweep for prior exploitation given the narrow disclosure-to-exploitation window |
| **NIST 800-53 Rev 5** | SI-2 — Flaw Remediation | Patch management for ColdFusion instances |
| **NIST 800-53 Rev 5** | SI-3 — Malicious Code Protection | Web-shell detection and removal |
| **NIST 800-53 Rev 5** | SI-10 — Information Input Validation | Root-cause control gap this CVE represents |
| **NIST 800-53 Rev 5** | AC-3 — Access Enforcement | Disable/restrict RDS access where authentication is not enforced |
| **ISO/IEC 27001:2022** | A.8.8 — Management of technical vulnerabilities | Vulnerability management process coverage for ColdFusion |
| **ISO/IEC 27001:2022** | A.8.28 — Secure coding | Vendor-side root cause; relevant to any custom ColdFusion application code review |
| **CIS Controls v8** | Control 7 (7.4) — Manage OS/Application Vulnerabilities | Patch deployment tracking |
| **CIS Controls v8** | Control 16 — Application Software Security | WAF rules on RDS/CFIDE endpoints as compensating control |

## Gap Assessment
RDS is a development-time convenience feature that is frequently left enabled in production ColdFusion deployments without authentication — a configuration-management gap independent of this specific CVE. Organizations should treat this finding as a prompt to audit all ColdFusion instances for RDS status generally, not just to patch this one flaw, since similar RDS-adjacent vulnerabilities have recurred in ColdFusion's history.

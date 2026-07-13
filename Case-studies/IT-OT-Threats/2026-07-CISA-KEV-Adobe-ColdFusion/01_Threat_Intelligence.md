# Threat Intelligence Report — Adobe ColdFusion RDS Path Traversal RCE

## CVE Details

| Field | Value |
|---|---|
| **CVE ID** | CVE-2026-48282 |
| **Vulnerability Name** | Adobe ColdFusion — RDS FILEIO Path Traversal Leading to Remote Code Execution |
| **Affected Vendor/Product** | Adobe ColdFusion 2025 (Update 9 and earlier), Adobe ColdFusion 2023 (Update 20 and earlier) |
| **CVSS Score** | 10.0 (Critical) |
| **Vulnerable Component** | Remote Development Services (RDS) FILEIO handler — `/CFIDE/main/ide.cfm?ACTION=FILEIO` |
| **Date Added to KEV** | 2026-07-07 |
| **CISA Remediation Due Date** | 2026-07-10 (3-day emergency mandate under BOD 26-04) |
| **Exploitation Type** | Path traversal → arbitrary file write → remote code execution (unauthenticated when RDS authentication is disabled) |

## Exploitation Summary
The RDS FILEIO endpoint fails to adequately validate file paths supplied in requests, allowing an attacker to write arbitrary files anywhere the ColdFusion service account can reach — including uploading a CFML web shell containing `cfexecute` tags. Once written, the web shell can be invoked to execute arbitrary commands with the privileges of the ColdFusion service account, which on Windows deployments is commonly `NT AUTHORITY\SYSTEM`. When RDS authentication is disabled (a common production configuration, since RDS is a development-time feature often left enabled/unauthenticated by oversight), no credentials are required to exploit the flaw. Adobe patched the issue on 2026-06-30 via security bulletin APSB26-68. KEVIntel honeypots detected active exploitation within approximately two hours of technical analysis becoming public, and both the Canadian Centre for Cyber Security and the Centre for Cybersecurity Belgium issued independent alerts. CISA added the CVE to KEV on 2026-07-07 based on confirmed active exploitation.

## Framework Mapping
- **NIST CSF 2.0:** PR.PS-04 (Software/firmware kept up to date), DE.CM-01 (Networks/network services monitored), RS.AN-03 (Analysis performed to determine incident scope)
- **NIST 800-53 Rev 5:** SI-2 (Flaw Remediation), SI-3 (Malicious Code Protection), SI-10 (Information Input Validation), AC-3 (Access Enforcement)
- **ISO/IEC 27001:2022:** A.8.8 (Management of technical vulnerabilities), A.8.28 (Secure coding), A.8.16 (Monitoring activities)
- **CIS Controls v8:** Control 7 (Continuous Vulnerability Management), Control 16 (Application Software Security)

## Recommended Immediate Action
Apply Adobe's patch (ColdFusion 2025 Update 10 / ColdFusion 2023 Update 21) immediately on all instances. Where patching cannot occur within the federal window, disable RDS entirely unless strictly required, and block external access to `/CFIDE/administrator` and RDS endpoints via WAF/firewall rules as an interim compensating control. Hunt for unauthorized `.cfm`, `.cfc`, `.cfml`, or `.jsp` files in the ColdFusion web root as evidence of prior exploitation.

## Risk Rating
**Critical** — CVSS 10.0, unauthenticated RCE as SYSTEM-level service account, confirmed active exploitation within hours of public disclosure, 3-day federal remediation mandate.

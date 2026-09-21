# Threat Intelligence Report
## 2026-09-CISA-KEV-Cisco-SecureEmail-SQLi
**Date:** 2026-09-21 | **Source:** Cisco PSIRT Advisory cisco-sa-esa-inj-2bLVGmhX; CISA KEV (added 2026-09-14) | **Severity:** Critical | **Category:** IT-OT-Threats

## Executive Overview
Cisco Secure Email Gateway (running AsyncOS software) is a mail-filtering appliance deployed at the network edge to inspect inbound and outbound email for spam, malware, and policy violations before it reaches end users. CVE-2026-76461 is a SQL injection vulnerability in the appliance's email-message parsing logic: insufficient input validation allows a specially crafted email to inject SQL that ultimately leads to arbitrary operating-system command execution with root privileges — meaning the attacker does not just compromise the mail-filtering function, but gains full control of the underlying appliance operating system. No authentication or user interaction is required; the attack vector is simply sending an email to an address the gateway processes.

## Technical Details
- **CVE ID:** CVE-2026-76461
- **CVSS Score:** 9.8 (Critical) — CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H
- **Affected Vendor/Product/Version:** Cisco AsyncOS for Secure Email Gateway, 15.5 and earlier, 16.0, 16.5 pre-fix builds. Fixed in 15.5.5-0141, 16.0.4-302, 16.5.0-780.
- **Vulnerability Type:** SQL Injection (CWE-89) in email-parsing logic, escalating to OS command execution
- **Exploitation Status:** Actively exploited in the wild; added to CISA KEV 2026-09-14
- **Threat Actor Attribution:** None publicly named in reporting reviewed
- **MITRE ATT&CK Technique IDs:** T1190 (Exploit Public-Facing Application), T1059 (Command and Scripting Interpreter)
- **CISA Remediation Due Date:** 2026-09-17

## Affected Technology Context
Email security gateways sit in a uniquely exposed architectural position: by design, they must accept and process untrusted inbound content (email) from the open internet, making any parsing-layer vulnerability in them directly remotely reachable without any prior foothold. A root-level compromise of the gateway gives an attacker a foothold inside the network perimeter with the ability to intercept, modify, or exfiltrate email traffic in transit, and to pivot into the broader network from a device that is often granted broad internal network trust as "security infrastructure."

## Intelligence Source Links
- Cisco Security Advisory: https://sec.cloudapps.cisco.com/security/center/content/CiscoSecurityAdvisory/cisco-sa-esa-inj-2bLVGmhX
- CISA KEV Catalog: https://www.cisa.gov/known-exploited-vulnerabilities-catalog
- NVD: https://nvd.nist.gov/vuln/detail/CVE-2026-76461
- The Hacker News: https://thehackernews.com/2026/09/cisco-secure-email-gateway-flaw.html

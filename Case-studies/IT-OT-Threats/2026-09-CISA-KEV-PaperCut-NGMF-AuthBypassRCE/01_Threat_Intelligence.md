# Threat Intelligence Report
## 2026-09-CISA-KEV-PaperCut-NGMF-AuthBypassRCE
**Date:** 2026-09-07 | **Source:** CISA KEV (added 2026-08-31) | **Severity:** Critical | **Category:** IT-OT-Threats

## Executive Overview
PaperCut NG/MF is print-management server software widely deployed across education, government, and enterprise environments to manage and account for network printing. Two vulnerabilities disclosed together and explicitly designed to be chained give an unauthenticated remote attacker a complete path to code execution on the PaperCut server. CVE-2026-81578 is a missing-authentication-for-critical-function flaw (CWE-306) that lets an unauthenticated attacker modify certain system configuration parameters. CVE-2026-82078 is an unsafe reflection vulnerability (CWE-470) that allows those manipulated configuration parameters to trigger execution of arbitrary Java bytecode already present on the application's classpath, running in the security context of the PaperCut server process itself. Chained, the pair requires no credentials and no user interaction: an attacker reaches the exposed management interface, uses the missing-authentication flaw to set malicious configuration values, and those values are then reflectively executed as code.

## Technical Details
- **CVE IDs:** CVE-2026-81578 (missing authentication for critical function); CVE-2026-82078 (unsafe reflection)
- **CVSS Score:** Not published numerically in the CISA KEV entry; the unauthenticated-configuration-write-to-code-execution chain is independently assessed as Critical (CVSS-equivalent 9.0+) given no authentication or user interaction is required for full compromise
- **Affected Vendor/Product/Version:** PaperCut NG/MF — see PaperCut's 2026-08-27 security bulletin for precise version ranges; organizations should confirm current version against that bulletin rather than assume based on general product knowledge
- **Vulnerability Type:** CWE-306 (Missing Authentication for Critical Function) chained with CWE-470 (Unsafe Reflection / Unsafe Use of Reflection)
- **Exploitation Status:** KEV-listed 2026-08-31; CISA's BOD 26-04 required-action language applies (evaluate internet exposure, apply mitigations, follow cloud-service guidance where relevant); public reporting identifies over 1,000 internet-exposed PaperCut instances as of this report
- **Threat Actor Attribution:** Not publicly attributed for this specific chain at time of this report; PaperCut's product line has prior confirmed association with Cl0p and Bl00Dy ransomware initial access (2023, unrelated CVEs)
- **MITRE ATT&CK Technique IDs:** T1190 (Exploit Public-Facing Application) for initial unauthenticated access; T1059 (Command and Scripting Interpreter) / T1055 (Process Injection, reflective-loading-adjacent) for the unsafe-reflection code execution stage
- **IOCs:** Unexpected configuration changes on PaperCut servers not attributable to legitimate administrative activity; unusual Java process behavior or unexpected class loading on the PaperCut server process; anomalous requests to the web management interface from unauthenticated sources
- **CISA Remediation Due Date:** 2026-09-14

## Affected Technology Context
Print-management infrastructure is frequently deprioritized in patch-management programs relative to perimeter network or identity systems, despite PaperCut's specific, well-documented history as a ransomware initial-access vector — the 2023 Cl0p and Bl00Dy campaigns both used earlier PaperCut vulnerabilities (CVE-2023-27350/27351) to gain initial footholds before pivoting to broader network compromise and data exfiltration. That history is directly relevant risk context for this new chain: an organization that treats "print server" as inherently low-value infrastructure is applying the wrong risk model to a product category with a proven track record as a ransomware entry point. The scale of exposure reported publicly (1,000+ internet-facing instances) suggests many organizations continue to expose PaperCut management interfaces to the internet unnecessarily, which is itself a control gap independent of any specific CVE.

## Intelligence Source Links
- CISA KEV Catalog: https://www.cisa.gov/known-exploited-vulnerabilities-catalog
- PaperCut Security Bulletin (2026-08-27): https://www.papercut.com/kb/Main/security-bulletin-27-aug-2026-urgent-security-advisory/
- CISA BOD 26-04: https://www.cisa.gov/news-events/directives/bod-26-04-prioritizing-security-updates-based-risk
- NVD: https://nvd.nist.gov/vuln/detail/CVE-2026-81578 ; https://nvd.nist.gov/vuln/detail/CVE-2026-82078

# Threat Intelligence Report
## 2026-09-CISA-KEV-SonicWall-SMA1000-SSRFChain
**Date:** 2026-09-07 | **Source:** CISA KEV (added 2026-09-02) | **Severity:** Critical | **Category:** IT-OT-Threats

## Executive Overview
SonicWall SMA1000 series appliances provide secure mobile/remote access (SSL-VPN-class functionality) for enterprise users, sitting at the network perimeter by design and commonly internet-facing. Two vulnerabilities disclosed and KEV-listed together on 2026-09-02 form a complete pre-authentication remote code execution chain. CVE-2026-83548 is a server-side request forgery in the appliance's Work Place interface that allows an unauthenticated attacker to reach internal functionality through an alternate access path the appliance was not intended to expose. CVE-2026-83549 is an OS command injection in the separate Appliance Management Console (AMC) that, evaluated alone, requires authenticated administrator privileges. Chained together, the SSRF is used to reach and authenticate to the AMC context, after which the command injection executes arbitrary OS commands — collapsing what should be two independent authentication boundaries (public-facing Work Place vs. administrative AMC) into a single unauthenticated attack path.

## Technical Details
- **CVE IDs:** CVE-2026-83548 (SSRF); CVE-2026-83549 (OS command injection)
- **CVSS Scores:** CVE-2026-83548 — 10.0 (Critical), pre-authentication, network-exploitable; CVE-2026-83549 — 7.8 (High), post-authentication in isolation, but chainable to pre-authentication via CVE-2026-83548
- **Affected Vendor/Product/Version:** SonicWall SMA1000, firmware branch 12.4.3 build 03453 and earlier (fixed in 03526+) and branch 12.5.0 build 02835 and earlier (fixed in 02952+); affected models 6210, 7210, 8200v
- **Vulnerability Type:** CWE-918 (Server-Side Request Forgery) chained with an OS command injection in the administrative console
- **Exploitation Status:** Actively exploited; CISA KEV addition 2026-09-02, remediation due 2026-09-05 (3-day window reflecting confirmed active exploitation)
- **Threat Actor Attribution:** Not publicly attributed at time of this report
- **MITRE ATT&CK Technique IDs:** T1190 (Exploit Public-Facing Application) for the initial SSRF access; T1071 / T1090 (SSRF as a request-proxying technique to reach internal-only functionality); T1059.004 (Command and Scripting Interpreter: Unix Shell) for the resulting command execution
- **IOCs:** Anomalous requests to the SMA1000 Work Place interface consistent with SSRF probing; unexpected administrative console authentication events with no corresponding legitimate admin session; unexplained process execution or configuration changes on SMA1000 appliances
- **CISA Remediation Due Date:** 2026-09-05

## Affected Technology Context
SMA1000 appliances are, by design, the trust boundary between remote users and internal enterprise networks — a full pre-authentication compromise of one is equivalent to an attacker obtaining a foothold with the appliance's own network position and, depending on configuration, potential access to whatever internal resources the appliance is permitted to reach for legitimate remote-access purposes. Public reporting (Rapid7, Sophos, others) has also noted this is the third distinct SonicWall SMA1000 security event disclosed in 2026, following a July 2026 incident in which SonicWall's own encrypted firewall configuration backups — including MFA seed material — were reported stolen. No vendor advisory confirms a technical connection between that July incident and these two September CVEs, and this report does not assert one; however, any organization that was potentially exposed in the July incident should treat the current disclosure with additional scrutiny — specifically, verifying that no residual unauthorized access from that earlier event remains in place — rather than evaluating September's finding in isolation.

## Intelligence Source Links
- CISA KEV Catalog: https://www.cisa.gov/known-exploited-vulnerabilities-catalog
- Rapid7 analysis: https://www.rapid7.com/blog/post/etr-critical-sonicwall-sma1000-vulnerabilities-cve-2026-83548-cve-2026-83549-exploited-in-the-wild/
- Sophos coverage: https://www.sophos.com/en-us/blog/sonicwall-83548-83549
- Qualys ThreatPROTECT: https://threatprotect.qualys.com/2026/09/03/cisa-warns-of-sonicwall-sma1000-vulnerabilities-active-exploitation-cve-2026-83548-cve-2026-83549/
- SonicWall PSIRT advisory: https://psirt.global.sonicwall.com/vuln-detail/SNWLID-2026-0016
- NVD: https://nvd.nist.gov/vuln/detail/CVE-2026-83548 ; https://nvd.nist.gov/vuln/detail/CVE-2026-83549

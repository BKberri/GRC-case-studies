# Threat Intelligence Report
## 2026-08-CISA-KEV-Progress-LoadMaster-CommandInjection
**Date:** 2026-08-10 | **Source:** CISA KEV (added 2026-08-07) | **Severity:** Critical | **Category:** IT-OT-Threats

## Executive Overview
Progress Kemp LoadMaster is an application delivery controller (ADC) / load balancer appliance used to distribute traffic across backend application servers, commonly deployed at the network perimeter or in front of business-critical applications. The `/accessv2` API endpoint accepts unauthenticated requests and relies on an internal `escape_quotes()` function to sanitize input before it is used in a shell command. A memory-handling defect in that function — an uninitialized heap buffer allocated via `malloc()` without a trailing null terminator — causes out-of-bounds reads from adjacent freed memory, and critically, fails to properly neutralize shell metacharacters in attacker-supplied input. The unsanitized payload is then concatenated into a command executed with root privileges, giving a remote, unauthenticated attacker full root-level command execution on the appliance.

## Technical Details
- **CVE ID:** CVE-2026-8037
- **CVSS Score:** 9.6 (Critical) — pre-authentication, network-exploitable, full root compromise
- **Affected Vendor/Product/Version:** Progress Kemp LoadMaster GA 7.2.63.1 and earlier; LoadMaster LTSF 7.2.54.17 and earlier; fixed in GA 7.2.63.2 and LTSF 7.2.54.18 (both released June 2026)
- **Vulnerability Type:** OS Command Injection via improper input sanitization / uninitialized memory handling (CWE-78 / CWE-457 pathway)
- **Exploitation Status:** Actively exploited since 2026-06-29; CISA KEV addition 2026-08-07 following continued attack attempts against unpatched appliances more than five weeks after the vendor fix shipped
- **Threat Actor Attribution:** Not publicly attributed at time of this report
- **MITRE ATT&CK Technique IDs:** T1190 (Exploit Public-Facing Application), T1059.004 (Command and Scripting Interpreter: Unix Shell), T1068 (Exploitation for Privilege Escalation — though here initial access already yields root)
- **IOCs:** Anomalous requests to the `/accessv2` endpoint containing shell metacharacters (backticks, semicolons, pipe characters) in parameters; unexpected root-level process spawning on LoadMaster appliances
- **CISA Remediation Due Date:** Confirm against live catalog entry (added 2026-08-07)

## Affected Technology Context
LoadMaster appliances typically sit directly in the traffic path for business-critical applications and are frequently internet-facing by design (they exist specifically to receive and distribute inbound traffic). Root-level compromise of an ADC gives an attacker the ability to intercept, modify, or redirect traffic destined for every backend application the appliance serves, in addition to using the appliance itself as a foothold for further network penetration. The five-week gap between the vendor's June patch release and this KEV addition — with confirmed exploitation dating back even earlier, to 2026-06-29 — is a pattern worth flagging for the program's patch-SLA metrics: organizations that deprioritized this patch because it lacked a KEV listing at release time were exposed to real, ongoing attacks for over a month before CISA's catalog addition made the urgency visible through that specific channel.

## Intelligence Source Links
- CISA KEV Alert: https://www.cisa.gov/news-events/alerts/2026/08/07/cisa-adds-one-known-exploited-vulnerability-catalog
- SecurityWeek coverage: https://www.securityweek.com/cisa-urges-immediate-patching-of-exploited-progress-loadmaster-vulnerability/
- The Hacker News coverage: https://thehackernews.com/2026/07/latest-progress-kemp-loadmaster-pre.html
- Pentest-Tools vulnerability detail: https://pentest-tools.com/vulnerabilities-exploits/progress-adc-loadmaster-command-injection_29430

# Threat Intelligence Report — Check Point SmartConsole Authentication Bypass

## CVE Details

| Field | Value |
|---|---|
| **CVE ID (primary)** | CVE-2026-16232 |
| **Related CVEs (same patch cycle)** | CVE-2026-62144 (CVSS 9.3, admin command execution bypass), CVE-2026-62145 (CVSS 7.5, Gaia Portal privilege escalation to root) |
| **Vulnerability Name** | Improper Authentication in Check Point SmartConsole login process |
| **Affected Vendor/Product** | Check Point Security Management / Multi-Domain Security Management (MDSM); versions R77.30, R80, R80.10, R80.20, R80.30, R81, R81.10, R81.20, R82, R82.10 |
| **CVSS Score** | 9.3 (Critical) |
| **Vulnerable Component** | SmartConsole login/authentication process |
| **Date Added to KEV** | 2026-07-22 |
| **CISA Remediation Due Date** | 2026-07-25 (3-day emergency mandate under BOD 26-04) |
| **Exploitation Type** | Authentication bypass — unauthenticated attacker obtains application login token, authenticates with full administrative privileges |

## Executive Overview
Check Point's SmartConsole authenticates administrators to the Management Server that controls security policy for every Security Gateway (firewall) it manages. CVE-2026-16232 allows an unauthenticated remote attacker who can reach the Management Server IP to obtain a valid application login token and use it to gain full administrative access — the ability to modify security policies and configurations across the managed environment. Check Point has confirmed active exploitation against a limited set of customers and released patches on 2026-07-22 alongside two related vulnerabilities discovered in the same review cycle.

## Technical Details
- **CVE ID:** CVE-2026-16232 (CWE-287, Improper Authentication); support reference sk185169
- **CVSS Score and vector:** 9.3 Critical
- **Affected vendor/product/version:** Check Point Security Management and Multi-Domain Security Management, versions R77.30 through R82.10 (full list: R77.30, R80, R80.10, R80.20, R80.30, R81, R81.10, R81.20, R82, R82.10)
- **Vulnerability type:** Authentication bypass in the SmartConsole login process — successful exploitation yields a valid login token without valid credentials, which the attacker then uses for full administrative authentication
- **Exploitation status:** Actively exploited. Check Point VP of Research Lotem Finkelstein confirmed the company is aware of "a small number of customers" being targeted and has notified them directly; the company has not disclosed the nature or discovery date of those attacks
- **Threat actor attribution:** Not publicly attributed
- **MITRE ATT&CK:** T1190 (Exploit Public-Facing Application), T1078 (Valid Accounts — via forged/obtained login token), T1562.001 (Impair Defenses: Disable or Modify Tools — attacker with admin access to security policy can disable inspection/logging)
- **IOCs:** Check Point has published six IP addresses associated with observed exploitation activity: 151.241.99[.]207, 151.241.99[.]233, 158.62.198[.]182, 192.142.10[.]99, 139.28.37[.]250, 194.213.18[.]137
- **CISA remediation due date:** 2026-07-25 (KEV added 2026-07-22; 3-business-day BOD 26-04 emergency mandate)

## Related Vulnerabilities Patched in the Same Cycle
Check Point's 2026-07-22 advisory also patches two related flaws, both requiring the same underlying misconfiguration (management access without Firewall protection or unrestricted Trusted Clients) to exploit:
- **CVE-2026-62144** (CVSS 9.3): Authentication bypass in Security Management/MDSM allowing an unauthenticated remote attacker to execute administrative commands directly on the Management Server, including `run-script` and `exec-command` on the Security Gateway.
- **CVE-2026-62145** (CVSS 7.5): Improper privilege management in the Check Point Gaia Portal allowing an *authenticated* attacker with read-only Gaia Portal privileges to execute commands with root privileges.

## Affected Technology Context
SmartConsole and the Management Server it connects to are not just another managed endpoint — they are the control plane for an organization's entire firewall/security gateway estate. Compromise here means an attacker can silently rewrite security policy (open ports, whitelist attacker infrastructure, disable inspection profiles) across every gateway the console manages, effectively neutralizing the perimeter security architecture the organization believes is protecting it. Exploitation specifically requires the Management Server to be reachable from the internet without IP-based restriction on Trusted Clients (GUI clients) — a configuration choice, not an unavoidable architectural exposure, which makes this both a technical patching action and a configuration-hygiene finding.

## Intelligence Source Links
- Check Point security advisory: https://blog.checkpoint.com/security/security-advisory-action-required-active-exploitation-of-check-point-smartconsole-authentication-bypass-cve-2026-16232/
- Check Point support reference: https://support.checkpoint.com/results/sk/sk185169
- The Hacker News: https://thehackernews.com/2026/07/check-point-patches-exploited.html
- CISA KEV addition: https://www.cisa.gov/news-events/alerts/2026/07/22/cisa-adds-two-known-exploited-vulnerabilities-catalog
- Rapid7: https://www.rapid7.com/blog/post/etr-cve-2026-16232-critical-check-point-smartconsole-authentication-bypass-exploited-in-the-wild/

## Risk Rating
**Critical** — CVSS 9.3, confirmed active exploitation of a firewall management-plane authentication bypass, 3-day federal remediation mandate, and two related critical/high vulnerabilities patched in the same advisory that compound risk in the same misconfiguration scenario.

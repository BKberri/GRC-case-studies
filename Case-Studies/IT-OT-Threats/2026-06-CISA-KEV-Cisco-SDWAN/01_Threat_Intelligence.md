# Threat Intelligence Summary
## Case: CVE-2026-20245 — Cisco Catalyst SD-WAN Manager Authenticated Command Injection (root)
**Date Identified:** 2026-06-15 | **Source:** CISA KEV Catalog, added 2026-06-09 | **Analyst:** Blaise Kingko

---

### 1. CVE / Advisory ID
CVE-2026-20245 — Cisco Catalyst SD-WAN Manager Improper Encoding or Escaping of Output (CWE-116)

### 2. Vulnerability Name & Affected Product
Cisco Catalyst SD-WAN Manager (formerly Cisco SD-WAN vManage). SD-WAN Manager is the centralized management and orchestration platform for Cisco's SD-WAN fabric, controlling WAN routing policy, security policy, device templates, and configuration across all SD-WAN edge routers in the network.

### 3. CVSS Score
**7.8 (CVSS v3.1)** — High. Local authenticated attacker achieves root code execution.

### 4. Date Added to KEV
2026-06-09

### 5. Exploitation Type
**Improper output escaping → authenticated local OS command injection → arbitrary command execution as root.** An authenticated, local attacker supplies a crafted file to the SD-WAN Manager system. Due to improper escaping/encoding of output passed to OS command handlers, the crafted file content is interpreted as OS commands and executed with root privileges.

**Attack prerequisite:** Local authentication on the SD-WAN Manager system. In practice, this means an insider threat, a compromised admin account, or an attacker who has already achieved local access via a separate vulnerability.

### 6. CISA Remediation Due Date
**June 30, 2026** (Federal Civilian Executive Branch agencies, per BOD 26-04).

### 7. Exploitation Status
**Actively exploited in the wild** per CISA KEV addition. Exploitation is post-authentication, making this a significant escalation-of-privileges risk for environments where SD-WAN Manager admin access is shared, poorly controlled, or compromised.

### 8. Why SD-WAN Manager Root Access Matters
Root access on SD-WAN Manager provides an attacker with:
- Full control over SD-WAN routing policy for the entire WAN fabric
- Ability to exfiltrate or modify device configuration templates
- Access to stored credentials and API tokens for connected devices
- Ability to deploy malicious configurations to all edge routers in the SD-WAN fabric
- Potential for traffic interception/redirection at network-wide scale

### 9. MITRE ATT&CK TTPs
- **T1078** — Valid Accounts (requires authenticated access; insider or compromised credential)
- **T1059.004** — Command and Scripting Interpreter: Unix Shell (OS command injection)
- **T1548.003** — Abuse Elevation Control Mechanism (escalation to root via injection)
- **T1565.001** — Data Manipulation: Stored Data Manipulation (malicious SD-WAN config deployment)

### 10. Framework Mapping
- **NIST CSF 2.0:** PR.AA-05 (Access controlled through least-privilege); PR.PS-02 (Secure configurations maintained); DE.CM-03 (Personnel activity monitored)
- **NIST 800-53 Rev 5:** SI-2 (Flaw Remediation), AC-6 (Least Privilege), AU-9 (Protection of Audit Information), CM-6 (Configuration Settings)
- **ISO 27001:2022 Annex A:** A.8.8 (Technical Vulnerability Management), A.5.15 (Access Control), A.8.9 (Configuration Management)
- **CIS Controls v8:** Control 7.4 (Automated application patch management); Control 5.4 (Restrict administrator privileges); Control 12.6 (Use of secure network management protocols)

### 11. Recommended Immediate Action
Apply Cisco's security patch for CVE-2026-20245 to all Cisco Catalyst SD-WAN Manager instances immediately. Simultaneously: (1) audit all user accounts with local access to SD-WAN Manager — remove any inactive or unnecessary accounts; (2) enforce MFA on all SD-WAN Manager administrator accounts; (3) restrict SD-WAN Manager access to a dedicated management network segment accessible only via privileged access workstation (PAW) or bastion host; (4) review SD-WAN Manager audit logs for any anomalous file upload or command execution activity.

### 12. Risk Rating
**High**

### 13. Sources
- CISA KEV Alert, June 9, 2026 — https://www.cisa.gov/news-events/alerts/2026/06/09/cisa-adds-three-known-exploited-vulnerabilities-catalog
- The Hacker News, "CISA Adds Cisco, Chrome, and Arista Flaws to KEV Catalog" — https://thehackernews.com/2026/06/cisa-adds-cisco-chrome-and-arista-flaws.html
- OpenText Cybersecurity Community, "Alert CISA Adds Three Known Exploited Vulnerabilities to Catalog" — https://community.opentextcybersecurity.com/vulnerability-vault-228/alert-cisa-adds-three-known-exploited-vulnerabilities-to-catalog-release-date-june-09-2026-364580

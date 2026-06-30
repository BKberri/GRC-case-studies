# Threat Intelligence Summary
## Case: CVE-2026-35273 — Oracle PeopleSoft Enterprise PeopleTools Unauthenticated RCE (Zero-Day)
**Date Identified:** 2026-06-15 | **Source:** CISA KEV Catalog, added 2026-06-12 | **Analyst:** Blaise Kingko

---

### 1. CVE / Advisory ID
CVE-2026-35273 — Oracle PeopleSoft Enterprise PeopleTools Missing Authentication for Critical Function (CWE-306)

### 2. Vulnerability Name & Affected Vendor / Product
Oracle PeopleSoft Enterprise PeopleTools (EMHub component). Affected versions: **PeopleTools 8.61 and 8.62**. Oracle PeopleSoft is a widely deployed ERP suite used in HR, finance, supply chain, and student administration across government, higher education, healthcare, and large enterprises.

### 3. CVSS Score
**9.8 (CVSS v3.1)** — Critical. Remotely exploitable with no authentication and no user interaction required.

### 4. Date Added to KEV
2026-06-12

### 5. Exploitation Type
**Missing authentication for critical function → unauthenticated remote code execution (RCE).** The EMHub component in PeopleTools fails to enforce authentication on a critical API endpoint, allowing an unauthenticated remote attacker to execute arbitrary commands on the server with application-level privileges. Exploitation is low-complexity with no special conditions required.

### 6. CISA Remediation Due Date
**July 3, 2026** — Federal Civilian Executive Branch agencies per BOD 26-04 (supersedes BOD 22-01 effective June 10, 2026). Private-sector organizations should treat this as a hard internal deadline given confirmed zero-day exploitation and an active extortion campaign in progress.

### 7. Exploitation Status
**Actively exploited in the wild as a zero-day.** Mandiant and Google Threat Intelligence Group confirmed active exploitation between **May 27 and June 9, 2026** — predating Oracle's advisory by two weeks. The threat actor UNC6240 (ShinyHunters) conducted a targeted compromise and extortion campaign against PeopleSoft application infrastructure globally. Ransomware-adjacent data exfiltration TTPs observed.

### 8. Threat Actor Attribution
**UNC6240 (ShinyHunters)** — a financially motivated threat actor with a documented history of large-scale data theft and extortion targeting SaaS platforms, cloud environments, and enterprise application infrastructure. ShinyHunters has previously exfiltrated and auctioned sensitive databases on criminal forums. Attribution based on Mandiant reporting published June 11, 2026.

### 9. MITRE ATT&CK TTPs
- **T1190** — Exploit Public-Facing Application (Initial Access)
- **T1059** — Command and Scripting Interpreter (Execution)
- **T1078** — Valid Accounts (Persistence via post-compromise credential harvesting)
- **T1041** — Exfiltration Over C2 Channel
- **T1486** — Data Encrypted for Impact (extortion stage)
- **T1657** — Financial Theft / Extortion

### 10. Framework Mapping
- **NIST CSF 2.0:** PR.PS-04 (Software is maintained, replaced, and removed commensurate with risk); DE.CM-01 (Networks monitored for anomalies); RS.AN-03 (Analysis of what took place during incident); RS.MI-02 (Incidents are contained)
- **NIST 800-53 Rev 5:** SI-2 (Flaw Remediation), SI-10 (Information Input Validation), AC-3 (Access Enforcement), IA-2 (Identification and Authentication), IR-4 (Incident Handling), AU-6 (Audit Record Review, Analysis, and Reporting)
- **ISO 27001:2022 Annex A:** A.8.8 (Management of Technical Vulnerabilities), A.5.15 (Access Control), A.8.5 (Secure Authentication), A.5.26 (Response to Information Security Incidents)
- **CIS Controls v8:** Control 7 (Continuous Vulnerability Management), Safeguard 7.4 (Perform Automated Application Patch Management); Control 12 (Network Infrastructure Management); Control 17 (Incident Response Management)
- **CMMC 2.0:** L2 — SI.2.214 (Identify, report, and correct information and information system flaws in a timely manner)
- **Financial Services:** PCI-DSS v4.0 Req 6.3.3 (patch critical/high within defined SLAs); SEC Cybersecurity Disclosure Rules (4-day material incident disclosure if PeopleSoft breach meets materiality threshold)

### 11. Recommended Immediate Action
Apply Oracle's out-of-band emergency patch for CVE-2026-35273 to all PeopleTools 8.61 and 8.62 instances immediately (target by June 22, 2026 — 10 days ahead of the federal due date). If patching cannot be completed immediately, take internet-facing PeopleSoft portals offline or restrict access to VPN/internal networks only as an emergency compensating control. Immediately conduct threat-hunt activity across all PeopleSoft environments for IOCs published in the Mandiant June 11 report: look for anomalous EMHub API access, unexpected process spawning from PeopleSoft application service accounts, and unusual outbound connections from PeopleSoft hosts.

### 12. Risk Rating
**Critical**

### 13. Sources
- CISA KEV Alert, "CISA Adds One Known Exploited Vulnerability to Catalog," June 12, 2026 — https://www.cisa.gov/news-events/alerts/2026/06/12/cisa-adds-one-known-exploited-vulnerability-catalog
- Rapid7 ETR, "Active Exploitation of Oracle PeopleSoft Zero-Day (CVE-2026-35273)" — https://www.rapid7.com/blog/post/etr-active-exploitation-of-oracle-peoplesoft-zero-day-cve-2026-35273/
- HelpNet Security, "Oracle PeopleSoft servers under attack" — https://www.helpnetsecurity.com/2026/06/11/oracle-peoplesoft-under-attack-cve-2026-35273/
- SOCRadar, "CVE-2026-35273 in Oracle PeopleSoft PeopleTools EMHub Under Active Exploitation" — https://socradar.io/blog/cve-2026-35273-oracle-peoplesoft-peopletools/
- Security Affairs, "U.S. CISA adds Oracle PeopleSoft flaw to Known Exploited Vulnerabilities catalog" — https://securityaffairs.com/193574/security/u-s-cisa-adds-oracle-peoplesoft-enterprise-peopletools-flaw-to-its-known-exploited-vulnerabilities-catalog.html

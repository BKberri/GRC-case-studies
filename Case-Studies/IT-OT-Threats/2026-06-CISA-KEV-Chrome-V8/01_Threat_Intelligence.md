# Threat Intelligence Summary
## Case: CVE-2026-11645 — Google Chromium V8 Out-of-Bounds Read/Write (Sandbox Escape → RCE)
**Date Identified:** 2026-06-15 | **Source:** CISA KEV Catalog, added 2026-06-09 | **Analyst:** Blaise Kingko

---

### 1. CVE / Advisory ID
CVE-2026-11645 — Google Chromium V8 JavaScript Engine Out-of-Bounds Read and Write Vulnerability (CWE-125 / CWE-787)

### 2. Vulnerability Name & Affected Product
Google Chromium V8 JavaScript engine. V8 is the JavaScript execution engine used in Google Chrome, Microsoft Edge (Chromium-based), and all Electron-based enterprise applications (VS Code, Slack, Teams desktop, 1Password, and hundreds of enterprise desktop apps built on Electron). The vulnerability exists in V8's memory management for JavaScript objects.

### 3. CVSS Score
**8.8 (CVSS v3.1)** — High. Remote attacker can exploit via crafted HTML page.

### 4. Date Added to KEV
2026-06-09

### 5. Exploitation Type
**Out-of-bounds read and write in V8 → Chrome sandbox escape → arbitrary code execution.** A remote attacker delivers a crafted HTML page (via phishing, malvertising, or compromised website). When rendered by the V8 engine, the out-of-bounds memory operations allow the attacker to break out of the Chrome sandbox and execute arbitrary code in the context of the browser process — effectively gaining code execution on the victim's workstation.

### 6. CISA Remediation Due Date
**June 30, 2026** (Federal Civilian Executive Branch agencies, per BOD 26-04).

### 7. Exploitation Status
**Actively exploited in the wild** per CISA KEV addition. Exploitation via malicious web pages, phishing campaigns, or malvertising delivering crafted JavaScript.

### 8. Enterprise Impact Note
This vulnerability affects **all Electron-based enterprise applications** in addition to Chrome and Edge browsers. Any corporate tool built on Electron (VS Code, many vendor desktop applications) that runs an embedded V8 engine may be vulnerable until those apps ship updates incorporating the patched Chromium version. Endpoint patch management must track Chromium version across all Electron apps, not just the Chrome browser.

### 9. MITRE ATT&CK TTPs
- **T1189** — Drive-by Compromise (malicious web page exploitation)
- **T1566.002** — Phishing: Spearphishing Link (link to page hosting exploit)
- **T1059.007** — Command and Scripting Interpreter: JavaScript
- **T1055** — Process Injection (post-sandbox-escape)

### 10. Framework Mapping
- **NIST CSF 2.0:** PR.PS-04 (Software maintained commensurate with risk); DE.CM-04 (Malicious code detected); PR.AT-01 (Awareness and training — social engineering vector)
- **NIST 800-53 Rev 5:** SI-2 (Flaw Remediation), SI-3 (Malicious Code Protection), SC-18 (Mobile Code), SA-11 (Developer Security Testing)
- **ISO 27001:2022 Annex A:** A.8.8 (Technical Vulnerability Management), A.8.7 (Protection against malware), A.6.3 (Information security awareness)
- **CIS Controls v8:** Control 7.4 (Automated application patch management); Control 9.3 (Maintain/update anti-malware software); Control 14 (Security Awareness and Skills Training)

### 11. Recommended Immediate Action
Update Google Chrome to the latest stable release immediately (patch distributed via Chrome's auto-update mechanism; verify all Chrome instances are on current version). Update Microsoft Edge to current release. Identify all Electron-based enterprise applications in use and verify vendor patch status — prioritize any that handle sensitive data (HR tools, finance apps, password managers). For Electron apps awaiting vendor patch, consider restricting or disabling until patched builds are available.

### 12. Risk Rating
**High**

### 13. Sources
- CISA KEV Alert, June 9, 2026 — https://www.cisa.gov/news-events/alerts/2026/06/09/cisa-adds-three-known-exploited-vulnerabilities-catalog
- The Hacker News, "CISA Adds Cisco, Chrome, and Arista Flaws to KEV Catalog" — https://thehackernews.com/2026/06/cisa-adds-cisco-chrome-and-arista-flaws.html
- WindowsForum, "CISA KEV June 9: Chromium V8, Arista EOS Tunnels, Cisco SD-WAN Manager" — https://windowsforum.com/threads/cisa-kev-june-9-chromium-v8-arista-eos-tunnels-cisco-sd-wan-manager.424367/

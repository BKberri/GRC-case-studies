# Threat Intelligence Summary
## Case: CVE-2026-7473 — Arista Networks EOS Incomplete Tunnel Traffic Comparison (No Patch Planned)
**Date Identified:** 2026-06-15 | **Source:** CISA KEV Catalog, added 2026-06-09 | **Analyst:** Blaise Kingko

---

### 1. CVE / Advisory ID
CVE-2026-7473 — Arista Networks Extensible Operating System (EOS) Incomplete Comparison with Missing Factors Vulnerability (CWE-697)

### 2. Vulnerability Name & Affected Product
Arista EOS network operating system. The vulnerability causes EOS to process non-configured tunnel traffic due to an incomplete comparison in tunnel endpoint validation logic. Arista EOS runs on Arista data center and campus switches/routers widely deployed in large enterprise, cloud provider, financial services, and government network environments.

### 3. CVSS Score
**6.9 (CVSS v3.1)** — Medium. Actively exploited despite sub-Critical CVSS score.

### 4. Date Added to KEV
2026-06-09

### 5. Exploitation Type
**Network traffic processing bypass.** The flaw causes Arista EOS devices to accept and process network traffic from tunnel endpoints that are not configured in the device's tunnel policy — effectively bypassing tunnel ACL/policy enforcement. Exploited to inject traffic into network segments or exfiltrate traffic from otherwise isolated network tunnels.

### 6. CISA Remediation Due Date
**June 30, 2026** (Federal Civilian Executive Branch agencies, per BOD 26-04).

### 7. Exploitation Status
**Actively exploited in the wild** per CISA KEV addition. Exploitation pattern consistent with network-level traffic injection / policy bypass, potentially used for lateral movement between network segments that were believed to be isolated by tunnel configuration.

### 8. CRITICAL NOTE — No Vendor Patch Planned
**Arista has stated that no patch will be developed for CVE-2026-7473**, citing risks that a code-level fix could break existing configurations on deployed systems. This makes this vulnerability permanently unpatched on affected EOS versions. Mitigation relies entirely on compensating controls.

### 9. Threat Actor Context
No specific attribution. Network infrastructure exploitation is common in APT campaigns (nation-state actors, UNC groups targeting financial services and government). Tunnel bypass vulnerabilities are attractive for post-compromise lateral movement.

### 10. MITRE ATT&CK TTPs
- **T1599** — Network Boundary Bridging (using tunnel policy bypass to cross network segment boundaries)
- **T1557** — Adversary-in-the-Middle (injecting into tunnel traffic)
- **T1046** — Network Service Discovery (using tunnel access to enumerate otherwise hidden segments)

### 11. Framework Mapping
- **NIST CSF 2.0:** PR.IR-01 (Networks and environments protected through network integrity management); DE.CM-01 (Networks monitored for anomalies); ID.AM-03 (Network flows documented and managed)
- **NIST 800-53 Rev 5:** SC-7 (Boundary Protection), AC-4 (Information Flow Enforcement), SC-8 (Transmission Confidentiality and Integrity), SI-4 (System Monitoring)
- **ISO 27001:2022 Annex A:** A.8.22 (Segregation of Networks), A.8.23 (Web Filtering — tunnel policy enforcement analogous), A.8.16 (Monitoring Activities)
- **CIS Controls v8:** Control 12 (Network Infrastructure Management), Safeguard 12.2 (Establish/maintain secure network architecture); Control 13 (Network Monitoring and Defense)
- **IEC 62443:** Zone/Conduit model — tunnel policy bypass threatens zone boundary integrity; SL-2 conduit enforcement affected

### 12. Recommended Immediate Action
Since no vendor patch is available, implement the following compensating controls immediately: (1) Deploy additional ACLs on Arista EOS interfaces to explicitly deny unexpected tunnel traffic sources at the interface/VLAN level; (2) Enable NetFlow/sFlow on all Arista devices with tunnel configurations and alert on unexpected tunnel endpoint traffic in SIEM; (3) Audit all tunnel configurations (GRE, VXLAN, IPsec) on all Arista EOS devices and document expected traffic patterns as a detection baseline; (4) Consider network redesign to remove reliance on EOS tunnel policy enforcement as a security boundary — implement defense-in-depth with additional inline controls.

### 13. Risk Rating
**High**

### 14. Sources
- CISA KEV Alert, June 9, 2026 — https://www.cisa.gov/news-events/alerts/2026/06/09/cisa-adds-three-known-exploited-vulnerabilities-catalog
- CVEmon/Intruder, CVE-2026-7473 Overview — https://cvemon.intruder.io/cves/CVE-2026-7473
- The Hacker News, "CISA Adds Cisco, Chrome, and Arista Flaws to KEV Catalog Amid Active Exploitation" — https://thehackernews.com/2026/06/cisa-adds-cisco-chrome-and-arista-flaws.html

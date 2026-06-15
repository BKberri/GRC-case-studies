# Threat Intelligence Summary
## Case: CVE-2026-45657 / CVE-2026-47291 — Microsoft June 2026 Patch Tuesday: Wormable Windows Kernel RCE & HTTP.sys RCE
**Date Identified:** 2026-06-15 | **Source:** Microsoft Security Response Center (MSRC), June 10, 2026 Patch Tuesday | **Analyst:** Blaise Kingko

---

### 1. CVE / Advisory IDs
- **CVE-2026-45657** — Windows Kernel Use-After-Free Remote Code Execution (Wormable)
- **CVE-2026-47291** — Windows HTTP Protocol Stack (HTTP.sys) Integer Overflow Remote Code Execution

Both disclosed June 10, 2026 as part of Microsoft's record Patch Tuesday release (198–208 CVEs total; 32 Critical).

### 2. Vulnerability Names & Affected Products

**CVE-2026-45657 (Windows Kernel RCE — Wormable)**
- Use-after-free vulnerability in the Windows Kernel
- Affected: Windows 10, Windows 11, Windows Server 2019, 2022, 2025 (all supported versions)
- An unauthenticated remote attacker sends specially crafted TCP/IP packets, triggering the kernel flaw and achieving **SYSTEM-level code execution with no user interaction required**
- Security researchers (ZDI) confirmed the exploit is **wormable** — it can self-propagate across networks without user interaction, comparable in profile to EternalBlue (MS17-010), the vulnerability behind WannaCry

**CVE-2026-47291 (HTTP.sys RCE)**
- Integer overflow / heap-based buffer overflow in Windows HTTP Protocol Stack (http.sys)
- Affected: All Windows Server systems running HTTP.sys (IIS, Windows web-facing servers, Azure IaaS VMs with public HTTP exposure)
- An unauthenticated attacker sends a specially crafted HTTP packet to trigger the overflow and achieve RCE on the target server
- **Partial mitigation available:** Systems with `MaxRequestBytes` registry value set to ≤ 65,534 bytes (default 16,384) are not impacted

### 3. CVSS Scores
- **CVE-2026-45657:** 9.8 (Critical)
- **CVE-2026-47291:** 9.8 (Critical)

### 4. Exploitation Status
- **CVE-2026-45657:** No confirmed exploitation at time of disclosure; WORMABLE classification demands treat-as-exploited urgency. ZDI explicitly compared profile to EternalBlue.
- **CVE-2026-47291:** No confirmed exploitation at time of disclosure; trivially exploitable via network with no authentication. Mass exploitation risk if patch not applied before public PoC emerges.

### 5. CISA Remediation Due Date
Not yet added to KEV (as of June 15, 2026). Per BOD 26-04 (effective June 10, 2026), federal agencies must prioritize based on Asset Exposure and Post-Exploitation Technical Impact. Both CVEs score Tier 1 under BOD 26-04 criteria — highest remediation priority for agencies.

### 6. Threat Actor Context
No specific attribution. Both vulnerabilities are rated by the security community as extremely high-exploitation-risk. The wormable nature of CVE-2026-45657 makes it a priority target for ransomware operators and nation-state actors seeking mass lateral movement capability. The HTTP.sys RCE (CVE-2026-47291) is attractive for initial access into web-facing Windows infrastructure.

### 7. Additional Critical Vulnerabilities in Same Patch Tuesday (Cloud/IAM Relevance)

| CVE | Component | CVSS | Type | Cloud Relevance |
|---|---|---|---|---|
| CVE-2026-47652 | Windows Hyper-V | 9.8 | VM Guest Escape / RCE | Azure VM host compromise risk |
| CVE-2026-45641 | Windows Hyper-V | 9.0 | VM Guest Escape | Azure IaaS host risk |
| CVE-2026-45607 | Windows Hyper-V | 9.0 | VM Guest Escape | Azure IaaS host risk |
| CVE-2026-42985 | Remote Desktop Client | 9.8 | RCE | RDP-exposed cloud management workstations |
| CVE-2026-44810 | Microsoft Cryptographic Services | 8.4 | EoP | PKI / credential infrastructure |

### 8. Framework Mapping

- **NIST CSF 2.0:** PR.PS-04 (Software maintained commensurate with risk); PR.PS-02 (Software platforms use secure configurations); DE.CM-09 (Computing hardware/software monitored for anomalies); RS.MI-02 (Incidents contained)
- **NIST 800-53 Rev 5:** SI-2 (Flaw Remediation), CM-6 (Configuration Settings), SC-5 (Denial-of-Service Protection), SC-7 (Boundary Protection), RA-5 (Vulnerability Monitoring)
- **ISO 27001:2022 Annex A:** A.8.8 (Technical Vulnerability Management), A.8.9 (Configuration Management), A.8.22 (Network Segregation), A.8.5 (Secure Authentication)
- **CIS Controls v8:** Control 7 (Continuous Vulnerability Management), Safeguard 7.4 (Automated application patch management); Control 4 (Secure Configuration); Control 12 (Network Infrastructure Management)

### 9. Recommended Immediate Action

**CVE-2026-45657 (Wormable Kernel):** Apply the June 2026 Windows cumulative update to **all Windows endpoints and servers within 72 hours**. Prioritize internet-facing and network-bridging systems first. Implement network segmentation to limit east-west propagation potential before patching is complete. This is not a normal Patch Tuesday — treat as emergency.

**CVE-2026-47291 (HTTP.sys):** Apply June 2026 updates to all IIS/HTTP.sys-exposed servers within 48 hours. As a stopgap, set `HKLM\SYSTEM\CurrentControlSet\Services\HTTP\Parameters\MaxRequestBytes` to ≤ 65,534 bytes on all web servers where patching is delayed.

### 10. Risk Rating
**Critical** (both CVEs)

### 11. Sources
- MSRC, June 2026 Security Updates Release Notes — https://msrc.microsoft.com/update-guide/releaseNote/2026-Jun
- ZDI, "The June 2026 Security Update Review" — https://www.zerodayinitiative.com/blog/2026/6/9/the-june-2026-security-update-review
- Tenable, "Microsoft's June 2026 Patch Tuesday addresses 198 CVEs" — https://www.tenable.com/blog/microsofts-june-2026-patch-tuesday-addresses-198-cves-cve-2026-49160-cve-2026-50507
- CrowdStrike, "June 2026 Patch Tuesday Analysis" — https://www.crowdstrike.com/en-us/blog/patch-tuesday-analysis-june-2026/
- Threat-Modeling.com, "Microsoft June 2026 Patch Tuesday Critical Vulnerabilities" — https://threat-modeling.com/microsoft-june-2026-patch-tuesday-critical-cves/

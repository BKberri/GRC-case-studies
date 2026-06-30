# Threat Intelligence Summary
## Case: CVE-2026-45247 — Mirasvit Full Page Cache Warmer (Magento/Adobe Commerce) Unauthenticated RCE
**Date Identified:** 2026-06-08 | **Source:** CISA KEV Catalog, added 2026-06-03 | **Analyst:** Blaise Kingko

---

### 1. CVE / Advisory ID
CVE-2026-45247 — Mirasvit Full Page Cache Warmer Deserialization of Untrusted Data Vulnerability (PHP Object Injection → unauthenticated RCE)

### 2. Vulnerability Name & Affected Vendor / Product
Mirasvit "Full Page Cache Warmer" extension for Magento 2 / Adobe Commerce. Affects all versions prior to the vendor-released fix in **v1.11.12**.

### 3. CVSS Score
**9.8 (CVSS v3.1)** / 9.3 (CVSS v4.0) — Critical

### 4. Date Added to KEV
2026-06-03

### 5. Exploitation Type
Deserialization of untrusted data → PHP object injection → **unauthenticated remote code execution**. No authentication or user interaction required; attacker sends a crafted request to the vulnerable extension endpoint.

### 6. CISA Remediation Due Date
**2026-06-06** (Federal Civilian Executive Branch agencies, per BOD 22-01). Private-sector organizations are not bound by this date but should treat it as a hard internal deadline given confirmed active exploitation.

### 7. Exploitation Status
**Actively exploited in the wild** — confirmed by Sansec, Imperva, and SecurityWeek; attackers are using the flaw to plant web shells and execute arbitrary code on Magento/Adobe Commerce servers.

### 8. Threat Actor Attribution
No specific group publicly attributed; consistent with opportunistic e-commerce-platform compromise campaigns (historically linked to Magecart-style skimming operations once initial access is achieved).

### 9. Framework Mapping
- **NIST CSF 2.0:** PR.PS-02 (Software maintained/replaced commensurate with risk); DE.CM-01 (Networks and network services are monitored); RS.AN-03 (Analysis is performed to establish what has taken place during an incident)
- **NIST 800-53 Rev 5:** SI-2 (Flaw Remediation), SI-3 (Malicious Code Protection), SI-10 (Information Input Validation), RA-5 (Vulnerability Monitoring and Scanning)
- **ISO 27001:2022 Annex A:** A.8.8 (Management of Technical Vulnerabilities), A.8.28 (Secure Coding), A.8.16 (Monitoring Activities)
- **CIS Control Number:** Control 16 (Application Software Security), Safeguard 16.13 (Conduct Application Penetration Testing); Control 7 (Continuous Vulnerability Management)

### 10. Recommended Immediate Action
Update the Mirasvit Full Page Cache Warmer extension to **v1.11.12 or later** on every Magento 2 / Adobe Commerce instance immediately; if patching cannot occur before 2026-06-10, disable or remove the extension and conduct a web-shell sweep of affected servers (check `pub/media`, `var/`, and custom module directories for unauthorized PHP files).

### 11. Risk Rating
**Critical**

### 12. Sources
- Sansec Research, "Critical vulnerability in Mirasvit Cache Warmer for Magento" (https://sansec.io/research/mirasvit-cache-warmer-object-injection)
- Imperva Blog, "Imperva Customers Protected Against CVE-2026-45247"
- SecurityWeek, "Mirasvit Vulnerability Exploited to Execute Code on Magento Servers"
- SecurityAffairs, "U.S. CISA adds Mirasvit Full Page Cache Warmer flaw to its KEV catalog"

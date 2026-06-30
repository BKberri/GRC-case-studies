# Threat Intelligence Report — Cisco Catalyst SD-WAN Manager (Second KEV Entry, 2026)

## Change Since Original
- **Original bundle date:** 2026-06-15 (Case: `IT-OT-Threats/2026-06-CISA-KEV-Cisco-SDWAN`)
- **What changed:** CISA added a **second, distinct** Cisco Catalyst SD-WAN Manager vulnerability — CVE-2026-20262 — to the KEV catalog on 2026-06-15. This is not a revision of the original CVE-2026-20245 (authenticated OS command injection); it is a separate path-traversal flaw (CWE-22) in the SD-WAN Manager web UI/API file-upload flow, exploited as a zero-day, with new Cisco-issued fixed software released this week.
- **Why this qualifies for a new bundle:** Per Section 3A escalation criteria, a new vendor patch was released this week and a new actively-exploited CVE was added to KEV referencing the same affected product family (Cisco Catalyst SD-WAN Manager). The two CVEs are independent attack chains and must be tracked and remediated separately; this UPDATE bundle documents the second exposure on the same platform rather than overwriting the original case.

---

## CVE Details

| Field | Value |
|---|---|
| **CVE ID** | CVE-2026-20262 |
| **Vulnerability Name** | Cisco Catalyst SD-WAN Manager Directory or Path Traversal Vulnerability |
| **Affected Vendor/Product** | Cisco Catalyst SD-WAN Manager (formerly vManage) — all currently supported releases prior to fixed train |
| **CVSS Score** | 6.5 (Base) — CWE-22, authenticated, network-exploitable. **Note:** base score understates operational risk; chained with file-write-to-RCE/root escalation, the practical impact is Critical. |
| **Date Added to KEV** | 2026-06-15 |
| **Exploitation Type** | Path traversal → arbitrary file creation/overwrite on underlying OS → privilege escalation to root |
| **CISA Remediation Due Date** | 2026-06-29 (BOD 26-04) |

## Exploitation Summary
An authenticated remote attacker exploits insufficient path validation in the SD-WAN Manager web UI/API file-upload handler to write or overwrite arbitrary files on the underlying operating system. The written file is then leveraged to escalate privileges to root on the appliance. CISA and multiple vendor threat intel teams confirm this was exploited as a zero-day prior to patch availability, with active, targeted exploitation ongoing as of this run. Cisco has released fixed software for all affected branches; **no workarounds exist** — upgrade is the only remediation path.

## Relationship to Original Case (CVE-2026-20245)
The original case (bundle dated 2026-06-15) tracks CVE-2026-20245, an authenticated local OS command injection in vManage requiring a compromised/insider account to reach root. CVE-2026-20262 is a separate, lower-authentication-bar path to the same outcome (root on the WAN management plane). Organizations that completed remediation for CVE-2026-20245 are **not** protected against CVE-2026-20262 — both patch trains must be applied.

## Framework Mapping
- **NIST CSF 2.0:** PR.AA-05 (Access permissions managed), PR.PS-04 (Software is maintained, updated), DE.CM-03 (Personnel activity monitored)
- **NIST 800-53 Rev 5:** SI-2 (Flaw Remediation), AC-6 (Least Privilege), AC-2 (Account Management), CM-3 (Configuration Change Control), AU-9 (Protection of Audit Information)
- **ISO/IEC 27001:2022 Annex A:** A.8.8 (Management of Technical Vulnerabilities), A.5.15 (Access Control), A.8.22 (Segregation of Networks), A.8.32 (Change Management)
- **CIS Controls v8:** Control 5 (Account Management), Control 7 (Continuous Vulnerability Management), Control 8 (Audit Log Management), Control 12 (Network Infrastructure Management)

## Recommended Immediate Action
Apply the Cisco fixed-software release for CVE-2026-20262 to all SD-WAN Manager instances by 2026-06-29; in parallel, confirm CVE-2026-20245 remediation is complete — both are independently exploitable on the same control plane.

## Risk Rating
**High** (base CVSS 6.5, escalated due to confirmed active exploitation, no available workaround, and criticality of the affected asset as the single point of control for the enterprise WAN fabric).

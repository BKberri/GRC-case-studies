# Control Mapping Matrix
## Case: CVE-2026-11645 — Google Chromium V8 Sandbox Escape RCE
**Date:** 2026-06-15 | **Analyst:** Blaise Kingko

---

| Control Domain | NIST CSF 2.0 | NIST 800-53 Rev 5 | ISO 27001:2022 | CIS Controls v8 | Recommendation |
|---|---|---|---|---|---|
| **Browser Patch Management** | PR.PS-04 | SI-2 | A.8.8 | Control 7.4 | Force Chrome/Edge to latest via MDM/Intune/GPO; verify no update deferrals |
| **Electron App Inventory & Patching** | ID.AM-02, PR.PS-04 | CM-8, SI-2 | A.8.8, A.5.9 | Control 2.1, 7.4 | Inventory all Electron apps; track embedded Chromium version; enforce updates |
| **Web Content Filtering** | DE.CM-04, PR.PS-05 | SC-18, SI-3 | A.8.23, A.8.7 | Control 9.2 | Block malicious URLs via DNS/proxy filtering; update threat intel feeds |
| **Email Phishing Controls** | PR.AT-01, DE.CM-04 | SI-8, AT-2 | A.6.3, A.8.7 | Control 9.4, 14.1 | DMARC/DKIM/SPF enforcement; sandbox phishing link detonation; user training |
| **EDR / Endpoint Detection** | DE.CM-09, DE.AE-02 | SI-4 | A.8.16 | Control 13.7 | Verify EDR signatures cover known V8 exploit payloads; enable script block logging |
| **Browser Session Protection** | PR.AA-03, PR.DS-02 | SC-10, IA-11 | A.5.15, A.8.5 | Control 6.3, 6.7 | Enforce short session timeouts; deploy token binding where possible; MFA on all cloud consoles |

---

## Gap Analysis

| Gap | Severity | Recommendation |
|---|---|---|
| Electron app Chromium version not tracked in CMDB | High | Add Chromium engine version as a required field in software inventory for all Electron apps |
| Chrome auto-update disabled/delayed by GPO | High | Audit GPO settings; remove any update deferral policies on browser applications |
| No URL sandbox for clicked links in email | Medium | Deploy email link scanning / sandbox detonation (e.g., Defender for Office 365 Safe Links) |

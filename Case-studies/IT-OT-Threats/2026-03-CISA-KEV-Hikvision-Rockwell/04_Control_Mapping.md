# Control Mapping Matrix
## Case: CISA KEV 2026-03 — Hikvision & Rockwell Automation Dual Listing
**Date:** 2026-03-10 | **Analyst:** Blaise Kingko

---

| Vulnerability | NIST SP 800-53 Rev 5 | ISO 27001:2022 | CIS Controls v8 | Control Description |
|---|---|---|---|---|
| CVE-2017-7921 | RA-5 (Vulnerability Monitoring and Scanning) | Annex A.12.6 | Control 7.1 | Vulnerability management / scanning coverage for IoT and physical security devices |
| CVE-2017-7921 | AC-2 (Account Management) | Annex A.9.2 | Control 6.1 | Account management / authentication hardening |
| CVE-2021-22681 | SI-2 (Flaw Remediation) | Annex A.12.6 | Control 7.4 | Flaw remediation / patching for OT assets |
| CVE-2021-22681 | SC-7 (Boundary Protection) | Annex A.13.1 | Control 12.1 | Network segmentation / OT isolation |
| Program-wide | CM-8 (System Component Inventory) | Annex A.8.1 | Control 1.1 | Inventory and control of enterprise assets (closes the scanner-visibility gap) |
| Program-wide | CA-7 (Continuous Monitoring) | Annex A.18.2 | Control 18.1 | Continuous monitoring program |

---

## Gap Identified

The root cause enabling both findings to persist was not a missing patch — it was an **asset visibility gap**: Hikvision devices were outside the scope of the automated vulnerability scanner, and OT devices in general are not covered by standard EDR. CM-8 (asset inventory) and the corresponding ISO/CIS controls are therefore weighted as the highest-leverage remediation items, ahead of the CVE-specific patches.

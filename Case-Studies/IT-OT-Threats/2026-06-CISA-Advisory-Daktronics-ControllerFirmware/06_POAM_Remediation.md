# POA&M / Remediation Plan — ICSA-26-176-04 (Daktronics Controller Firmware)

| # | Action | Owner | Target Date | Status |
|---|---|---|---|---|
| 1 | Inventory all Daktronics controllers and identify safety/transportation-adjacent deployments | Facilities/IT Engineering | 2026-07-06 | Open |
| 2 | Apply Daktronics firmware update addressing advisory vulnerabilities | Facilities/IT Engineering | 2026-07-13 | Open |
| 3 | Verify firmware update integrity verification (signed updates) is enforced | IT Security | 2026-07-13 | Open |
| 4 | Confirm network segmentation between controllers and other OT/IT systems | Network Engineering | 2026-07-13 | Open |
| 5 | Document closure evidence (firmware version, segmentation verification) | GRC | 2026-07-20 | Open |

## Specific Remediation
Apply Daktronics' firmware update addressing the authentication, input validation, and insecure update mechanism flaws described in ICSA-26-176-04. Verify network segmentation isolates affected controllers from other systems, prioritizing any controller serving a safety-relevant public messaging function.

## Federal Deadline
No CISA-mandated emergency deadline (not KEV-listed; no confirmed active exploitation). Standard ICS advisory remediation timeline applies — recommend completion within 30 days, expedited for safety-relevant deployments.

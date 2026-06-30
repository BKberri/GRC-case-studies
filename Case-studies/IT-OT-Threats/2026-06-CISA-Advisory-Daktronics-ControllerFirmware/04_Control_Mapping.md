# Control Mapping — ICSA-26-176-04 (Daktronics Controller Firmware)

| Framework | Control/Clause | Application to This Case |
|---|---|---|
| **NIST CSF 2.0** | PR.AA-01 — Identities and credentials managed | Address authentication weakness identified in advisory |
| **NIST CSF 2.0** | PR.PS-04 — Software is maintained, replaced, removed | Apply Daktronics firmware update |
| **NIST CSF 2.0** | PR.IR-01 — Network segmentation | Verify controller isolation from general IT/OT networks |
| **NIST 800-53 Rev 5** | IA-2 — Identification and Authentication | Remediate authentication weakness |
| **NIST 800-53 Rev 5** | SI-10 — Information Input Validation | Address improper input validation flaw |
| **NIST 800-53 Rev 5** | SC-7 — Boundary Protection | Confirm network segmentation around display controllers |
| **IEC 62443** | SR 1.1 — Authentication | Zone/conduit authentication control for controller access |
| **IEC 62443** | SR 3.1 — Communication Integrity | Address insecure firmware update mechanism |
| **CIS Controls v8** | Control 12 — Network Infrastructure Management | Verify segmentation/firewall rules around controller network segment |

## Gap Assessment
The advisory's identification of an insecure firmware update mechanism is itself a notable finding — recommend confirming firmware update integrity verification (signed updates) is enforced before applying the patch, to avoid simply patching one vulnerability while leaving the update mechanism itself exploitable.

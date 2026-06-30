# POA&M / Remediation Plan — CVE-2025-67038 (Lantronix EDS5000)

| # | Action | Owner | Target Date | Status |
|---|---|---|---|---|
| 1 | Inventory all Lantronix EDS5000 (EDS5008/5016/5032) devices and current firmware versions | Network/OT Engineering | 2026-06-25 | Open |
| 2 | Upgrade all affected devices to firmware 2.2.0.0R1 | Network/OT Engineering | 2026-06-26 | Open |
| 3 | Remove/restrict direct internet exposure on management interfaces pending patch | Security Operations | 2026-06-24 | Open |
| 4 | Review device logs for anomalous login attempts or command injection indicators predating patch | Security Operations / IR | 2026-06-26 | Open |
| 5 | Re-validate IT/OT zone-conduit boundary assumptions for any segment traversed by this device class | OT/ICS Engineering | 2026-06-30 | Open |
| 6 | Document closure evidence (firmware version confirmation, log review results) | GRC | 2026-07-02 | Open |

## Specific Remediation
Upgrade every EDS5000 device to firmware version 2.2.0.0R1. Pending upgrade, isolate device management interfaces from direct internet reachability and restrict to an out-of-band management network segment.

## Federal Deadline
CISA-mandated due date: 2026-06-26 (3-day mandate, BOD 26-04). Given confirmed active exploitation, treat as an emergency remediation, not a standard patch-cycle item.

# POA&M / Remediation Plan — CVE-2026-34908 / -34909 / -34910 (Ubiquiti UniFi OS)

| # | Action | Owner | Target Date | Status |
|---|---|---|---|---|
| 1 | Inventory all UniFi OS-powered devices (Cloud Gateways, Network Controllers, Protect NVRs, Access Hubs, Talk) | Network/Facilities Engineering | 2026-06-25 | Open |
| 2 | Upgrade all devices to UniFi OS Server v5.0.8 or later | Network Engineering | 2026-06-26 | Open |
| 3 | Remove direct internet exposure on management interfaces pending/following patch; restrict to VPN | Security Operations | 2026-06-24 | Open |
| 4 | Check devices for botnet conscription indicators (outbound C2 traffic, unexpected processes) | Security Operations | 2026-06-26 | Open |
| 5 | Audit surveillance footage retention and access-control logs for unauthorized changes during exposure window | Facilities Security / IR | 2026-06-27 | Open |
| 6 | Document closure evidence (firmware version, compromise-check results) | GRC | 2026-07-01 | Open |

## Specific Remediation
Upgrade every UniFi OS-powered device to UniFi OS Server v5.0.8 or later. Pending full fleet upgrade, restrict management interfaces to VPN-only access and remove direct internet exposure.

## Federal Deadline
CISA-mandated due date: 2026-06-26 (3-day mandate, BOD 26-04). Given confirmed botnet-based active exploitation, treat as an emergency remediation across the full device fleet.

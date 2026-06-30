# Business Impact Analysis — CVE-2026-34908 / -34909 / -34910 (Ubiquiti UniFi OS)

## Affected Business Function
Network infrastructure management, physical security/video surveillance (UniFi Protect), and physical access control (UniFi Access Hub) for any site using UniFi OS-powered devices.

## Impact Categories

| Impact Type | Assessment |
|---|---|
| **Confidentiality** | High — network configuration, video surveillance footage, and access logs may be exposed |
| **Integrity** | Critical — attacker can reconfigure network controllers, tamper with surveillance recordings, or modify access-control policies |
| **Availability** | High — device takeover can be used to disable network management, surveillance, or access control functions entirely |
| **Regulatory/Compliance** | Medium-High — physical access control or surveillance compromise may trigger sector-specific physical security or privacy obligations depending on facility type |
| **Reputational** | Medium — botnet participation or a publicized physical-security breach carries reputational risk beyond the immediate technical incident |

## Recovery Time Objective (RTO) / Recovery Point Objective (RPO)
- **RTO:** Patch deployment and network-exposure remediation should be completed within the 72-hour federal mandate window given confirmed active exploitation.
- **RPO:** Restore controller configuration from last known-good backup and review surveillance/access logs for unauthorized changes if compromise indicators are found.

## Dependency Mapping
Any facility relying on UniFi Protect for physical security monitoring or UniFi Access Hub for door/access control should treat patch deployment as a physical-security continuity action, not solely a network-availability action — surveillance or access-control downtime during remediation should be bridged with compensating physical security measures.

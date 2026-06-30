# Business Impact Analysis — CVE-2025-67038 (Lantronix EDS5000)

## Affected Business Function
Remote/serial connectivity for legacy OT field devices (PLCs, RTUs, sensors) in industrial, utility, and remote-monitoring environments that rely on EDS5000 console servers for IP bridging.

## Impact Categories

| Impact Type | Assessment |
|---|---|
| **Confidentiality** | Medium — device configuration and any cached credentials for downstream serial devices may be exposed |
| **Integrity** | Critical — root access enables reconfiguration of the gateway and potential manipulation of traffic to/from connected OT field devices |
| **Availability** | High — attacker with root access can disable or disrupt the gateway, severing IT/OT connectivity for monitored equipment |
| **Regulatory/Compliance** | Medium-High — depends on sector (utilities, manufacturing, critical infrastructure operators may have sector-specific reporting obligations if OT systems are affected) |
| **Reputational** | Medium — limited public visibility unless compromise cascades into a safety or service-disruption event |

## Recovery Time Objective (RTO) / Recovery Point Objective (RPO)
- **RTO:** Firmware upgrade and network isolation should be completed within 72 hours of this report given confirmed active exploitation and the 3-day federal mandate.
- **RPO:** Restore device configuration from last known-good backup if unauthorized configuration changes are identified during post-patch review.

## Dependency Mapping
Any OT monitoring, telemetry, or control function relying on field devices connected through an affected EDS5000 gateway is exposed to availability and integrity impact if the gateway is compromised or taken offline for emergency remediation.

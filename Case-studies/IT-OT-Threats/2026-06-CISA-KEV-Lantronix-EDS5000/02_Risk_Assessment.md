# Risk Assessment — CVE-2025-67038 (Lantronix EDS5000)

## Risk Statement
An actively exploited, unauthenticated OS command injection vulnerability in Lantronix EDS5000 console servers allows attackers to execute arbitrary commands as root on devices that bridge legacy OT field equipment to IP networks.

## Likelihood: 5/5 (Actively exploited in the wild)
- CISA confirmed active exploitation against internet-facing/network-accessible devices prior to KEV listing.
- No authentication is required — the malicious payload rides in the username field of a standard login attempt.
- Internet-exposed serial-to-IP gateways are routinely discovered via mass scanning (Shodan-class reconnaissance).

## Impact: 5/5 (Full system compromise — root on an OT-boundary device)
- Successful exploitation yields root-level command execution on the device.
- Because the EDS5000 bridges serial OT equipment (PLCs, RTUs, sensors) to IP networks, compromise of the device provides a pivot point into operational technology environments that may otherwise be segmented from the IT network.

## Risk Score: 25 (5 × 5) — **Critical**

## Inherent Risk: Critical
## Residual Risk: Critical until patched — no effective compensating control exists for a pre-auth root command injection on the management interface; network isolation reduces but does not eliminate exposure for devices reachable from any IP-connected segment.

## Business Risk Translation
Compromise of an EDS5000 device used in industrial, utility, or remote-monitoring operations risks attacker pivot into OT systems, with potential consequences ranging from loss of monitoring/telemetry visibility to manipulation of connected field equipment — a safety and operational-continuity risk, not merely a data risk.

## Compliance Note
Organizations operating EDS5000 devices within IEC 62443-scoped zones should document this as a zone-integrity event requiring re-validation of zone/conduit boundary assumptions, independent of whether exploitation is confirmed in their specific environment.

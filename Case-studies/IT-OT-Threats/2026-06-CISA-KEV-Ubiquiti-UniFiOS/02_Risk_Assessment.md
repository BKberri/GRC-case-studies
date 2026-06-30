# Risk Assessment — CVE-2026-34908 / -34909 / -34910 (Ubiquiti UniFi OS)

## Risk Statement
A chained set of three maximum-severity vulnerabilities in UniFi OS allows unauthenticated attackers to fully take over any UniFi Cloud Gateway, Network Controller, Protect NVR, Access Hub, or Talk appliance, with confirmed active exploitation via a botnet campaign.

## Likelihood: 5/5 (Actively exploited in the wild)
- CISA confirmed active exploitation, including a Mirai/Gafgyt-class botnet campaign.
- No authentication is required for any stage of the attack chain.
- UniFi devices are widely deployed and easily fingerprinted via standard internet scanning, and a vendor patch has been publicly available since May 21, 2026 — giving attackers a known, well-documented patch gap to target.

## Impact: 5/5 (Full system compromise)
- The chain results in complete, unauthenticated root-level takeover of the device.
- Depending on device role, impact extends beyond the network controller itself to video surveillance (Protect NVR) footage/access and physical access control (Access Hub) systems.
- Compromised devices can be conscripted into a botnet, creating both an internal risk (network/surveillance compromise) and an external liability (the organization's infrastructure participating in attacks against third parties).

## Risk Score: 25 (5 × 5) — **Critical**

## Inherent Risk: Critical
## Residual Risk: High until patched; reduced to Low-Medium with both patching and removal of direct internet exposure on management interfaces.

## Business Risk Translation
Beyond the direct network-compromise risk, organizations using UniFi Protect for physical security or Access Hub for door/access control face a secondary risk: a compromised controller can blind security teams to physical intrusions or grant unauthorized physical access, converting a cyber vulnerability into a physical security incident.

## Compliance Note
Organizations using UniFi Access Hub for regulated facility access (e.g., data centers, financial services branches) should treat this as a physical-security control failure requiring documented risk acceptance or emergency remediation, not solely an IT patching item.

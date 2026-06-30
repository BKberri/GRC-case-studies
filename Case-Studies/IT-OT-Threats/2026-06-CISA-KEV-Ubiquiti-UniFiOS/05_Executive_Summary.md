# Executive Summary — Ubiquiti Network Device Takeover Chain (CVE-2026-34908/-34909/-34910)

## What Happened
Three flaws in Ubiquiti's UniFi network and security platform — used to manage networks, security cameras, and door access systems — can be chained together to give an attacker complete, password-free control of the device. This is already being exploited by an automated botnet, and a fix has been available since late May.

## Why It Matters
If we use UniFi equipment for networking, video surveillance, or building access control, a compromised device could expose our network, blind our security cameras, or unlock doors — turning a software bug into a physical security problem.

## What We're Doing
We are identifying every UniFi device in our environment, applying the vendor's available fix, and removing any devices from direct internet exposure while remediation is in progress.

## Recommended Executive Actions
1. **Inventory all UniFi OS devices** (network controllers, cameras/NVRs, access hubs) — Owner: Network/Facilities Engineering — Target: 48 hours.
2. **Apply the vendor patch (UniFi OS Server v5.0.8+)** to every device — Owner: Network Engineering — Target: within the 3-day federal deadline.
3. **Verify no devices show signs of botnet compromise** (anomalous outbound traffic) — Owner: Security Operations — Target: this week.
4. **Confirm physical access control and surveillance systems were not tampered with** during the exposure window — Owner: Facilities Security — Target: this week.

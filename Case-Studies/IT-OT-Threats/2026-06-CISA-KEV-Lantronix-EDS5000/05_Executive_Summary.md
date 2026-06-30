# Executive Summary — Lantronix Device Server Flaw (CVE-2025-67038)

## What Happened
A critical flaw in Lantronix EDS5000 device servers — hardware used to connect older industrial equipment to modern networks — lets attackers take full control of the device without needing a password. This is already being actively exploited, and the federal patch deadline is just three days from the date this flaw was added to the government's watch list.

## Why It Matters
These devices often sit at the boundary between our office IT network and operational/industrial equipment. A compromised device could give an attacker a foothold to reach systems that are normally isolated from the internet.

## What We're Doing
We are identifying every Lantronix EDS5000 device in our environment, applying the vendor's firmware fix, and removing any devices from direct internet exposure while remediation is in progress.

## Recommended Executive Actions
1. **Inventory all Lantronix EDS5000 devices** across IT and OT environments — Owner: Network/OT Engineering — Target: 48 hours.
2. **Apply the vendor firmware update** to every affected device — Owner: Network/OT Engineering — Target: within the 3-day federal deadline.
3. **Restrict management access** to affected devices to an isolated management network until patched — Owner: Security Operations — Target: immediate.

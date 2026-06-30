# Executive Summary — Daktronics Display Controller Firmware Vulnerabilities (ICSA-26-176-04)

## What Happened
CISA published an advisory describing a chain of weaknesses in Daktronics display controller firmware — used in stadium displays, transportation signage, and other public-facing digital displays — that together could let an attacker take full control of the device. No active attacks have been confirmed yet.

## Why It Matters
If we operate Daktronics displays, particularly in transportation or public-safety-adjacent settings, a compromised controller could be used to display unauthorized or harmful content, or to take the display offline, with public visibility and reputational consequences.

## What We're Doing
We are applying the vendor's firmware update, verifying that display controller networks are properly isolated from other systems, and prioritizing any controllers used for safety-related public messaging.

## Recommended Executive Actions
1. **Inventory all Daktronics controllers** and identify which, if any, serve safety-related or transportation-adjacent functions — Owner: Facilities/IT Engineering — Target: 1 week.
2. **Apply the Daktronics firmware update** — Owner: Facilities/IT Engineering — Target: within standard change window, expedited for safety-relevant displays.
3. **Verify network segmentation** isolates display controllers from other operational systems — Owner: Network Engineering — Target: 2 weeks.

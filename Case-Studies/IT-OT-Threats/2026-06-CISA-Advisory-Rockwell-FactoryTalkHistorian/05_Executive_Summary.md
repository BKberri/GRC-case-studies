# Executive Summary — Rockwell Industrial Data Historian Vulnerabilities

## What Happened
The maker of widely-used industrial control software (Rockwell Automation) disclosed three security flaws in its FactoryTalk Historian product, which collects and stores production data from factory floor equipment. The most serious flaw could let an attacker take over the historian server remotely.

## Why It Matters
This data historian typically sits at the boundary between corporate IT networks and the factory floor (OT) network. If compromised, it could give an attacker a foothold to reach deeper into operational technology systems, and it could also let someone tamper with the production data we rely on for safety and compliance reporting.

## What We're Doing
We are applying the vendor's patches, rotating any default passwords built into the product, and verifying that the network barrier between our IT and OT systems is working as designed.

## Recommended Executive Actions
1. **Confirm FactoryTalk Historian inventory and patch status** — Owner: OT/ICS Engineering — Target: 2 weeks.
2. **Rotate hardcoded/default credentials per vendor guidance** — Owner: OT/ICS Engineering — Target: 2 weeks.
3. **Verify IT/OT network segmentation controls around historian servers** — Owner: Security Architecture — Target: this month.

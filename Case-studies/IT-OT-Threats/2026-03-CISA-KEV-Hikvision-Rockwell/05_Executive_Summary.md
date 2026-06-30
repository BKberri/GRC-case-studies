# Executive Summary
## Case: CISA KEV 2026-03 — Hikvision & Rockwell Automation Dual Listing
**Date:** 2026-03-10 | **Prepared by:** Blaise Kingko

---

## The Situation

On March 6, 2026, CISA added two critical vulnerabilities (CVSS 9.8 each) to the Known Exploited Vulnerabilities catalog: an authentication bypass in Hikvision surveillance equipment, and a credential exposure flaw in Rockwell Automation industrial control systems. A KEV listing means confirmed, active exploitation — this is no longer a theoretical risk.

These are Operational Technology (OT) and IoT-layer assets, a category that standard IT patch cycles and vulnerability scanners frequently miss. That blind spot is the central finding of this case: both vulnerabilities had existed for years, but the controlling factor in our exposure was whether these devices were even visible to our existing security tooling.

## Business Risk

- **Operational Risk:** Potential shutdown of manufacturing lines if Rockwell PLC logic is manipulated.
- **Physical Risk:** Loss of site security and unauthorized surveillance access if Hikvision devices are compromised.
- **Compliance Risk:** Exposure under BOD 22-01 federal remediation mandates, and potential cyber insurance coverage invalidation if the known-exploited window is not closed on a defensible timeline.

## What We Are Doing

1. Running full asset discovery (Nmap / passive discovery) to close the visibility gap that kept Hikvision devices outside scanner scope.
2. Isolating vulnerable OT assets from internet-facing VLANs as an immediate compensating control ahead of firmware remediation.
3. Deploying firmware patches across the Hikvision fleet and migrating Rockwell credential storage to an MFA-backed encrypted vault.
4. Validating closure with a final audit and vulnerability scan before closing the incident.

## Decision Required

The GRC team is recommending an accelerated remediation SLA — 7 business days for internet-facing assets, 15 days for internal segmented assets — which exceeds standard patch SLAs but is necessary to maintain current risk appetite given the confirmed KEV status of both findings.

**Current Risk Level: CRITICAL — Active exploitation confirmed. Compensating controls in progress. Accelerated remediation SLA requested.**

---

*This document is intended for Executive Leadership and the Risk Committee.*

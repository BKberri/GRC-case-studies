# Executive Summary
## 2026-08-CISA-KEV-Arista-VeloCloud-CommandInjection
**Date:** 2026-08-03 | **Prepared by:** GRC Intelligence Program | **Classification:** Critical

## What Happened
A critical, unauthenticated vulnerability was discovered in the management console (Orchestrator) that controls our wide-area network's SD-WAN fabric. Attackers are already exploiting this flaw in the wild against exposed instances, with no login credentials required.

## Why It Matters
This management console is the single point of control for every branch, store, or site connection on our SD-WAN network. An attacker who compromises it can potentially redirect network traffic, push malicious changes to every connected site at once, and use it as a launching point into segments of the network that are normally isolated from each other — turning one weak point into an organization-wide incident.

## What We Are Doing About It
- Patch the Orchestrator to the vendor-confirmed fixed version immediately (Network Engineering, target: within 72 hours of this report per federal remediation guidance)
- Remove the Orchestrator's management interface from direct internet exposure and restrict access to a dedicated administrative network (Network Engineering / Security Architecture, target: concurrent with patching)
- Review network traffic logs for signs of unauthorized access to the Orchestrator prior to patching (Security Operations, target: within 5 business days)
- Reissue credentials and certificates managed by the Orchestrator if any indicators of compromise are found (IT Operations, target: upon confirmation of compromise)

## Bottom Line
Leadership should treat this as an "assume breach until proven otherwise" event for any period the Orchestrator was internet-exposed and unpatched — the fix is straightforward, but the exposure window determines whether this stays a patching exercise or becomes an incident response.

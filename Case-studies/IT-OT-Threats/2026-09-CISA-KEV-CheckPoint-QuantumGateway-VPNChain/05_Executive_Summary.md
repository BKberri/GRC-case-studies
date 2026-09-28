# Executive Summary
## Check Point Quantum Security Gateway & Management Server Dual RCE (CVE-2026-85102 / CVE-2026-93616)

| Field | Details |
|---|---|
| **Case Study ID** | CS-ITOT-2026-09-002 |
| **Risk Register Reference** | RR-080 |
| **Report Period** | 2026-09-21 to 2026-09-28 |
| **Date** | 2026-09-28 |
| **Author** | Blaise Kingko |

---

## 7. Executive Summary

### The Situation
CISA added two Check Point vulnerabilities to its Known Exploited Vulnerabilities catalog on September 22. Both are rated 9.8 out of 10 in severity. Both are already being exploited. The first lets an attacker with no password take over a Check Point VPN gateway directly. The second lets an attacker with no password take over the server that manages that gateway's security policy. Check Point confirmed active exploitation in its own advisory, and CISA gave federal agencies three business days to patch, a due date of September 25 that has already passed as of this report.

### The Risk to Us
A VPN gateway is the door we build specifically to keep unauthenticated attackers out. This finding removes the lock from that door. Where we also use a Quantum gateway to segment our OT environment from the corporate network, or as the path for remote vendor and engineering support into that environment, the same finding puts that segmentation at risk. The management server finding is the one I want leadership to sit with a little longer, because it is quieter and it is worse. That server does not carry customer traffic. It carries the instructions that tell every gateway it manages what to allow and what to block. An attacker who takes the management server does not need to attack our gateways one at a time. They take the thing that tells the gateways what to do. I want to be precise here: there is no public evidence anyone has chained these two vulnerabilities together into a single attack. That is my own risk analysis connecting two vulnerabilities Check Point disclosed the same week, not a confirmed attacker playbook. I am treating it as a realistic worst case anyway, because the two systems are already connected in our own architecture whether or not any attacker has connected them yet.

### What We Are Doing
We are patching the gateways first, since they are the visible, internet-facing side of this and the side with the largest immediate exposure. We are patching the management server on the same track, not a slower one, because the blast radius argument above means it does not get to wait for a quieter week. Where a gateway sat exposed to the internet during the window between disclosure and patch, we are running a compromise assessment on that device before we consider it closed, not just applying the fix and moving on. Full detail on ownership, milestones, and status lives in the POAM at 06_POAM_Remediation.md.

### What We Need From Leadership
Three things. First, sign off on emergency change windows for the gateway and management server patches outside our normal change cadence, the three-day CISA deadline does not wait for the next scheduled maintenance window. Second, fund the compromise assessment on any device that was internet-reachable during the exposure window, that is not optional scope, it is the difference between patched and actually clean. Third, treat this as the latest entry in a pattern, not a one-off. This is the fourth internet-facing VPN or perimeter appliance in our case study history to land in the CISA KEV catalog with unauthenticated remote code execution this year, following Ivanti Connect Secure, SonicWall SMA1000, and Progress LoadMaster, and it arrives the same week as a comparable Citrix NetScaler disclosure. If our remote-access architecture keeps generating this same class of incident every few weeks, the fix leadership needs to fund next is not another emergency patch cycle. It is a review of whether this architecture is still the right one.

---

## Revision History

| Version | Date | Author | Changes |
|---|---|---|---|
| 1.0 | 2026-09-28 | Blaise Kingko | Initial publication |

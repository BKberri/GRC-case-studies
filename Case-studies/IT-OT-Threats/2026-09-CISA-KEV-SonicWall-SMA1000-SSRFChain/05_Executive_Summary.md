# Executive Summary
## 2026-09-CISA-KEV-SonicWall-SMA1000-SSRFChain
**Date:** 2026-09-07 | **Prepared by:** GRC Intelligence Program | **Classification:** Critical

## What Happened
A device that lets our (or a comparable organization's) remote employees securely connect into the internal network has two flaws that, combined, let an attacker take it over completely with no password at all. The federal government's cybersecurity agency confirmed active attacks and gave a 3-day window to fix it — one of the shortest deadlines they issue, reflecting how urgent this is.

## Why It Matters
This device is the front door for remote work. Complete control of it could let an attacker intercept employee logins, pivot into the internal network, or shut down remote access entirely. Public reporting also notes this is the third security event this year for this vendor's remote-access product line, following an earlier incident where backup security codes were reportedly stolen — a pattern worth watching closely if we run this vendor's equipment.

## What We Are Doing About It
- Confirm patch status and apply the vendor fix (firmware 12.4.3 build 03526+ or 12.5.0 build 02952+) immediately (Network Engineering, target: within 24 hours — ahead of the government's 3-day deadline)
- Engage vendor support to check for signs of compromise predating the patch, since attacks were confirmed active before the fix was available (Security Operations, target: within 48 hours)
- If we were affected by this vendor's July 2026 incident involving stolen backup security codes, treat that as a related risk factor requiring extra scrutiny during this remediation, not a separate closed issue (Security Operations, target: immediate)
- Prepare remote-workforce communications in case remediation requires a brief remote-access outage (IT Communications, target: within 24 hours)

## Bottom Line
This is an active, ongoing attack against a device that sits between our employees and our network — treat it with the same urgency the federal government is treating it with. If we run this equipment, the deadline is this week, not next sprint.

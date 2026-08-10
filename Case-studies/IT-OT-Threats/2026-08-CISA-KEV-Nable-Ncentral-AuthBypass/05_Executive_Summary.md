# Executive Summary
## 2026-08-CISA-KEV-Nable-Ncentral-AuthBypass
**Date:** 2026-08-10 | **Prepared by:** GRC Intelligence Program | **Classification:** Critical

## What Happened
The remote-management platform used to administer our (or our MSP's) computers fleet-wide has a login-bypass flaw that attackers are actively using. The vendor's first fix didn't fully work — attackers found a second way around it — so a corrected patch has now been issued.

## Why It Matters
This platform, by design, has full remote-control access to every computer it manages. Attackers who bypass its login aren't just getting into one system — they're getting the same fleet-wide control our own IT team has, and they're using the tool's own legitimate "remote control" feature to do it, which makes it harder to spot than typical malware.

## What We Are Doing About It
- Apply N-central's corrected hotfix (build 2026.3.1.7 or later) immediately (IT Operations / MSP Relationship Owner, target: within 24 hours)
- Audit all "Take Control" remote-access session history since August 1st for anything not tied to a known help-desk action (Security Operations, target: within 3 business days)
- Check all managed computers for unauthorized "Cloudflare Tunnel" software, which attackers used to maintain access (Security Operations, target: within 3 business days)
- If we use a third-party MSP for this platform, request written confirmation of their patch status and audit findings (Vendor Management, target: within 2 business days)

## Bottom Line
This is a "keys to everything" tool, and the vendor already got the first fix wrong once. We should verify remediation ourselves rather than taking the vendor's word for it, and we should assume some level of unauthorized access occurred until the audit proves otherwise.

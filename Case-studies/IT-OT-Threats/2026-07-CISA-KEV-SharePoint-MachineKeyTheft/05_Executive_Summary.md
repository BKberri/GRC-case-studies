# Executive Summary
## SharePoint Server Deserialization RCE with Machine Key Theft
**Date:** 2026-07-27 | **Prepared by:** GRC Intelligence Program | **Classification:** Critical

## What Happened
A critical flaw in our on-premises document management platform (SharePoint Server) is being actively exploited, with attackers not just breaking in but stealing a specific piece of cryptographic material — "machine keys" — that let them forge valid logins even after the security patch is applied. This is the third such SharePoint flaw exploited in an ongoing wave of attacks this month.

## Why It Matters
Normally, "apply the patch" ends an incident. Here it does not: an attacker who stole machine keys before the patch was applied can continue to log in as if they were a legitimate, trusted user indefinitely — the patch closes the original break-in point but not the back door the attacker may have already built. Given SharePoint typically holds sensitive internal and client documents, undetected persistent access is a serious ongoing exposure, not a closed incident.

## What We Are Doing About It
- Apply Microsoft's security patch to all on-premises SharePoint servers immediately
- Before rotating any credentials, first search for and remove any tools or backdoors an attacker may have planted — rotating too early lets an active attacker simply steal the new credentials too
- Once clean, rotate the affected cryptographic keys so any previously stolen material becomes worthless
- Review authentication logs for suspicious activity dating back to July 20, when public attack instructions first appeared
- Treat this and the related SharePoint issues from earlier this month as one connected incident, not separate one-off patches

## Bottom Line
Leadership should understand that "we patched it" is not the same as "the incident is over" for this specific issue — full closure requires confirming no attacker foothold remains and that stolen credentials, if any, have been invalidated.

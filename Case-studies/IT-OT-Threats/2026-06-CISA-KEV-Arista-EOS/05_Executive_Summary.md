# Executive Summary
## Case: CVE-2026-7473 — Arista EOS Tunnel Traffic Bypass (No Patch Planned)
**Date:** 2026-06-15 | **Prepared by:** Blaise Kingko

---

## The Situation

A security flaw in Arista's network operating system — widely used in data centers, campus networks, and financial services environments — has been confirmed as actively exploited and added to CISA's most-wanted vulnerability list. The flaw allows attackers to bypass network tunnel policies, meaning traffic can cross network segment boundaries that were supposed to be isolated from each other.

The most significant aspect of this finding is that **Arista has stated it will not release a patch**. The company's position is that fixing the code could break existing network configurations at deployed sites. This means the vulnerability will never be patched, and organizations must implement alternative controls or redesign their network architecture to address it.

## Business Risk

If our network architecture relies on Arista tunnel policy enforcement as a primary security boundary between sensitive segments — particularly in data center, OT/ICS, or financial trading network contexts — that boundary is now unreliable. An attacker with a foothold in one segment could potentially move laterally to adjacent segments that tunnel policy was supposed to isolate.

## What We Are Doing

1. We have audited all Arista EOS devices with tunnel configurations to identify which network segment boundaries rely on tunnel policy enforcement.
2. We are adding explicit interface-level ACLs on affected devices as a compensating control — these block unexpected tunnel traffic at the interface layer independently of the broken tunnel policy logic.
3. We have enabled enhanced traffic monitoring (NetFlow) on all affected devices to detect any exploitation activity.
4. For critical boundaries (OT/ICS zone separation, financial data environments), we are evaluating placement of additional inline firewalls to provide defense-in-depth independent of the EOS flaw.

## Decision Required

Because no patch is available, this risk requires **formal risk acceptance sign-off from the CISO and CRO**. Our compensating controls reduce but do not eliminate the residual risk. The risk acceptance documentation will be reviewed annually or upon any new intelligence about exploitation activity.

**Current Risk Level: HIGH — Permanent unpatched state. Compensating controls in place. Formal risk acceptance required.**

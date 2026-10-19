# Executive Summary, Ivanti Connect Secure VPN Gateway Breach (CVE-2026-104935)

**Case ID:** 2026-10-CISA-KEV-Ivanti-ConnectSecure-AuthBypass | **Audience:** CISO / Board

## What Happened

Attackers found and used a flaw in Ivanti Connect Secure, a remote-access VPN product many organizations use to let employees work from outside the office, to get inside company networks without a username or password. The attacks started before Ivanti told anyone the flaw existed.

## Why It Matters

If your organization uses Connect Secure for remote access and it is reachable from the internet (the normal setup), an attacker could have walked straight past the front door used by your remote workforce. Investigators also found the attackers used a second, related weakness that Ivanti has not yet fixed, so patching this one issue may not be the whole story for anyone who was already a target.

## What We're Doing

1. Confirming whether Connect Secure is in use and applying the vendor's emergency patch immediately, outside the normal update schedule.
2. Checking system logs against the published indicators of a prior break-in, since the attacks began before the public disclosure.
3. Treating this as a possible existing-compromise scenario, not just a patch-and-move-on item, until that check is complete.

## Business Risk in Plain Terms

A broken VPN gateway is not just an IT inconvenience, it is a potential open door directly into the internal network, used by exactly the system meant to keep that door locked for everyone except legitimate remote employees.

## Recommended Executive Action

Approve emergency change authority to patch all internet-facing Connect Secure appliances immediately, and fund a short compromise-assessment review given confirmed exploitation before public disclosure.

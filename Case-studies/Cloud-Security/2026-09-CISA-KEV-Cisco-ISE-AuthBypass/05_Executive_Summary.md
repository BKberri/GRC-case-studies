# Executive Summary
## 2026-09-CISA-KEV-Cisco-ISE-AuthBypass
**Date:** 2026-09-21 | **Prepared by:** GRC Intelligence Program | **Classification:** Critical

## What Happened
Cisco disclosed a critical flaw, already being actively exploited by attackers, in Identity Services Engine (ISE) — the system many organizations use to control which devices and users are allowed onto their network. The flaw lets an attacker with no valid credentials at all take full administrative control of ISE. The U.S. government's cyber agency (CISA) confirmed real-world attacks within a day of the disclosure and gave federal agencies a 3-day deadline to patch. Six related, less severe flaws in the same product were also fixed.

## Why It Matters
ISE isn't just another server — it's the system that decides who gets network access and to what. An attacker who takes it over can grant themselves trusted access to the network, disable security checks for other devices, or use the platform's own connection to the corporate identity directory as a launching point for a much bigger intrusion. Because this is confirmed to already be under active attack, any organization running an unpatched, internet-reachable ISE instance should treat this as a potential active incident, not a routine update.

## What We Are Doing About It
- Confirm whether we run Cisco ISE or ISE-PIC and identify every instance and its patch level (Network/Identity Team, target: within 24 hours)
- Apply the emergency vendor patch to all instances, prioritizing any internet- or DMZ-facing ISE nodes first, using a staged rollout to avoid a network-wide lockout from a botched upgrade (Network/Identity Team, target: within CISA's 3-day window)
- Review ISE administrative access logs and policy-change history since September 16th for any signs of unauthorized access predating the patch (Security Operations, target: within 5 business days)

## Bottom Line
This is the single most urgent finding in this week's sweep — a confirmed, actively exploited, full-takeover flaw in the system that controls network access itself. Leadership should expect this to take priority over other patch-cycle work this week, and should ask for a direct answer on whether the log review found any evidence of prior unauthorized access before considering this closed.

# Executive Summary — Second Cisco SD-WAN Manager Vulnerability (CVE-2026-20262)

## What Happened
For the second time in two weeks, the federal government's vulnerability watchlist (CISA KEV) flagged a flaw in Cisco's SD-WAN management software that attackers are actively exploiting. This new flaw lets an attacker who already has a valid login write malicious files to the system and seize full administrative control — separate from, and in addition to, the vulnerability we already addressed on 2026-06-15.

## Why It Matters
SD-WAN Manager is the single control point for how traffic moves between every office and data center connected to the network. An attacker with full control of it can redirect, inspect, or shut down traffic enterprise-wide. Two independently exploitable paths to that outcome being found within two weeks indicates sustained attacker interest in this platform.

## What We're Doing
Cisco has released a fix; we are deploying it on the same emergency timeline as the prior case (target: 2026-06-29). We are also auditing all administrator accounts on the platform and enabling multi-factor authentication, since this flaw requires a valid login — tightening who can log in reduces exposure while the patch rolls out.

## Bottom Line
This is a continuation of the same risk theme flagged two weeks ago, not a new category of exposure. The action is the same: patch promptly, tighten account access, and confirm both fixes are installed before considering this closed.

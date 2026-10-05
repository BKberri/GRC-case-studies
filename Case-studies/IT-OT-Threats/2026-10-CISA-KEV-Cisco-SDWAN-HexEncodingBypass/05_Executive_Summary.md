# Executive Summary, Cisco SD-WAN Manager Authentication Bypass (CVE-2026-76504)

**Case ID:** 2026-10-CISA-KEV-Cisco-SDWAN-HexEncodingBypass | **Audience:** CISO / Board

## What Happened

Cisco discovered, while helping a customer through a support case, that attackers were already breaking into Catalyst SD-WAN Manager, the system that centrally controls network routing across every office and data center connected by SD-WAN. The break-in method required no password at all: a simple trick in how web addresses are encoded let attackers in with full administrator rights.

## Why It Matters

If your organization runs Cisco Catalyst SD-WAN, this management system is effectively the central nervous system of your network. An attacker with administrator access to it can see everything about how your network is laid out, redirect traffic, or take connectivity down across every connected office at once.

## What We're Doing

1. Identifying every SD-WAN Manager instance in use and its current software version.
2. Preserving diagnostic evidence before upgrading, so Cisco's support team can check whether any instance was already compromised.
3. Upgrading all instances to Cisco's fixed software release, there is no interim workaround, so this cannot wait for the next scheduled maintenance window.

## Business Risk in Plain Terms

This is not a routine patch. It is confirmation that attackers were already inside the system that controls how the company's offices talk to each other and to the internet, discovered only because Cisco happened to notice it while helping someone else.

## Recommended Executive Action

Authorize an emergency maintenance window for all affected sites this week, and approve engagement of Cisco TAC for a compromise assessment rather than treating this as patch-and-move-on.

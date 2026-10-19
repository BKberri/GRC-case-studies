# Executive Summary, BeyondTrust Remote Support Nation-State Compromise (CVE-2026-102764)

**Case ID:** 2026-10-CISA-KEV-BeyondTrust-RemoteSupport-AuthBypass | **Audience:** CISO / Board

## What Happened

A suspected foreign intelligence-linked hacking group quietly broke into BeyondTrust's Remote Support product, a tool widely used to give IT staff and support teams privileged remote access to systems, and used it undetected for roughly seven weeks before the vendor even knew about it. The attackers gained full administrative control, installed hidden backdoor tools, and deliberately erased logs to cover their tracks.

## Why It Matters

Remote-support tools are deliberately given broad, trusted access so IT staff can fix problems anywhere. That same design means a compromise of the tool itself is a compromise of everything it was ever used to touch. Because the attackers wiped logs, it may not be possible to prove a clean bill of health for every system this tool accessed during the affected window, only that nothing suspicious has been found so far.

## What We're Doing

1. Confirming whether BeyondTrust Remote Support is in use, and patching every self-hosted installation immediately if not already covered by automatic vendor updates.
2. Treating any internet-reachable instance that ran a vulnerable version since late August as a potential compromise, not assuming the patch alone clears it.
3. Reviewing for the attacker's known tools and techniques (hidden web shell, tunneling malware, unusual administrator account activity) across systems the tool was used to access.

## Business Risk in Plain Terms

This is a worst-case scenario for a trusted-access tool: the keys meant for your own support staff were, for close to two months, also in the hands of a sophisticated foreign intelligence actor, and the normal way you'd prove nothing else happened, the logs, was specifically targeted and erased.

## Recommended Executive Action

Approve an independent forensic review of every system BeyondTrust Remote Support was used to access during the exploitation window, in addition to immediate patching, and brief any client or partner whose environment may have been reachable through this tool if your organization provides managed IT or support services.

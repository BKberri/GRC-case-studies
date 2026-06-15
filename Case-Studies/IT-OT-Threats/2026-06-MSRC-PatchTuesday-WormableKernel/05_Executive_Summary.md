# Executive Summary
## Case: CVE-2026-45657 / CVE-2026-47291 — Microsoft June 2026 Patch Tuesday: Wormable Kernel & HTTP.sys RCE
**Date:** 2026-06-15 | **Prepared by:** Blaise Kingko | **Audience:** CISO, CTO, Board Risk Committee

---

## The Situation

Microsoft released its largest-ever security update on June 10, 2026, patching 198 to 208 vulnerabilities in a single day. Two of those vulnerabilities are rated the highest possible severity (9.8 out of 10) and require immediate emergency action.

The first — a flaw in the Windows operating system kernel — has been characterized by leading security researchers as potentially **wormable**, meaning it can spread from one computer to another automatically without anyone clicking anything or opening any files. The last time the industry saw a vulnerability of this type was in 2017, when EternalBlue (a similar Windows kernel flaw) was used to build WannaCry and NotPetya — two cyberattacks that collectively caused over $10 billion in damages globally and shut down hospitals, banks, shipping companies, and governments.

The second — a flaw in Windows' web server component — allows an attacker to take full control of any internet-facing Windows web server by sending it a single malicious message, with no password needed.

Neither flaw has been confirmed as actively exploited yet. However, once a fix is published, attackers immediately analyze it to build the attack tool. Historical data shows that functional exploits for wormable vulnerabilities typically emerge within 2–8 weeks of patch release.

## What We Are Doing

1. Emergency patch deployment has been initiated across all Windows servers and cloud VMs — targeting 72-hour completion.
2. Network segmentation controls are being reviewed and tightened to reduce the blast radius if the worm exploit becomes public before patching is complete.
3. A registry configuration change (available from Microsoft as a temporary workaround) is being applied to all web servers to neutralize the HTTP.sys flaw until the full patch is deployed.
4. Backup integrity has been verified and immutable backup coverage is being extended as a ransomware preparedness measure.

## What Leadership Should Know

- **This is not a routine monthly update.** Treating it as such exposes the organization to WannaCry-level consequences.
- **The risk window is open right now.** Attackers are actively analyzing Microsoft's patches. We have days to weeks, not months.
- **Microsoft patches cloud infrastructure — but we are responsible for our VMs.** Azure and AWS manage the underlying hardware. Every Windows virtual machine we own in the cloud requires a guest OS update from us.
- **No confirmed exploitation yet** means we still have time to prevent, not just respond. Every hour of delay narrows that window.

## Decision Required

Emergency change control approval is needed to bypass the standard 14-day patch testing window and proceed with accelerated deployment within 72 hours. The risk of deploying without a standard testing cycle is significantly lower than the risk of a WannaCry-class ransomware event against an unpatched estate.

**Current Risk Level: CRITICAL — Emergency patching authorization required.**

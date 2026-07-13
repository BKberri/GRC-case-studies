# Executive Summary
## AWS Linux Kernel Privilege-Escalation Family ("Copy.fail" / "DirtyFrag") — Bulletin 2026-030

**Audience:** CISO / Board | **Date:** 2026-06-08 | **Risk Rating:** High

---

**What happened:**
AWS published an active bulletin tracking a family of Linux kernel flaws that let a low-level process on a shared server gain full administrative control of that server. Technical proof-of-concept code for these flaws is already public. AWS has patched the parts of its cloud it controls directly, but any systems we manage ourselves on AWS — particularly our container clusters and virtual machines — need us to apply the fix.

**Why it matters:**
If exploited, an attacker who already has a small foothold (for example, through a compromised application or container) could take over the entire underlying server, potentially reaching other customers' or our own other workloads on the same shared infrastructure. This is exactly the kind of "shared responsibility gap" that regulators and auditors scrutinize closely — AWS securing its side does not secure ours.

**What we're doing:**
We are inventorying every server and container cluster running on the affected software versions, scheduling a rolling replacement to the patched versions within the next two weeks, and validating completion through our automated security-scanning tools. No customer-facing disruption is expected because replacements will be done in rotation, one batch at a time.

**Bottom line for leadership:**
This is a "patch before it's exploited" situation, not an active breach. The cost of patching now is near zero engineering time; the cost of not patching — a confirmed server takeover — would mean a multi-day operational disruption, potential regulatory notification obligations, and lasting damage to customer trust in our cloud isolation guarantees. We recommend treating the two-week patch window as a hard deadline.

---

## Update — 2026-06-15

Good news on a partial front: AWS has completed its portion of the fix. All AWS-managed Fargate environments are now patched as of today, June 15, 2026.

The remaining work is on our side: any EKS clusters using EC2-backed worker nodes, any servers running Bottlerocket, and any self-managed Linux EC2 instances need to be rotated to the patched builds AWS has already published. Cloud platform engineering is running this as a planned rolling update this week, with full remediation expected by June 22, 2026.

**Current risk level:** High → reducing to Low upon completion of customer-side node rotation. No active exploitation of this vulnerability in AWS environments has been confirmed; the risk is theoretical but real if an attacker first gains a foothold in a container environment.

**Action: no executive decision required. Tracking to the June 22 remediation target.**

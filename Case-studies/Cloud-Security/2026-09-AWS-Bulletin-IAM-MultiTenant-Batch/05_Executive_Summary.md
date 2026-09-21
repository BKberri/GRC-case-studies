# Executive Summary
## 2026-09-AWS-Bulletin-IAM-MultiTenant-Batch
**Date:** 2026-09-21 | **Prepared by:** GRC Intelligence Program | **Classification:** High

## What Happened
AWS published fixes for two separate flaws in tools organizations use to enforce least-privilege access and workload isolation. One, in a tool called TEAM used to grant temporary elevated AWS account access, could have let an ordinary application user get more access than intended. The other, in Amazon's managed Kubernetes network-isolation feature, could let workloads in different namespaces reach each other when they shouldn't be able to — under a specific naming-pattern condition. Neither is known to have been exploited.

## Why It Matters
Both tools exist specifically to enforce boundaries — "only grant temporary elevated access when needed" and "keep these workloads isolated from each other." A flaw in the tool meant to enforce a boundary is a different kind of risk than an ordinary application bug: it means the safeguard itself needs periodic re-verification, not just a one-time setup-and-forget.

## What We Are Doing About It
- If we use TEAM for temporary elevated AWS access, upgrade to the fixed version and review recent access grants for anything unintended (Cloud Security Team, target: within 1 week)
- If we run Amazon EKS with NetworkPolicy-based namespace isolation, upgrade the affected components and audit namespace names for the collision pattern (Cloud/Platform Engineering, target: within 1 week)
- Add periodic testing of both tools' actual enforcement behavior to our standing cloud security verification process, rather than relying on initial setup alone (Cloud Security Team, target: next quarterly review)

## Bottom Line
No emergency here, but a useful reminder: the tools we use to enforce access and isolation boundaries need the same ongoing scrutiny as anything else we run in production. Leadership should expect a standing verification step to come out of this, not just a one-time patch.

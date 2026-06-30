# Business Impact Analysis — UPDATED
## Case: AWS Bulletin 2026-030 — Linux Kernel "Copy.fail / DirtyFrag" LPE Family
**Date Updated:** 2026-06-15 | **Analyst:** Blaise Kingko

---

## BIA Update Summary

The AWS-managed Fargate platform is now fully patched as of June 15, 2026. Business impact exposure has decreased materially for organizations that rely on Fargate-managed workloads. The remaining business impact risk is concentrated in **customer-managed EKS node groups, Bottlerocket hosts, and self-managed EC2 instances** that have not yet been rotated to patched kernel builds.

---

## Residual Business Impact (Customer-Managed Compute Only)

| Scenario | Probability | Business Impact |
|---|---|---|
| LPE exploit chained with container escape on unpatched EKS node | Low (no public PoC; attacker needs prior foothold) | Medium — attacker achieves root on worker node; can access kubelet credentials; potential lateral movement to other pods on same node |
| LPE exploit on unpatched self-managed EC2 instance | Low | Medium — root on EC2 instance; access to instance profile credentials; potential pivot to AWS services |
| LPE exploit after successful remote exploit (chained attack) | Very Low | High — full host compromise if chained with a separate RCE |

---

## Updated Financial Exposure

Original BIA estimated $2M–$15M exposure for fully unpatched AWS estate. With Fargate patched by AWS, exposure is now concentrated in customer-managed compute:

- Fargate-only organizations: exposure substantially reduced — **no customer action required for Fargate workloads**
- EKS EC2-backed organizations: exposure unchanged until node rotation complete
- Mixed-compute organizations: proportional to percentage of unpatched self-managed compute remaining

---

## RTO/RPO Impact of Node Rotation

Node group rotation is a planned operational event (not a security incident), but requires workload rescheduling. Typical impact:
- EKS node rotation: 2–4 hours per node group (rolling update with cordon/drain)
- Bottlerocket update: 15–30 minutes per host
- Risk: No business continuity impact if rolling update strategy is used; impact is operational scheduling only

# Plan of Action & Milestones (POA&M) — UPDATED
## Case: AWS Bulletin 2026-030 — Linux Kernel "Copy.fail / DirtyFrag" LPE Family
**Date Updated:** 2026-06-15 | **Analyst:** Blaise Kingko

---

## POA&M Status Update

| Milestone | Original Due | Status | Notes |
|---|---|---|---|
| AWS Fargate platform patch (all regions) | 2026-06-15 | ✅ CLOSED | AWS confirmed complete per bulletin update June 11 |
| Bottlerocket v1.61.0 release | 2026-06-15 | ✅ CLOSED (AWS-side) | v1.61.0 GA; customer update step M3 now unblocked |
| EKS-optimized AMI patched build published | 2026-06-10 | ✅ CLOSED (AWS-side) | Patched AMI available; customer rotation is M2 |

---

## Remaining Customer-Side Milestones

| Milestone | Action | Owner | Due Date | Status |
|---|---|---|---|---|
| **M2 — EKS Node Group Rotation** | Run `aws eks update-nodegroup-version` for all EKS managed node groups to rotate to patched AMI. Use rolling update (maxUnavailable=1) to avoid workload disruption. Verify via `kubectl get nodes` — all nodes should show patched kernel version. | Cloud Platform Engineering | 2026-06-22 | In Progress |
| **M3 — Bottlerocket Update** | On all Bottlerocket hosts: run `apiclient update apply && apiclient update boot-into-updated`. Confirm v1.61.0 kernel post-update. | Cloud Platform Engineering | 2026-06-22 | Pending |
| **M4 — Self-Managed EC2 Kernel Update** | Apply ALAS2023 kernel update to all Amazon Linux 2023 EC2 instances. For RHEL/Ubuntu EC2: apply kernel update from respective vendor security advisories. Reboot required. | Cloud Ops / Linux Sysadmin | 2026-06-22 | Pending |
| **M5 — CSPM Verification Scan** | Run AWS Security Hub / CSPM tool scan confirming zero non-compliant kernel versions across entire AWS estate. Export compliance report for CISO review. | Cloud Security Architecture | 2026-06-23 | Pending |
| **M6 — Risk Register Update** | Update RR-006 in place: reduce Likelihood from 4→3 (Fargate patched); add revision note "REVISED 2026-06-15 — Fargate patches complete; customer EKS/Bottlerocket action ongoing." After M5 completes: further update to Likelihood 1, Risk Score 3, Rating Low. | GRC Program | 2026-06-23 | In Progress |

---

## Success Metrics

| Metric | Target |
|---|---|
| EKS node groups rotated to patched AMI | 100% by June 22 |
| Bottlerocket hosts updated to v1.61.0 | 100% by June 22 |
| Self-managed EC2 kernel updated | 100% by June 22 |
| CSPM scan: non-compliant kernels | 0 by June 23 |
| Risk Register RR-006 updated | June 15 (Likelihood revision); June 23 (final closure) |

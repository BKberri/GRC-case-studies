# Plan of Action & Milestones (POA&M) — Remediation Plan
## Case: AWS Bulletin 2026-030 — Copy.fail / DirtyFrag Linux Kernel LPE Family
**Risk ID:** RR-006 | **Opened:** 2026-06-08 | **Target Closure:** 2026-06-22

| # | Action Item | Specific Task | Owner | Start | Due | Status |
|---|---|---|---|---|---|---|
| 1 | Asset inventory | Query AWS Config / CSPM for all EC2, EKS node groups, ECS container instances, and Bottlerocket hosts running kernel versions 4.14, 5.4, 5.10, 5.15, 6.1, 6.12, or 6.18 | Cloud Platform Engineering | 2026-06-09 | 2026-06-11 | Open |
| 2 | Patch artifact staging | Pull patched Amazon Linux AMIs and Bottlerocket v1.61.0+ images into the internal AMI pipeline / golden-image registry | Cloud Platform Engineering | 2026-06-09 | 2026-06-12 | Open |
| 3 | EKS node-group rotation | Execute rolling replacement of EKS-optimized AMIs across all clusters using managed node group update strategy (max-unavailable = 1) | Cloud Platform Engineering | 2026-06-12 | 2026-06-18 | Open |
| 4 | EC2 / ECS host rotation | Replace EC2 instances and ECS container instances via Auto Scaling Group instance refresh with patched AMIs | Cloud Platform Engineering | 2026-06-12 | 2026-06-18 | Open |
| 5 | Fargate validation | Confirm all Fargate workloads are running on platform versions issued on/after 2026-06-09; force redeploy any stragglers | Cloud Platform Engineering | 2026-06-10 | 2026-06-15 | Open |
| 6 | Compliance verification | Re-scan all production accounts via CSPM/Inspector; confirm 0% non-compliant kernel versions remain | GRC / Security Architecture (Blaise Kingko) | 2026-06-18 | 2026-06-20 | Open |
| 7 | Control evidence capture | File scan results, change records, and rotation logs as SI-2 / RA-5 audit evidence for SOC 2 and ISO 27001 surveillance | GRC / Security Architecture (Blaise Kingko) | 2026-06-20 | 2026-06-22 | Open |
| 8 | Executive close-out report | Brief cloud governance board on completion percentage, residual exceptions (if any), and final risk-rating downgrade to Medium/Low | GRC / Security Architecture (Blaise Kingko) | 2026-06-22 | 2026-06-22 | Open |

### Specific Patch References
- Amazon Linux: apply kernel updates per AL1/AL2/AL2023 advisory tracked under bulletin 2026-030-AWS
- Bottlerocket: upgrade to **v1.61.0** or later
- EKS: update to current EKS-optimized AMI release tagged post-2026-06-04
- Fargate: confirm platform version ≥ release dated 2026-06-09

### Escalation Trigger
If any production account remains non-compliant past 2026-06-22, escalate to CISO for risk-acceptance sign-off or emergency change-freeze override.

---

## Update — 2026-06-15

**Milestones closed (AWS-side):**

| Milestone | Original Due | Status | Notes |
|---|---|---|---|
| AWS Fargate platform patch (all regions) | 2026-06-15 | ✅ CLOSED | AWS confirmed complete per bulletin update June 11 |
| Bottlerocket v1.61.0 release | 2026-06-15 | ✅ CLOSED (AWS-side) | v1.61.0 GA; customer update step M3 now unblocked |
| EKS-optimized AMI patched build published | 2026-06-10 | ✅ CLOSED (AWS-side) | Patched AMI available; customer rotation is M2 |

**Remaining customer-side milestones:**

| Milestone | Action | Owner | Due Date | Status |
|---|---|---|---|---|
| M2 — EKS Node Group Rotation | Run `aws eks update-nodegroup-version` for all managed node groups; rolling update (maxUnavailable=1); verify via `kubectl get nodes` | Cloud Platform Engineering | 2026-06-22 | In Progress |
| M3 — Bottlerocket Update | `apiclient update apply && apiclient update boot-into-updated` on all hosts; confirm v1.61.0 post-update | Cloud Platform Engineering | 2026-06-22 | Pending |
| M4 — Self-Managed EC2 Kernel Update | Apply ALAS2023 (or vendor advisory for RHEL/Ubuntu) kernel update; reboot required | Cloud Ops / Linux Sysadmin | 2026-06-22 | Pending |
| M5 — CSPM Verification Scan | Run Security Hub/CSPM scan confirming zero non-compliant kernel versions; export report for CISO review | Cloud Security Architecture | 2026-06-23 | Pending |
| M6 — Risk Register Update | Update RR-006 in place (Likelihood 4→3 now; →1 after M5 completes, Risk Score 3/Low) | GRC Program | 2026-06-23 | In Progress |

**Success metrics:** 100% EKS node groups rotated, 100% Bottlerocket hosts updated, 100% self-managed EC2 kernel updated — all by June 22; 0 non-compliant kernels on CSPM scan by June 23; RR-006 fully closed by June 23.

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

# Business Impact Analysis (BIA)
## Case: AWS Bulletin 2026-030 — Copy.fail / DirtyFrag Linux Kernel LPE Family

---

### 1. Process / Asset Criticality
**Affected Asset Class:** Compute tenancy underpinning containerized production workloads (EKS clusters, ECS instances, EC2 fleets, Bottlerocket hosts, SageMaker/EMR compute).
**Criticality Tier:** Tier 1 — supports customer-facing applications, CI/CD pipelines, and data-processing workloads across the AWS multi-account landing zone.

### 2. Impact Categories

**Operational Impact**
A successful host-compromise event would force emergency node-group replacement, workload migration, and forensic isolation across affected accounts — a multi-day operational disruption even before considering data-handling obligations.

**Financial Impact**
Estimated incident-response and remediation cost band: $150K–$600K (forensic investigation, emergency engineering hours, potential customer notification, and regulatory engagement) if exploitation occurs prior to patching. Patch-now cost is near-zero (engineering time for rolling node replacement).

**Reputational Impact**
A confirmed container-breakout incident in a multi-tenant cloud environment would materially damage customer trust, particularly for customers under FedRAMP, SOC 2, or financial-services regulatory scrutiny who rely on tenant-isolation assurances.

**Regulatory / Legal Impact**
If host compromise leads to cross-tenant data exposure, notification obligations may be triggered under SEC cybersecurity disclosure rules (4-business-day material incident reporting), state breach-notification statutes, and — for regulated customers — GLBA Safeguards Rule or NYDFS Part 500 reporting chains.

### 3. Recovery Objectives
- **RTO (Recovery Time Objective):** 8 hours for affected node-group replacement and workload restoration
- **RPO (Recovery Point Objective):** Near-zero — stateless container workloads with externalized persistent storage (EBS/EFS/RDS) should not lose data during node replacement

### 4. Maximum Tolerable Downtime (MTD)
24 hours for Tier 1 production workloads before SLA breach and material customer/financial impact accrues.

### 5. Dependencies
- AWS control-plane patch rollout (outside customer control; tracked via the bulletin)
- Internal CI/CD and infrastructure-as-code pipelines to roll node groups safely without service interruption
- CSPM/vulnerability management tooling to confirm patch convergence

### 6. BIA Conclusion
This is a **patch-before-exploit** scenario rather than an active-incident scenario. The business impact of *inaction* (a successful LPE chain in production) substantially outweighs the negligible cost of timely, orchestrated node replacement. Recommend treating the 14-day remediation window as a hard internal SLA, independent of the absence of a CISA KEV listing.

---

## Update — 2026-06-15

AWS-managed Fargate is now fully patched, materially reducing exposure for Fargate-only workloads (no customer action required there). Residual business impact is now concentrated in customer-managed compute:

| Scenario | Probability | Business Impact |
|---|---|---|
| LPE chained with container escape on unpatched EKS node | Low (no public PoC; attacker needs prior foothold) | Medium — root on worker node, kubelet credential access, potential lateral movement |
| LPE on unpatched self-managed EC2 instance | Low | Medium — root on instance, instance-profile credential access, potential pivot to AWS services |
| LPE after a separate successful remote exploit (chained attack) | Very Low | High — full host compromise |

**Updated financial exposure:** original estimate ($2M–$15M for a fully unpatched estate) is now scoped down — Fargate-only organizations require no further action; exposure for EKS EC2-backed and mixed-compute organizations is proportional to remaining unpatched self-managed compute.

**RTO/RPO impact of remediation itself:** node rotation is a planned operational event, not an incident — EKS node rotation runs 2–4 hours per node group (rolling, cordon/drain), Bottlerocket updates 15–30 minutes per host, with no business-continuity impact if the rolling-update strategy is followed.

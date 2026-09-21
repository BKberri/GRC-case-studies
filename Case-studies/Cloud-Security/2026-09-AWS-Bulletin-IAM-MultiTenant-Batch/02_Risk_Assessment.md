# Risk Assessment
## 2026-09-AWS-Bulletin-IAM-MultiTenant-Batch

## Risk Scoring
| Method | Score | Rating |
|---|---|---|
| Likelihood x Impact Matrix | 3 x 4 = 12 | High |
| CVSS Base Score | Not published (qualitative High per AWS "Important" label) | High |
| FAIR Qualitative | Moderate-high exposure — both require an existing authenticated foothold (application user for TEAM, cluster access for EKS), bounding the realistic attacker population, but the exploitation technique itself requires no special skill once that foothold exists | High |

## Risk Narrative
Likelihood is scored at 3 (technically feasible) because both vulnerabilities require the attacker already hold some authenticated foothold — an application user account for TEAM, or workload/namespace access within the EKS cluster for the NetworkPolicy bypass — rather than being externally reachable, unauthenticated flaws. Once that foothold exists, however, exploitation is straightforward: no specialized research or novel technique is required for either. Impact is scored at 4 (significant) because both findings defeat a control specifically built to enforce least-privilege or isolation — TEAM's entire purpose is limiting standing elevated access, and NetworkPolicy's entire purpose is enforcing workload isolation, so a flaw in either has outsized governance significance beyond its technical severity alone.

## Framework Control Gaps
- **NIST 800-53 AC-6 (Least Privilege):** Root cause for TEAM — a tool built to enforce least-privilege, time-boxed access instead allowed unintended privilege assignment.
- **NIST 800-53 SC-7 (Boundary Protection) / AC-4 (Information Flow Enforcement):** Root cause for the EKS finding — namespace-level network boundary enforcement failed due to an identifier-collision edge case.
- **NIST CSF 2.0 PR.AA-05 (Access permissions and authorizations are managed):** Both findings show that access-governance tooling itself requires the same vulnerability-management rigor as any other production system, not an assumption of correctness because it exists to enforce security.
- **ISO 27001:2022 A.8.22 (Segregation of Networks):** Directly applicable to the EKS NetworkPolicy bypass — network segmentation controls must be independently verified, not assumed reliable by design.

## Residual Risk Statement
After upgrading TEAM to v1.5.1+ and the EKS VPC CNI/Network Policy Agent components to their fixed versions, residual risk drops to Low for both findings. Organizations using TEAM should additionally review recent elevated-access grants for any that may have resulted from the flawed privilege-assignment logic prior to patching. Organizations using EKS NetworkPolicy for tenant isolation should audit existing namespace names for hyphen-adjacency collision risk even after patching, since the underlying identifier-construction pattern is a useful data point for broader namespace-naming governance.

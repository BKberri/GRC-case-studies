# Plan of Action & Milestones (POA&M)
## 2026-09-AWS-Bulletin-IAM-MultiTenant-Batch
**Date Opened:** 2026-09-21 | **Source:** AWS Security Bulletins 2026-112-AWS, 2026-113-AWS | **Risk Rating:** High | **Target Closure:** 2026-09-28

## POA&M Table
| Item ID | Weakness / Finding | Affected System | Control Reference | Responsible Role | Planned Action | Milestone 1 | Milestone 2 | Milestone 3 | Target Date | Status |
|---|---|---|---|---|---|---|---|---|---|---|
| POA-202609-019 | Incorrect privilege assignment allowing unintended elevated access (CVE-2026-86830) | TEAM (IAM Identity Center elevated access) | NIST 800-53 AC-6 | Cloud Security Lead | Upgrade to TEAM v1.5.1+ and review recent access grants | 2026-09-23: Confirm TEAM deployment and current version | 2026-09-25: Upgrade to v1.5.1+ | 2026-09-26: Review access-grant history for anomalies | 2026-09-26 | Open |
| POA-202609-020 | Pod identifier collision bypasses cross-namespace NetworkPolicy enforcement (CVE-2026-86831) | Amazon EKS VPC CNI / Network Policy Agent | NIST 800-53 SC-7 | Cloud/Platform Engineering Lead | Upgrade affected components and audit namespace naming | 2026-09-24: Upgrade VPC CNI Add-on and Network Policy Agent | 2026-09-26: Audit existing namespace names for collision risk | N/A | 2026-09-26 | Open |
| POA-202609-021 | No standing verification process confirms access-governance tooling enforces intended boundaries | TEAM, EKS NetworkPolicy (process gap) | NIST CSF 2.0 PR.AA-05 | Cloud Security Team | Add periodic synthetic verification testing to standing process | 2026-09-28: Define test cases for both tools | N/A | N/A | 2026-09-28 (next quarterly review) | Open |

## Remediation Narrative
Upgrade TEAM to v1.5.1 or later and the affected EKS components (VPC CNI Managed Add-on to v1.22.4+, Network Policy Agent to v1.4.0+), then complete the access-grant and namespace-naming reviews to confirm no unintended access or cross-namespace exposure resulted prior to patching.

## Compensating Controls
Until the EKS upgrade is complete, avoid hyphens in namespace names as an interim workaround per AWS guidance. No interim workaround is available for the TEAM finding beyond restricting which application users can request elevated access pending the upgrade.

## Verification & Closure Criteria
Closure requires: (1) confirmed upgrade of TEAM to v1.5.1+; (2) confirmed upgrade of EKS VPC CNI Add-on and Network Policy Agent to fixed versions; (3) completed access-grant review for TEAM with no unresolved anomalies; (4) completed namespace-naming audit for EKS; (5) test cases defined for the standing periodic verification process.

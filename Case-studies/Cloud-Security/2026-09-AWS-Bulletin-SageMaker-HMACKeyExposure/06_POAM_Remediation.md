# Plan of Action & Milestones (POA&M)
## 2026-09-AWS-Bulletin-SageMaker-HMACKeyExposure
**Date Opened:** 2026-09-07 | **Source:** AWS Security Bulletin 2026-093-AWS | **Risk Rating:** High | **Target Closure:** 2026-09-21

## POA&M Table
| Item ID | Weakness / Finding | Affected System | Control Reference | Responsible Role | Planned Action | Milestone 1 | Milestone 2 | Milestone 3 | Target Date | Status |
|---|---|---|---|---|---|---|---|---|---|---|
| POA-202609-004 | Cleartext HMAC signing key exposure enables cross-user code execution (CVE-2026-83551) | SageMaker Python SDK (`@step`/`@remote` pipelines) | NIST 800-53 SC-28, IA-5 | ML Engineering Lead | Upgrade SDK to v3.11.0+ / v2.256.0+ | 2026-09-08: Inventory all SageMaker Studio domains/accounts using `@step`/`@remote` | 2026-09-12: Upgrade SDK across all environments | 2026-09-14: Rotate all pipeline HMAC signing keys in use pre-patch | 2026-09-14 | Open |
| POA-202609-005 | CloudTrail log review for cross-user pipeline execution during exposure window | Shared SageMaker environments | NIST 800-53 AU-6 | Security Operations | Review pipeline execution logs for signature/owner mismatches | 2026-09-15: Pull CloudTrail logs for affected domains | 2026-09-19: Complete anomaly analysis | 2026-09-19: Escalate to IR if any mismatch found | 2026-09-19 | Open |
| POA-202609-006 | Shared AI/ML environment tenant-isolation assumption not independently verified | AI/ML platform architecture | NIST AI RMF MAP 5.1; ISO 42001 6.1.2 | AI Governance / Cloud Architecture | Evaluate account/domain segregation for higher-sensitivity ML workloads | 2026-09-21: Present findings at quarterly architecture review | N/A | N/A | 2026-09-21 | Open |

## Remediation Narrative
Upgrade the SageMaker Python SDK across every environment where the `@step`/`@remote` decorator pattern is in use, prioritizing shared/multi-tenant SageMaker Studio domains. Because the underlying credential exposure predates this patch, rotate any HMAC signing keys that were in circulation prior to the upgrade rather than assuming the patch alone resolves already-exposed key material.

## Compensating Controls
Until the SDK upgrade and key rotation are complete, restrict shared SageMaker Studio domain membership to teams with an equivalent trust level where feasible, and monitor CloudTrail for pipeline execution events whose signing identity does not match the expected owning principal.

## Verification & Closure Criteria
Closure requires: (1) confirmed SDK upgrade across all in-scope environments; (2) confirmed rotation of all pre-patch HMAC signing keys; (3) completed CloudTrail log review with no unresolved cross-user execution anomalies, or an escalated incident record if found; (4) a documented decision from the architecture review on whether shared-domain segregation is warranted for higher-sensitivity ML workloads.

# Control Mapping
## 2026-09-AWS-Bulletin-IAM-MultiTenant-Batch

## Applicable Frameworks
NIST CSF 2.0 and NIST 800-53 Rev 5 for least-privilege and boundary-protection control gaps; ISO 27001:2022 for network segregation; CIS Controls v8 and AWS Well-Architected Security Pillar for cloud-specific remediation guidance.

## Control Mapping Table
| Framework | Control ID | Control Name | Applicability | Gap / Status |
|---|---|---|---|---|
| NIST 800-53 | AC-6 | Least Privilege | TEAM's privilege-assignment logic allowed unintended elevated access | Gap (vendor, fixed) |
| NIST 800-53 | SC-7 | Boundary Protection | EKS NetworkPolicy enforcement bypassed via pod-identifier collision | Gap (vendor, fixed) |
| NIST CSF 2.0 | PR.AA-05 | Access permissions and authorizations are managed | Access-governance tooling requires independent vulnerability verification | Organizational — verify |
| ISO 27001:2022 | A.8.22 | Segregation of Networks | Namespace-level network segmentation should be independently audited | Organizational — verify |
| CIS Controls v8 | Control 6 | Access Control Management | Applies directly to TEAM's elevated-access-grant function | Organizational — verify |
| AWS Well-Architected | SEC-2 | Identity and Access Management | Both findings sit squarely within the Security Pillar's IAM design principles | Organizational — verify |

## Control Narrative
Both findings share a common governance lesson worth elevating beyond the individual patch: tools an organization adopts specifically to strengthen least-privilege or isolation posture (TEAM for time-boxed access, NetworkPolicy for namespace isolation) are themselves production software subject to the same vulnerability-management discipline as anything else — adopting a security-focused tool is not a substitute for continuing to verify it works as intended. This program recommends organizations using either tool add a periodic verification step (a synthetic test confirming TEAM grants only intended scope, or a namespace-isolation test confirming NetworkPolicy actually blocks cross-namespace traffic) rather than relying solely on the tool's documented behavior.

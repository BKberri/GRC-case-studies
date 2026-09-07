# Control Mapping
## 2026-09-AWS-Bulletin-SageMaker-HMACKeyExposure

## Applicable Frameworks
NIST AI RMF and ISO 42001 for AI/ML platform tenant-isolation and impact-assessment gaps; NIST CSF 2.0 and NIST 800-53 Rev 5 for the underlying credential-protection and access-management control failures.

## Control Mapping Table
| Framework | Control ID | Control Name | Applicability | Gap / Status |
|---|---|---|---|---|
| NIST 800-53 | SC-28 | Protection of Information at Rest | HMAC signing key stored/returned in cleartext without owner-scoping | Gap (vendor, now fixed) |
| NIST 800-53 | IA-5 | Authenticator Management | Signing credential was not adequately protected as an authenticator tied to a specific principal | Gap (vendor, now fixed) |
| NIST CSF 2.0 | PR.AA-05 | Access permissions and authorizations are managed | Shared SageMaker environment did not enforce per-user isolation of pipeline signing credentials | Gap |
| NIST AI RMF | MAP 5.1 | Likelihood and magnitude of impacts documented | Cross-tenant impact of a shared ML platform credential was not identified prior to disclosure | Gap (vendor) |
| ISO 42001 | 6.1.2 | AI risk assessment | Multi-tenant AI/ML platform deployments warrant explicit tenant-isolation risk assessment | Gap (organizational, ongoing) |

## Control Narrative
This finding is a conventional credential-protection failure (SC-28, IA-5) with AI-governance-relevant consequences because of where it sits: a shared ML platform where the isolation boundary between users is assumed rather than verified. The fix (SDK upgrade) closes the immediate technical gap, but the control gap this program flags for the organization's standing AI governance posture is the assumption itself — that account-level IAM authentication is sufficient to isolate one data scientist's ML pipeline execution from another's within a shared SageMaker domain. Combined with this week's MCP-server findings (`2026-09-AWS-Bulletin-MCP-Server-InputValidation`), the pattern across all three AWS AI/ML-platform disclosures this run is the same: AWS's rapid feature expansion in AI/ML tooling (agent MCP servers, low-friction pipeline decorators) is introducing new implicit trust boundaries faster than operators' mental models of "what isolates what" are being updated. This program recommends treating multi-tenant SageMaker/AI-platform isolation as a recurring architecture-review topic rather than a closed item after this single patch.

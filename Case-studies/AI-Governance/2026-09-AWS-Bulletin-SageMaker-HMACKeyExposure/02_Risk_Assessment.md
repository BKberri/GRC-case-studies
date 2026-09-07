# Risk Assessment
## 2026-09-AWS-Bulletin-SageMaker-HMACKeyExposure

## Risk Scoring
| Method | Score | Rating |
|---|---|---|
| Likelihood x Impact Matrix | 3 x 4 = 12 | High |
| CVSS Base Score | 7.2 (High) | High |
| FAIR Qualitative | Moderate-high loss exposure — requires an existing authenticated foothold on the shared account, bounding the realistic attacker population to insiders or already-compromised lower-privileged accounts, but the exploit path itself (read cleartext key, forge signature) requires no special skill once that foothold exists | High |

## Risk Narrative
Likelihood is scored at 3 (technically feasible) rather than lower because, while exploitation requires the attacker already hold authenticated access to the shared AWS account (CVSS PR:H — this is not an externally-reachable, unauthenticated flaw), the exploitation technique itself is trivial once that foothold exists: read a cleartext key from an API response and reuse it to forge a signature, no specialized skill or novel research required. The realistic threat scenario is an insider (a data scientist with legitimate but lower-trust access to a shared SageMaker Studio domain) or an attacker who has already compromised one account within the shared environment through an unrelated vector. Impact is scored at 4 (significant) because successful exploitation yields arbitrary code execution within another user's pipeline — which, depending on that pipeline's permissions and data access, could reach training data, model artifacts, or downstream deployment infrastructure the victim user is authorized to touch but the attacker is not.

## Framework Control Gaps
- **NIST 800-53 SC-28 (Protection of Information at Rest) / IA-5 (Authenticator Management):** Root cause — a signing credential (the HMAC key) was not scoped or protected such that only its owning principal could retrieve it via the API.
- **NIST AI RMF MAP 5.1:** The multi-tenant trust-boundary assumption underlying shared SageMaker environments was not validated against this specific cross-user escalation path prior to disclosure.
- **NIST CSF 2.0 PR.AA-05 (Access permissions and authorizations are managed):** Shared ML platform environments should not assume that AWS IAM account-level authentication alone is sufficient to isolate one user's pipeline execution context from another's — a gap this finding makes explicit.
- **ISO 42001 Clause 6.1.2 (AI risk assessment):** Multi-tenant AI/ML platform deployments warrant an explicit tenant-isolation risk assessment distinct from general cloud multi-tenancy review, given the additional trust placed in pipeline-level credentials like this HMAC key.

## Residual Risk Statement
After upgrading to SageMaker Python SDK v3.11.0 / v2.256.0 and rotating any HMAC keys that may have been exposed prior to patching (which cannot be assumed safe simply because the underlying bug is fixed — an already-exposed key remains valid until rotated), residual risk drops to Low. Organizations running shared SageMaker Studio domains should additionally review whether their environment design assumes stronger inter-user isolation than SageMaker actually provides, independent of this specific CVE.

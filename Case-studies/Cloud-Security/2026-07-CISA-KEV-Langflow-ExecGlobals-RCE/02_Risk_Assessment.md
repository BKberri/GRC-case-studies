# Risk Assessment
## Langflow Unauthenticated Root RCE via `exec_globals` (CVE-2026-0770)

## Risk Scoring
| Method | Score | Rating |
|---|---|---|
| Likelihood × Impact Matrix | 5 × 5 = 25 | Critical |
| CVSS Base Score | 9.8 | Critical |
| FAIR Qualitative (AI governance framing) | High loss exposure | High |

**Likelihood = 5 (Actively exploited):** Confirmed mass-scanning exploitation since 2026-06-27, three weeks prior to KEV listing, from 64 distinct source IPs.
**Impact = 5 (Full system compromise / data breach):** Unauthenticated root RCE with observed attempts to harvest cloud credentials and container metadata — a direct path to lateral movement into the surrounding cloud environment.

## Risk Narrative
The realistic threat scenario is opportunistic and automated rather than targeted: mass internet scanners identify exposed Langflow `/validate` endpoints, submit crafted `exec_globals` payloads, and obtain root execution with no authentication step to defeat. From there, observed attacker behavior (per KEVIntel and independent researcher telemetry) moves directly to credential harvesting — AWS keys, environment variables, and container instance metadata — which converts a single-host compromise into a cloud-account-level incident if the harvested credentials carry meaningful IAM permissions. The most probable attack path for an enterprise: a developer or data-science team stands up Langflow on a cloud VM or container for prototyping, exposes the validation endpoint (directly or via a permissive load balancer/ingress rule) without realizing it requires no authentication, and the instance is compromised within the first exploitation wave rather than through any targeted effort.

## Framework Control Gaps
- **NIST 800-53 SI-2 (Flaw Remediation):** No control was in place to detect or remediate the flaw prior to KEV publication; organizations lacking a software inventory that includes internally-adopted AI tooling (Langflow, LangChain-based agents, etc.) cannot act on KEV advisories they don't know apply to them.
- **NIST 800-53 AC-3 / SC-7 (Access Enforcement / Boundary Protection):** The endpoint should never have been reachable without authentication or network-layer restriction; lack of a default-deny posture on management/validation endpoints is the root architectural gap.
- **NIST 800-53 IA-2 (Identification and Authentication):** The `/validate` endpoint's absence of any authentication requirement is the specific control failure this CVE exploits.
- **NIST AI RMF MAP 4.1 / MANAGE 2.3:** Absent an AI system inventory and incident-response linkage specific to agentic tooling, organizations cannot rapidly determine exposure when a KEV entry names an AI platform.

## Residual Risk Statement
After upgrading to a patched Langflow release, restricting the validation endpoint to authenticated/internal access, and rotating all credentials reachable by the instance, residual risk is Low-Medium: the specific unauthenticated RCE vector is closed, but any credentials or lateral-movement footholds established during the unpatched exposure window persist until confirmed remediated through log review and credential rotation. Organizations that cannot confirm the instance's public exposure history should treat residual risk as High pending forensic review.

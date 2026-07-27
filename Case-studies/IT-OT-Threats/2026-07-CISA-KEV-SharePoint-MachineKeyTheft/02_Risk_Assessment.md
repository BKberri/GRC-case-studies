# Risk Assessment
## SharePoint Server Deserialization RCE with Machine Key Theft (CVE-2026-50522)

## Risk Scoring
| Method | Score | Rating |
|---|---|---|
| Likelihood × Impact Matrix | 5 × 5 = 25 | Critical |
| CVSS Base Score | 9.8 | Critical |
| FAIR Qualitative | High loss exposure (persistent forged-identity access) | High |

**Likelihood = 5 (Actively exploited):** Public PoC released 2026-07-20; active exploitation confirmed within hours, as part of a broader ongoing wave targeting SharePoint Server this month.
**Impact = 5 (Full system compromise / persistent access):** RCE plus machine key theft enabling forged authentication tokens that remain valid after patching — impact extends beyond the initial compromise window.

## Risk Narrative
The realistic threat scenario begins with an attacker who has obtained (or can obtain) at least Site Owner-level access — a lower bar than full administrative compromise, achievable via a compromised user account, insider access, or chaining with another SharePoint vulnerability in the same exploitation wave. From there, the attacker triggers the deserialization flaw for code execution and immediately harvests IIS machine keys in a single request. This is the critical pivot: with valid machine keys, the attacker can forge SharePoint authentication tokens that appear legitimate to the patched server, granting persistent, difficult-to-detect access that a standard patch-and-verify remediation cycle will not catch. The most probable path to sustained business impact is an organization that patches promptly (closing the RCE) but does not rotate machine keys, leaving a forged-token backdoor open indefinitely — the exact failure mode watchTowr's research specifically warns against.

## Framework Control Gaps
- **NIST 800-53 SI-2 (Flaw Remediation):** Patch alone addresses only the initial RCE vector, not the machine-key compromise — this control's standard definition of "remediated" is insufficient for this specific finding class.
- **NIST 800-53 IA-5 (Authenticator Management):** Machine key rotation is an authenticator-management action distinct from patching; its absence from standard patch runbooks is the core gap this case highlights.
- **NIST 800-53 AC-3 (Access Enforcement):** Site Owner-level access should be tightly scoped and monitored, given it is the minimum privilege needed to trigger this vulnerability.
- **NIST 800-53 SI-4 (System Monitoring):** Detecting forged-token usage post-patch requires monitoring for authentication anomalies that don't correlate with normal login patterns — a detection capability many organizations lack for on-premises SharePoint.

## Residual Risk Statement
After patching alone, residual risk remains **High** — this is the key finding of this assessment. Residual risk drops to Low only after machine keys are rotated *and* a review confirms no malicious artifacts (web shells, unauthorized service accounts) remain from the exploitation window beginning 2026-07-20. Rotating keys before removing any persistence mechanism the attacker planted is itself insufficient, per watchTowr guidance — sequencing matters: hunt and remove artifacts first, then rotate keys, or a still-active harvesting tool simply steals the new keys too.

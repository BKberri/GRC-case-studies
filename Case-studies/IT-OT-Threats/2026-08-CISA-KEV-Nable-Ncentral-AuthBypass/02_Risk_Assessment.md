# Risk Assessment
## 2026-08-CISA-KEV-Nable-Ncentral-AuthBypass

## Risk Scoring
| Method | Score | Rating |
|---|---|---|
| Likelihood x Impact Matrix | 5 x 5 = 25 | Critical |
| CVSS Base Score (higher of the two, CVE-2026-18577) | 8.1 | High |
| FAIR Qualitative | Very high loss exposure — active exploitation of an MSP-grade management plane with fleet-wide remote-control capability | Critical |

## Risk Narrative
Likelihood is scored at the maximum (5): exploitation has been confirmed active since before N-able's own initial disclosure, and the vendor's first remediation attempt did not fully close the exposure, indicating a persistent and actively-targeted attack surface. Impact is scored at the maximum (5) despite the vendor's CVSS rating of "High" rather than "Critical" for CVE-2026-18577, because internal risk scoring accounts for N-central's structural position as a fleet-wide management plane: administrative compromise of the server converts directly into remote-control access over every endpoint it manages, and observed attacker behavior (abusing "Take Control" plus Cloudflare Tunnel persistence) demonstrates this is not a theoretical escalation path but the actual attack chain in use. Organizations using N-central in an MSP capacity should treat this as a potential multi-tenant incident until proven otherwise.

## Framework Control Gaps
- **NIST 800-53 IA-2 / IA-8 (Identification and Authentication):** The core defect is an authentication-bypass vulnerability in a privileged administrative platform; no customer-side control could detect the logic flaw itself.
- **NIST 800-53 AC-17 (Remote Access):** Organizations should have compensating monitoring on any remote-access/remote-control feature (like "Take Control") that can be triggered without a corresponding, attributable administrator action.
- **NIST CSF 2.0 GV.SC-05 (Third-party risk requirements are established for suppliers):** RMM/MSP-tooling vendors represent a concentrated third-party risk; the incomplete first fix underscores the need for independent verification of vendor remediation claims before considering an incident closed.
- **CIS Control 13.3 (Deploy a Network Intrusion Detection Solution):** Detecting anomalous "Take Control" sessions and outbound tunnel traffic (Cloudflare Tunnel) requires network-level monitoring tuned to this platform's normal behavior baseline.

## Residual Risk Statement
After applying N-central 2026.3 Hotfix 1 (build 2026.3.1.7) and conducting a full audit of "Take Control" session history and any unauthorized Cloudflare Tunnel instances, residual risk drops to Medium. Because the vendor's first fix was incomplete, residual risk should not be considered Low until independent verification confirms the second fix closes the authentication bypass — do not rely solely on the vendor's own confirmation given the track record on this specific vulnerability class.

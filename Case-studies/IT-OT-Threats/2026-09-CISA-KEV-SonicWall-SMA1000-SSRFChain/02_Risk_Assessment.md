# Risk Assessment
## 2026-09-CISA-KEV-SonicWall-SMA1000-SSRFChain

## Risk Scoring
| Method | Score | Rating |
|---|---|---|
| Likelihood x Impact Matrix | 5 x 5 = 25 | Critical |
| CVSS Base Score | 10.0 (chained pre-auth RCE) | Critical |
| FAIR Qualitative | Very high loss exposure — unauthenticated compromise of an internet-facing remote-access appliance sitting at the enterprise network perimeter, with confirmed active exploitation | Critical |

## Risk Narrative
Likelihood is scored at the maximum (5): CISA's KEV addition confirms active exploitation, and the 3-day remediation deadline (among the shortest CISA issues) signals both the severity of the flaw and the observed exploitation tempo. Impact is scored at the maximum (5) because the vulnerability chain grants unauthenticated remote code execution on a perimeter remote-access appliance — a device whose entire function is to be the trusted gateway between external users and internal enterprise networks. There is no meaningful partial-compromise scenario here: successful exploitation of the chain gives an attacker the appliance's own network position and administrative control.

## Framework Control Gaps
- **NIST 800-53 SC-7 (Boundary Protection) / AC-4 (Information Flow Enforcement):** The SSRF flaw allowed the public-facing Work Place interface to reach functionality that should have been isolated from unauthenticated network paths — a boundary-enforcement failure at the application layer.
- **NIST 800-53 SI-10 (Information Input Validation):** Root cause for the OS command injection component of the chain.
- **NIST CSF 2.0 PR.PS-01 (Configuration management practices are established):** Perimeter remote-access appliances warrant expedited, KEV-independent patch handling given their exposure profile and history (this is the second SonicWall SMA-series KEV entry this program has tracked in 2026).
- **CIS Control 12.2 (Establish and Maintain a Secure Network Architecture):** Reinforces that administrative interfaces (the AMC) should not be reachable via any path originating from an unauthenticated, internet-facing interface, independent of the specific vulnerabilities involved.

## Residual Risk Statement
After upgrading to firmware 12.4.3 build 03526+ or 12.5.0 build 02952+, and engaging SonicWall support to investigate for indicators of compromise predating the patch (per Rapid7's guidance), residual risk drops to Low-Medium. Given confirmed active exploitation prior to and at KEV listing, any unpatched appliance discovered during remediation should be treated as a potential compromise requiring investigation, not merely a vulnerable system requiring a patch — consistent with this program's standing guidance for KEV-listed perimeter appliances with confirmed active exploitation.

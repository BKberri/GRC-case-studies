# Risk Assessment
## 2026-08-CISA-KEV-Langflow-AutoLoginRCE

## Risk Scoring
| Method | Score | Rating |
|---|---|---|
| Likelihood x Impact Matrix | 5 x 5 = 25 | Critical |
| CVSS Base Score | 9.8 | Critical |
| FAIR Qualitative | Very high loss exposure — unauthenticated RCE with public exploit code against an AI workflow platform holding third-party credentials | Critical |

## Risk Narrative
Likelihood is scored at the maximum (5) because CISA has confirmed active exploitation and a working public exploit chain exists, requiring no authentication and no user interaction. Impact is scored at the maximum (5) because the vulnerability grants unauthenticated remote code execution with SUPERUSER-equivalent privileges — a full compromise of the Langflow host and, by extension, every credential and data-source connector configured within its flows. Unlike a conventional web-application RCE, the practical blast radius here extends into whatever the AI workflows were built to touch (databases, SaaS APIs, internal tools), which is difficult to fully scope without a flow-by-flow audit of the compromised instance.

## Framework Control Gaps
- **NIST 800-53 IA-2 (Identification and Authentication):** The `auto_login` endpoint's failure to bind to loopback or require any credential is a direct violation of organizational-user authentication requirements for privileged sessions.
- **NIST 800-53 SI-2 (Flaw Remediation):** Two prior Langflow CVEs in the same 90-day window indicate remediation velocity and patch-management cadence for this platform need explicit tracking rather than ad hoc patching.
- **NIST AI RMF MAP 5.1 (Third-party AI system risks are identified and characterized):** Langflow's insecure-by-default configuration and repeat-CVE history should be documented as a standing third-party AI platform risk in the organization's AI system inventory, not treated as a one-time patch event.
- **CIS Control 16.1 (Application Software Security):** Reinforces that AI/LLM tooling deployed as an application server requires the same secure-configuration review applied to any other internet-facing web application — including disabling or network-isolating convenience endpoints like `auto_login`.

## Residual Risk Statement
After upgrading to Langflow 1.10.1 and rotating every credential and API key referenced by flows on the affected instance, residual risk drops to Low-Medium. Because the exploit grants access to whatever the flows touch, residual risk cannot be fully closed until a flow-by-flow credential and data-access audit confirms no unauthorized use occurred during the exposure window (2026-07-17, IBM's disclosure/patch date, through the organization's actual patch date).

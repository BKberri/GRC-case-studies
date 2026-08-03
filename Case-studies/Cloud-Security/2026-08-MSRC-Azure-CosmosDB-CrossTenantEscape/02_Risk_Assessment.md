# Risk Assessment
## 2026-08-MSRC-Azure-CosmosDB-CrossTenantEscape

## Risk Scoring
| Method | Score | Rating |
|---|---|---|
| Likelihood × Impact Matrix | 2 × 5 = 10 | High |
| CVSS Base Score (estimated from disclosed vector) | ~9.8–10.0 (Critical, as originally exploitable) | Critical (pre-remediation) |
| FAIR Qualitative | Low current loss exposure (closed vulnerability); High historical loss exposure had it been exploited pre-disclosure | Medium (net, post-remediation) |

## Risk Narrative
This is scored differently than an actively exploited finding: likelihood is set at 2 (theoretical/closed) because Microsoft fully remediated the vulnerability platform-wide before public disclosure, reports no evidence of customer impact, and no proof-of-concept or in-the-wild exploitation has surfaced. Impact is scored at the maximum (5) because, had this been discovered and weaponized by a malicious actor before Wiz's responsible disclosure and Microsoft's fix, the realistic worst case was cross-tenant compromise of any Cosmos DB account on the Azure platform — a scope of impact equivalent to a hyperscaler-level breach affecting potentially thousands of organizations simultaneously, entirely independent of any individual customer's security posture. The residual risk this case represents for our organization is not "will this specific flaw be exploited" (it is closed) but rather a governance question: what is our visibility into, and contractual assurance around, security incidents that occur entirely within our cloud service providers' shared infrastructure, where we have no independent means of detection?

## Framework Control Gaps
- **NIST 800-53 SA-9 (External System Services) / CA-3 (System Interconnections):** This case underscores the need for documented due-diligence processes over CSP security posture, since customer-side technical controls cannot detect or prevent provider-side control-plane vulnerabilities.
- **NIST CSF 2.0 GOVERN (GV.SC — Cybersecurity Supply Chain Risk Management):** Third-party/cloud-provider risk management processes should include a defined process for reviewing CSP-disclosed vulnerabilities and vendor security advisories, even when "no customer action is required."
- **ISO 27001 A.5.23 (Information Security for Use of Cloud Services):** Requires a defined approach to acquiring, using, and exiting cloud services, including monitoring of provider security posture — this incident is a direct test case for that control's effectiveness.
- **SOC 2 / CSA STAR:** Reinforces the value of reviewing CSP SOC 2 Type II reports and CSA STAR attestations, which should reflect the provider's incident response and vulnerability management maturity evidenced by responses like this one.

## Residual Risk Statement
Because Microsoft has confirmed full remediation and eliminated the platform-wide key architecture that made cross-tenant compromise possible, residual technical risk from this specific vulnerability is Low. The residual risk that remains is programmatic: this incident should be logged in third-party/vendor risk management records as a data point on Microsoft Azure's security response maturity (2-day emergency hotfix, full platform remediation, transparent advisory), and used to inform periodic CSP risk reviews rather than triggering customer-side remediation action.

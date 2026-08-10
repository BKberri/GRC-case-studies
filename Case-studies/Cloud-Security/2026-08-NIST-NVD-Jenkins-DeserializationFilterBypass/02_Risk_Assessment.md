# Risk Assessment
## 2026-08-NIST-NVD-Jenkins-DeserializationFilterBypass

## Risk Scoring
| Method | Score | Rating |
|---|---|---|
| Likelihood x Impact Matrix | 3 x 5 = 15 | High |
| CVSS Base Score | 9.0 | Critical |
| FAIR Qualitative | Moderate-to-high loss exposure — no confirmed exploitation, but low complexity once agent-level access is obtained, against a high-value CI/CD trust anchor | High |

## Risk Narrative
Likelihood is scored at 3 (technically feasible) rather than higher, because exploitation requires either Agent/Connect permission, control of an agent process, or (for the companion findings) specific Item/Configure and Item/Build permissions — this is not a pre-authentication, zero-click remote finding, and no in-the-wild exploitation has been reported following responsible disclosure. Impact is scored at the maximum (5) because successful exploitation of any of the three findings yields controller-level code execution — full compromise of the CI/CD trust anchor, with direct access to every credential and deployment target the controller manages. The combined score of 15 (High, just below the Critical band) reflects a serious but access-gated finding rather than an internet-wide zero-click emergency; organizations with untrusted or loosely-governed build agents, or broad developer permissions, should weight likelihood upward relative to organizations with tightly-scoped agent and permission models.

## Framework Control Gaps
- **NIST 800-53 SI-2 (Flaw Remediation):** Standard patch-management applies; Jenkins controllers should be prioritized for expedited patching given their CI/CD trust-anchor position.
- **NIST 800-53 AC-6 (Least Privilege):** Two of the three findings are directly mitigated by tightly scoping Agent/Connect permission and Item/Configure/Item/Build permissions to only those who genuinely need them — a control gap independent of the underlying code defect.
- **NIST CSF 2.0 PR.AA-05 (Access permissions incorporate least privilege):** Directly applicable to limiting the practical exploitability of all three findings via permission scoping.
- **CIS Control 16 (Application Software Security) / CIS Control 4 (Secure Configuration):** CI/CD platform hardening — including agent trust boundaries and controller filesystem permissions — is a standing control area these findings validate as under-addressed industry-wide.

## Residual Risk Statement
After upgrading to Jenkins weekly 2.576 or LTS 2.568.2 (or applying the published workaround if immediate upgrade is not feasible) and reviewing Agent/Connect and Item/Configure/Item/Build permission assignments for unnecessary breadth, residual risk drops to Low. Organizations that cannot immediately upgrade should prioritize permission-scoping as an interim compensating control, since it directly reduces the population of potential exploiters for all three findings.

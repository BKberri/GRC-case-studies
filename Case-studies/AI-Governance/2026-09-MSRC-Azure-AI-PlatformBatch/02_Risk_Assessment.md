# Risk Assessment
## 2026-09-MSRC-Azure-AI-PlatformBatch

## Risk Scoring
| Method | Score | Rating |
|---|---|---|
| Likelihood x Impact Matrix | 2 x 5 = 10 | High |
| CVSS Base Score | Up to 10.0 (Critical) | Critical |
| FAIR Qualitative | Bounded loss exposure given no confirmed exploitation and a completed server-side fix, but the theoretical severity (unauthenticated full privilege escalation in an AI development platform) warrants High treatment pending customer-side log review | High |

## Risk Narrative
Likelihood is scored at 2 (theoretical) rather than higher because both vulnerabilities were responsibly disclosed and fixed by Microsoft before any confirmed exploitation was observed — this is the same disclosure pattern this program has seen repeatedly in vendor-caught cloud AI-platform flaws. Impact is scored at 5 (full system compromise) because, had either been exploited prior to the fix, the outcome is full unauthenticated privilege escalation (Foundry) or authenticated-to-elevated escalation within an AI assistant with deep M365 data access (Copilot) — a severity level that would affect the integrity of an organization's AI development pipeline or the trust boundary around what their AI assistant can do on a user's behalf.

## Framework Control Gaps
- **NIST AI RMF MAP 5.1 (Likelihood and magnitude of impacts documented):** The specific cross-boundary impact of a missing-authentication flaw in an AI platform's critical functions was not identified prior to vendor disclosure — a pattern, not a one-off, across this program's Azure AI findings.
- **NIST 800-53 IA-2 (Identification and Authentication):** Root cause for CVE-2026-85889 — a critical function lacked authentication enforcement entirely.
- **NIST 800-53 SI-10 (Information Input Validation):** Root cause for CVE-2026-85885 — command elements were not adequately neutralized before execution.
- **ISO 42001 Clause 8.4 (AI system impact assessment):** Organizations building on Azure AI Foundry or deploying Copilot broadly should independently verify their own impact-assessment documentation accounts for platform-level authentication/authorization risk, not just model-level risk.

## Residual Risk Statement
Because Microsoft applied both fixes server-side before this report, residual risk for the vulnerabilities themselves is Low. However, residual uncertainty remains around whether either flaw was exploited prior to the fix — organizations using Azure AI Foundry should complete the recommended log review (privileged activity, new service principals, role assignments, API connections predating 2026-09-17) before considering this fully closed, since Microsoft's advisory language recommends but does not confirm the absence of prior exploitation.

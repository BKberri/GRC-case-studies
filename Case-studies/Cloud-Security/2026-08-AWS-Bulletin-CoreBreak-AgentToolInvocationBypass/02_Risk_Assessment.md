# Risk Assessment
## 2026-08-AWS-Bulletin-CoreBreak-AgentToolInvocationBypass

## Risk Scoring
| Method | Score | Rating |
|---|---|---|
| Likelihood x Impact Matrix | 4 x 5 = 20 | Critical |
| CVSS Base Score (highest, Google ADK, v4.0) | 9.3 | Critical |
| FAIR Qualitative | High loss exposure given multi-vendor architectural scope, even absent confirmed in-the-wild exploitation | Critical |

## Risk Narrative
Likelihood is scored at 4 (PoC public in the sense that full technical detail, CWE classification, and vendor patch diffs are publicly available, even though the researchers withheld a fully weaponized exploit) rather than 5, because no confirmed exploitation against a live deployment has been reported. Impact is scored at the maximum (5) because, where exploitable, these paths bypass tool-authorization entirely — the practical outcome ranges from unauthorized cloud API calls and secret/credential exfiltration (Vercel path, contingent on sandbox compromise) to full unauthorized tool execution bypassing human-approval gates (Google path) to direct tool dispatch without model mediation (AWS path, already mitigated). The combined score of 20 (Critical) reflects that this is an architecture-level risk class credibly demonstrated across three independent, widely-used platforms — the kind of finding that should prompt a design review of any in-house agentic AI system, not just a patch-and-close response to the four listed CVEs.

## Framework Control Gaps
- **NIST AI RMF MANAGE 4.1 (Risk treatment includes third-party AI components):** Organizations using AWS Bedrock AgentCore, Google ADK, or Vercel AI SDK harnesses for internal agent development need a documented risk-treatment record for this vulnerability class, not just individual patch tickets.
- **NIST AI RMF MAP 1.1 (AI system context and boundaries are understood):** The core failure mode — trusting caller-supplied data that resembles a model decision — is exactly the kind of architectural boundary-confusion MAP 1.1 is meant to surface during system design, not after a Black Hat disclosure.
- **ISO 42001 6.1.2 (AI risk assessment):** In-house agentic AI systems built on any of these frameworks (or with a similar tool-invocation pattern) should be re-assessed against this specific failure mode as part of ongoing AI risk assessment, independent of whether the organization uses the exact affected products.
- **NIST 800-53 AC-3 (Access Enforcement):** The unifying technical gap across all three vendors is a failure to enforce that tool execution requires a specific, verified authorization event — a variant of access enforcement applied to the AI-agent-to-tool boundary rather than the traditional user-to-resource boundary.

## Residual Risk Statement
For AWS Bedrock AgentCore's managed InvokeHarness API, residual risk is Low following AWS's automatic server-side fix — but organizations running the open-source Strands SDK directly (not through the managed AgentCore service) retain exposure to the comparable model-skipping code path and should apply the documented mitigation (build message history only from trusted, application-controlled sources) explicitly, since AWS has not shipped a code fix for that path. For Google ADK, residual risk drops to Low after upgrading to 2.5.0. For Vercel, residual risk drops to Low-Medium after upgrading to the patched harness versions, contingent on separately hardening sandbox isolation, since the underlying attack precondition (untrusted code execution inside the sandbox) is a distinct risk the patch does not eliminate.

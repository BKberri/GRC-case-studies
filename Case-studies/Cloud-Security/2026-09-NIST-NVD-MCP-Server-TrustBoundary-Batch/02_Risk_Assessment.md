# Risk Assessment
## 2026-09-NIST-NVD-MCP-Server-TrustBoundary-Batch

## Risk Scoring
| Method | Score | Rating |
|---|---|---|
| Likelihood x Impact Matrix | 3 x 5 = 15 | High |
| CVSS Base Score | Up to 9.8 (Critical) across the batch | Critical |
| FAIR Qualitative | High loss exposure — several findings are unauthenticated and remotely reachable (LightLLM, GitLab MCP); credential-theft (Lokka) and RCE (atomic-agents-stack) outcomes present in the batch; no confirmed exploitation yet moderates immediate likelihood | High |

## Risk Narrative
Likelihood is scored at 3 (technically feasible) reflecting that while no confirmed in-the-wild exploitation was found for any of the six CVEs, several are unauthenticated, network-reachable flaws (LightLLM's WebSocket endpoint, the GitLab MCP server's SSE transport) requiring no special attacker capability to exploit once discovered. Impact is scored at 5 (full system compromise) at the batch level because the range of outcomes spans prompt/data disclosure, cloud credential theft (Lokka's Azure bearer-token leak), and remote code execution (atomic-agents-stack) — any of which, in an environment where the affected MCP server has privileged access to production systems, could yield a severe outcome.

## Framework Control Gaps
- **NIST 800-53 IA-2 (Identification and Authentication):** Root cause for LightLLM, GitLab MCP, and ToolHive — MCP endpoints exposed without authentication enforcement.
- **NIST 800-53 SC-8 (Transmission Confidentiality and Integrity):** Root cause for atomic-agents-stack — cleartext HTTP transport for a security-relevant registry backend.
- **NIST AI RMF GOVERN 1.1 (Policies for AI risk management):** Organizations adopting MCP servers from open-source/community sources should apply a documented vetting policy given this program's now three-week pattern of findings across independently-developed MCP implementations.
- **ISO 42001 Clause 6.1.2 (AI risk assessment):** The MCP tooling layer itself — not just the AI model — warrants explicit inclusion in AI system risk assessments given its direct access to external systems on the agent's behalf.

## Residual Risk Statement
After upgrading each affected MCP server component to its fixed version, residual risk per individual CVE drops to Low. However, this program assesses the category-level residual risk as Medium given the sustained three-week finding rate across independently-developed MCP implementations — organizations should not treat this batch's remediation as closing the broader MCP trust-boundary risk, only this specific set of findings.

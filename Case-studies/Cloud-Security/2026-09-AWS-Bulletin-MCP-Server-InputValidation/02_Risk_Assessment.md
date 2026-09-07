# Risk Assessment
## 2026-09-AWS-Bulletin-MCP-Server-InputValidation

## Risk Scoring
| Method | Score | Rating |
|---|---|---|
| Likelihood x Impact Matrix | 3 x 4 = 12 | High |
| CVSS Base Score | CVE-2026-85787: High (unscored) / CVE-2026-85654: 7.1 (High, v4.0) | High |
| FAIR Qualitative | Moderate-high loss exposure — no confirmed exploitation, but the defect defeats a specific operator-configured safety control (read-only mode) and, for the DynamoDB path, converts a convenience feature into an RCE primitive under realistic supply-chain conditions | High |

## Risk Narrative
Likelihood is scored at 3 (technically feasible) rather than higher because there is no confirmed in-the-wild exploitation and both findings were responsibly disclosed and patched by AWS before this report — but 3, not lower, because exploitation does not require novel research: the postgres-mcp-server bypass is a straightforward denylist-completeness gap, and the DynamoDB template-injection path is a well-understood vulnerability class (CWE-1336) being newly discovered in an AI-tooling-generation context. Impact is scored at 4 (significant data exposure/integrity impact) rather than 5 because exploitation is bounded by what the specific MCP server's underlying database or generated infrastructure can reach, rather than a full unauthenticated remote compromise of the host — but 4 reflects that a defeated read-only control on a production database, or arbitrary code execution injected into deployed infrastructure-as-code, both represent integrity failures with organization-wide blast radius if the affected MCP server sits in a shared or multi-tenant agent deployment.

## Framework Control Gaps
- **NIST AI RMF MAP 5.1 (Likelihood and magnitude of each identified impact are documented):** Neither defect was caught by the vendor's own pre-release trust-boundary threat modeling for agent-invoked tools — a MAP-function gap this program has now observed in two consecutive weekly sweeps (RR-049, this finding).
- **NIST AI RMF MANAGE 4.1 (AI risks and benefits are regularly monitored):** Organizations running these MCP servers had no way to detect the gap between configured intent (read-only mode) and actual enforced behavior without vendor disclosure — a monitoring/verification gap specific to agent-tool trust boundaries.
- **NIST 800-53 SI-10 (Information Input Validation):** Direct root cause for CVE-2026-85787 — the denylist-based validation approach is inherently incomplete compared to an allowlist/parameterized-query enforcement model.
- **NIST 800-53 SA-11 (Developer Security Testing and Evaluation):** The DynamoDB CDK generator's template-injection gap indicates code-generation output was not adversarially tested against attacker-controlled schema input prior to release.
- **ISO 42001 Clause 8.4 (AI system impact assessment):** Reinforces the MAP-function gap — an AI system impact assessment for an MCP server acting on a production database or deployment pipeline should explicitly test for safety-control bypass, not only functional correctness.

## Residual Risk Statement
After upgrading `postgres-mcp-server` to 1.1.7+ and `dynamodb-mcp-server` to 2.1.6+, and — per AWS's own defense-in-depth guidance — enforcing least-privilege database roles (avoiding superuser/rds_superuser connections, granting only the SQL verbs actually required) rather than relying on the MCP server's application-level read-only flag alone, residual risk drops to Low. Organizations should not treat the application-level "read-only mode" toggle on any MCP server as a sufficient control on its own going forward; the database- or infrastructure-level permission boundary is the actual control, and the application-level flag is, at best, defense-in-depth.

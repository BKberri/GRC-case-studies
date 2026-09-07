# Control Mapping
## 2026-09-AWS-Bulletin-MCP-Server-InputValidation

## Applicable Frameworks
NIST AI RMF for the AI-agent-specific risk management gap; ISO 42001 for AI management-system impact-assessment alignment; NIST CSF 2.0 and NIST 800-53 Rev 5 for the underlying input-validation and secure-development control failures; MITRE ATLAS for the AI-specific technique mapping.

## Control Mapping Table
| Framework | Control ID | Control Name | Applicability | Gap / Status |
|---|---|---|---|---|
| NIST AI RMF | MAP 5.1 | Likelihood and magnitude of impacts documented | Pre-release threat modeling did not surface the safety-control bypass (Postgres) or template-injection path (DynamoDB) | Gap (vendor) |
| NIST AI RMF | MANAGE 4.1 | AI risks and benefits regularly monitored | No operator-facing mechanism existed to verify the read-only flag was actually enforced at the database layer | Gap |
| NIST AI RMF | GOVERN 1.1 | Policies/processes for AI risk are in place | Reinforces need for an org-level policy requiring database-enforced (not application-flag-only) least privilege for any AI-agent data access | Gap |
| ISO 42001 | 8.4 | AI system impact assessment | Impact assessment for an MCP server acting on production data should test control-bypass scenarios, not only functional paths | Gap |
| NIST 800-53 | SI-10 | Information Input Validation | Direct root cause — incomplete denylist in SQL validation (CVE-2026-85787) | Gap (vendor, now fixed) |
| NIST 800-53 | SA-11 | Developer Security and Privacy Testing | Template-injection path in CDK code generation not caught by adversarial testing prior to release (CVE-2026-85654) | Gap (vendor, now fixed) |
| NIST 800-53 | AC-6 | Least Privilege | Reinforces recommended compensating control — database role enforcement independent of application-layer flags | Recommended standing control |
| MITRE ATLAS | AML.T0053 | LLM Plugin Compromise | Both findings fit the pattern of a tool/plugin the agent invokes performing a broader action than the agent's configured intent authorized | Applicable technique mapping |

## Control Narrative
Both defects are, at root, input-validation and secure-development-lifecycle gaps (SI-10, SA-11) that happen to surface through AI-agent tooling rather than a traditional API — which is exactly why NIST AI RMF's MAP and MANAGE functions are the more precise lens than a conventional vulnerability-management framing alone. A conventional read of these bulletins ("patch to the fixed version") is necessary but not sufficient; the AI-governance-relevant finding is that an application-level safety configuration (postgres-mcp-server's read-only mode) was silently bypassable, and no monitoring control existed to detect that bypass independent of the vendor's own disclosure. This is the second consecutive week this program has logged a finding in this exact shape (see RR-049, CoreBreak), which is enough of a pattern to recommend elevating "AI-agent tool-invocation trust boundary" to a standing review item in this program's AI governance control set — specifically, requiring that any AI-agent access to a data store or deployment pipeline be bounded by an infrastructure-enforced permission (IAM policy, database role, network segmentation) rather than solely by the AI tool's own application-level configuration, regardless of vendor.

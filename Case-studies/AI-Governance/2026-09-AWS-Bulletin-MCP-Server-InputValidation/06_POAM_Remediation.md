# Plan of Action & Milestones (POA&M)
## 2026-09-AWS-Bulletin-MCP-Server-InputValidation
**Date Opened:** 2026-09-07 | **Source:** AWS Security Bulletins | **Risk Rating:** High | **Target Closure:** 2026-09-21

## POA&M Table
| Item ID | Weakness / Finding | Affected System | Control Reference | Responsible Role | Planned Action | Milestone 1 | Milestone 2 | Milestone 3 | Target Date | Status |
|---|---|---|---|---|---|---|---|---|---|---|
| POA-202609-001 | Incomplete SQL-validation denylist allows read-only bypass (CVE-2026-85787) | `awslabs.postgres-mcp-server` deployments | NIST 800-53 SI-10 | AI/Platform Engineering Lead | Upgrade to postgres-mcp-server 1.1.7+ | 2026-09-08: Inventory all MCP-server deployments | 2026-09-10: Upgrade all instances | 2026-09-12: Verify read-only sessions cannot execute write statements (test) | 2026-09-12 | Open |
| POA-202609-002 | Template injection in CDK generator enables code execution (CVE-2026-85654) | `awslabs.dynamodb-mcp-server` deployments | NIST 800-53 SA-11 | AI/Platform Engineering Lead | Upgrade to dynamodb-mcp-server 2.1.6+ | 2026-09-08: Inventory all MCP-server deployments | 2026-09-10: Upgrade all instances | 2026-09-12: Review any previously-generated CDK code from untrusted data models for anomalies | 2026-09-12 | Open |
| POA-202609-003 | Application-level "read-only mode" is not an infrastructure-enforced control | Any AI-agent database integration | NIST 800-53 AC-6; NIST AI RMF MANAGE 4.1 | Database/Cloud Engineering | Enforce least-privilege database roles independent of MCP-server application settings for all AI-agent data access | 2026-09-14: Audit current AI-agent service-account database permissions | 2026-09-21: Remediate any AI-agent account with broader-than-required privileges | 2026-09-21: Document standing least-privilege requirement in AI integration standard | 2026-09-21 | Open |

## Remediation Narrative
Upgrade both AWS Labs MCP servers to their fixed versions across every environment where they are deployed (development, staging, and production agent integrations alike — MCP-server sprawl into non-production environments is common and should not be excluded from the inventory). Because neither vulnerability has confirmed exploitation, there is no forensic urgency, but the architectural gap they expose — an application-level safety toggle that does not reliably bound agent behavior — should not be closed as "patched" without also addressing the underlying control gap via database- and IAM-level least privilege.

## Compensating Controls
Until upgrades are confirmed across all instances, restrict the database role or IAM permissions available to any AI-agent service account to only the operations actually required, independent of the MCP server's own read-only configuration flag. For dynamodb-mcp-server, avoid running the CDK-generation feature against data-model files sourced from untrusted or externally-editable locations until patched.

## Verification & Closure Criteria
Closure requires: (1) confirmed upgrade of every postgres-mcp-server and dynamodb-mcp-server instance to the fixed version; (2) a documented test confirming a read-only-configured agent session cannot execute write/DDL statements against the target database; (3) a completed least-privilege audit of AI-agent database service accounts with any over-privileged account remediated; (4) this control documented as a standing requirement in the organization's AI-agent integration standard, not scoped only to these two CVEs.

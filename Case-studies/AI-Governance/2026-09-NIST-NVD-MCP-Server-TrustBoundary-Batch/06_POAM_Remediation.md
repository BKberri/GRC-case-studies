# Plan of Action & Milestones (POA&M)
## 2026-09-NIST-NVD-MCP-Server-TrustBoundary-Batch
**Date Opened:** 2026-09-21 | **Source:** NIST NVD | **Risk Rating:** High | **Target Closure:** 2026-09-28

## POA&M Table
| Item ID | Weakness / Finding | Affected System | Control Reference | Responsible Role | Planned Action | Milestone 1 | Milestone 2 | Milestone 3 | Target Date | Status |
|---|---|---|---|---|---|---|---|---|---|---|
| POA-202609-025 | Six independent MCP-server trust-boundary CVEs (auth bypass, SSRF, credential theft, RCE) across LightLLM, GitLab MCP, Lokka, docker/mcp-gateway, ToolHive, atomic-agents-stack | MCP server tooling, where deployed | NIST 800-53 IA-2, SC-8 | AI/ML Engineering Lead | Inventory deployed MCP servers and patch all affected instances | 2026-09-23: Complete inventory of deployed MCP server products | 2026-09-26: Patch all affected instances to fixed versions | N/A | 2026-09-26 | Open |
| POA-202609-026 | Potential Azure token exposure if Lokka MCP server is in use (CVE-2026-58201) | Azure/M365 tenant (if Lokka deployed) | NIST 800-53 AU-6 | Cloud Security Lead | Review Azure activity logs for token misuse if Lokka is confirmed in use | 2026-09-24: Confirm whether Lokka is deployed | 2026-09-27: Complete log review if applicable | N/A | 2026-09-27 | Open |
| POA-202609-027 | No standing vetting process for third-party MCP server adoption despite three-week finding pattern | AI agent tooling governance | NIST AI RMF GOVERN 1.1 | AI Governance / Security Architecture | Establish MCP-server vetting and inventory process | 2026-09-28: Present proposed vetting process at next governance review | N/A | N/A | 2026-09-28 (next quarterly review) | Open |

## Remediation Narrative
Complete an inventory of which of the six affected MCP server products are deployed before scoping detailed remediation, since this is a multi-vendor batch rather than a single-product patch cycle. Prioritize any Lokka (Azure/M365) or GitLab MCP deployments given their confirmed credential-theft and file-exfiltration mechanisms. Use this batch as the trigger to formalize a standing MCP-server vetting process given the sustained three-week finding pattern.

## Compensating Controls
Where an affected MCP server cannot be immediately patched, restrict its network reachability to only the systems it must legitimately serve, and disable or restrict any credential-bearing integrations (Azure, GitLab tokens) until patched.

## Verification & Closure Criteria
Closure requires: (1) completed inventory confirming which affected products are deployed; (2) confirmed patching of all in-use affected instances; (3) completed Azure activity log review if Lokka was in use; (4) a proposed MCP-server vetting process presented to AI governance.

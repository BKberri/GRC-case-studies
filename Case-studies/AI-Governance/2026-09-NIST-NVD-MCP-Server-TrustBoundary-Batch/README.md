# 2026-09-NIST-NVD-MCP-Server-TrustBoundary-Batch
**Date:** 2026-09-21 | **Source:** NIST NVD | **Category:** AI-Governance (dual: Cloud-Security) | **Risk Rating:** High

## Summary
Six distinct Model Context Protocol (MCP) server and AI-agent-tooling CVEs were published to NVD this week, continuing a pattern this program has tracked for three consecutive weeks (following RR-049 "CoreBreak" and last week's AWS Labs MCP-server findings): CVE-2026-93839 (LightLLM, CVSS 9.8, unauthenticated node registration), CVE-2026-61560 (GitLab MCP server, CVSS 9.8, unauthenticated arbitrary file read/exfiltration), CVE-2026-58201 (Lokka Microsoft 365 MCP server, CVSS v4.0 8.7, Azure bearer-token theft via SSRF), CVE-2026-55887 (docker/mcp-gateway, CVSS v4.0 8.7, YAML-based config injection), CVE-2026-58197 (Stacklok ToolHive, CVSS 8.8, unauthenticated local network exposure), and CVE-2026-91988 (atomic-agents-stack, CVSS 8.1/v4.0 9.2, cleartext MCP registry MITM leading to RCE). Each finding is independent, but all share the same structural weakness this program has now flagged repeatedly: the MCP ecosystem's rapid growth is outpacing baseline authentication, transport-security, and input-validation discipline across the tooling that connects AI agents to the systems they act on.

## Artifact Index
| File | Description |
|---|---|
| 01_Threat_Intelligence.md | Full technical threat intelligence report |
| 02_Risk_Assessment.md | Risk scoring and control gap analysis |
| 03_BIA.md | Business impact analysis |
| 04_Control_Mapping.md | Framework control mapping |
| 05_Executive_Summary.md | Board/CISO-level summary |
| 06_POAM_Remediation.md | Plan of Action & Milestones |

## Key Facts
- **CVE/Advisory ID:** CVE-2026-93839; CVE-2026-61560; CVE-2026-58201; CVE-2026-55887; CVE-2026-58197; CVE-2026-91988
- **CVSS Score:** Range 8.1-9.8 across the batch (see technical detail for per-CVE breakdown)
- **Affected Technology:** LightLLM (ModelTC LLM-inference server) ≤1.2.0; @zereight/mcp-gitlab <2.1.27; merill/lokka <2.1.2; docker/mcp-gateway 0.21.0-0.42.1; ToolHive CLI <0.30.1 / Studio <0.38.0; atomic-agents-stack <1.1.0
- **Frameworks Applied:** NIST AI RMF, ISO 42001, NIST CSF 2.0, NIST 800-53 Rev 5, MITRE ATLAS
- **Exploitation Status:** No confirmed in-the-wild exploitation for any of the six; all vendor-fixed
- **Vendor Due Date:** No CISA KEV listing; fixed versions available for all six as of this sweep

## Related Cases
Third consecutive week this program has logged an MCP-server/AI-agent-tooling trust-boundary finding, following `2026-08-AWS-Bulletin-CoreBreak-AgentToolInvocationBypass` (RR-049) and last week's `2026-09-AWS-Bulletin-MCP-Server-InputValidation` (RR-051/052). This program recommends treating "MCP/AI-agent infrastructure" as a standing register category going forward given the sustained weekly finding rate, rather than one-off tracking per incident.

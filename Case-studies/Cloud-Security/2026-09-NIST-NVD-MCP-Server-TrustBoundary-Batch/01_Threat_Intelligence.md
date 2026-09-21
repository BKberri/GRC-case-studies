# Threat Intelligence Report
## 2026-09-NIST-NVD-MCP-Server-TrustBoundary-Batch
**Date:** 2026-09-21 | **Source:** NIST NVD (published 2026-09-14 to 2026-09-18) | **Severity:** High | **Category:** AI-Governance / Cloud-Security

## Executive Overview
The Model Context Protocol (MCP) is the emerging standard for connecting AI agents and LLM applications to external tools, data sources, and systems — effectively the plumbing that lets an AI agent take action in the real world (read a file, query a database, call an API) rather than just generate text. This week's sweep identified six independent CVEs across six different MCP-related projects, all published within the same 5-day window, each exposing a different flavor of the same underlying problem: authentication, transport security, or input validation that has not kept pace with how quickly MCP server implementations are being built and adopted.

## Technical Details

| CVE | Product | CVSS | CWE | Description |
|---|---|---|---|---|
| CVE-2026-93839 | LightLLM (LLM-inference server) | 9.8 Critical | CWE-306 | Unauthenticated WebSocket `/pd_register` endpoint lets attackers register arbitrary nodes, disclose routed prompts, or redirect requests to internal addresses (SSRF-like) |
| CVE-2026-61560 | @zereight/mcp-gitlab (GitLab MCP server) | 9.8 Critical | CWE-22 | SSE transport exposes all MCP tools unauthenticated; `upload_markdown` tool reads arbitrary server files and exfiltrates them to a GitLab project |
| CVE-2026-58201 | Lokka (Microsoft 365/Graph MCP server) | v4.0 8.7 | CWE-918 | URL-concatenation SSRF flaw leaks the Azure Resource Manager bearer token to an attacker-controlled host |
| CVE-2026-55887 | docker/mcp-gateway | v4.0 8.7 | CWE-88 | Attacker-controlled OCI image label is YAML-unmarshalled into the MCP catalog structure, enabling argument injection into MCP server runtime config |
| CVE-2026-58197 | Stacklok ToolHive / ToolHive Studio | 8.8 High | CWE-284/306 | Locally-run MCP containers lack network isolation and expose unauthenticated API/proxy endpoints reachable via host.docker.internal |
| CVE-2026-91988 | atomic-agents-stack (AI-agent framework) | 8.1 / v4.0 9.2 | CWE-319 | Cleartext HTTP MCP server-registry backend allows MITM to rewrite the catalog and achieve RCE via MCPClientPool subprocess spawning |

**Exploitation Status:** No confirmed in-the-wild exploitation for any of the six as of this sweep; all have vendor fixes available.
**Threat Actor Attribution:** None for any of the six.
**MITRE ATLAS Technique IDs:** ML Supply Chain Compromise (catalog/registry tampering — CVE-2026-55887, CVE-2026-91988), ML Model Access, Exfiltration (CVE-2026-61560, CVE-2026-58201).
**CISA Remediation Due Date:** Not applicable — none KEV-listed.

## Affected Technology Context
Three consecutive weeks of MCP/AI-agent-tooling findings is no longer a coincidence this program treats as isolated incidents — it reflects the genuine immaturity of a fast-moving ecosystem where server implementations are frequently built and published by small teams or individual maintainers without the security review cadence applied to more established enterprise software categories. The specific failure modes vary (missing auth, SSRF, YAML injection, cleartext transport, network isolation gaps) but the pattern is consistent: MCP server implementations are, as a category, under-hardened relative to the privileged access they are granted (file systems, cloud credentials, internal APIs) on behalf of the AI agents that use them.

## Intelligence Source Links
- NVD: https://nvd.nist.gov/vuln/detail/CVE-2026-93839 ; https://nvd.nist.gov/vuln/detail/CVE-2026-61560 ; https://nvd.nist.gov/vuln/detail/CVE-2026-58201 ; https://nvd.nist.gov/vuln/detail/CVE-2026-55887 ; https://nvd.nist.gov/vuln/detail/CVE-2026-58197 ; https://nvd.nist.gov/vuln/detail/CVE-2026-91988

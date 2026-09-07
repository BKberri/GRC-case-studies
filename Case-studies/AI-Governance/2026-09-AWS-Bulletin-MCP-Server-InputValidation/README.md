# 2026-09-AWS-Bulletin-MCP-Server-InputValidation
**Date:** 2026-09-07 | **Source:** AWS Security Bulletins | **Category:** AI-Governance (dual: Cloud-Security) | **Risk Rating:** High

## Summary
AWS Labs published two security bulletins on 2026-09-04 for open-source Model Context Protocol (MCP) servers it maintains for AI agents to interact with AWS data services. `postgres-mcp-server` (CVE-2026-85787) ships an incomplete SQL-validation blocklist that lets an attacker smuggle write/DDL statements into a session an AI agent believes is restricted to read-only queries, letting the agent modify data beyond its intended scope. `dynamodb-mcp-server` (CVE-2026-85654, CVSS v4.0 7.1) contains a template-injection flaw in its CDK-code-generation feature: a malicious table, index, or attribute name in a data-model file is rendered unsanitized into generated infrastructure-as-code, achieving remote code execution when that generated code is later deployed. Both are grouped in one case because they share a root cause pattern — insufficient trust-boundary enforcement between natural-language/agent-driven input and the privileged database or deployment operations the MCP server executes on the agent's behalf — the same class of finding as the CoreBreak agent-tool-invocation research logged in this program's 2026-08-10 sweep (RR-049).

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
- **CVE/Advisory ID:** CVE-2026-85787 (AWS Bulletin 2026-101-AWS) and CVE-2026-85654 (AWS Bulletin 2026-097-AWS)
- **CVSS Score:** CVE-2026-85787 not numerically scored by AWS (rated High); CVE-2026-85654 CVSS v4.0 7.1 (High)
- **Affected Technology:** `awslabs.postgres-mcp-server` (PyPI) versions before 1.1.7; `awslabs.dynamodb-mcp-server` versions 2.0.10 and earlier
- **Frameworks Applied:** NIST AI RMF, ISO 42001, NIST CSF 2.0, NIST 800-53 Rev 5, MITRE ATLAS
- **Exploitation Status:** No confirmed in-the-wild exploitation reported by AWS at time of publication; both are responsibly-disclosed design/implementation flaws in AWS-maintained open-source tooling
- **Vendor Due Date:** No CISA KEV listing (not federally mandated); AWS recommends immediate upgrade

## Related Cases
Second consecutive sweep with a cross-vendor AI-agent-tooling trust-boundary finding — see `AI-Governance/2026-08-AWS-Bulletin-CoreBreak-AgentToolInvocationBypass` (RR-049, 2026-08-10 run) for the architecture-class precedent (AWS Bedrock AgentCore, Google ADK, Vercel AI SDK). This case narrows the same pattern to AWS Labs' own reference MCP servers for Postgres and DynamoDB, indicating the trust-boundary gap between agent-issued natural-language intent and the privileged operation an MCP tool actually executes is a recurring, vendor-agnostic AI-agent architecture risk rather than an isolated defect.

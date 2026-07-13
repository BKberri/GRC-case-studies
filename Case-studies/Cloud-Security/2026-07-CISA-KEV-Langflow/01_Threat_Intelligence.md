# Threat Intelligence Report — Langflow AI Agent Platform Authorization Bypass

## CVE Details

| Field | Value |
|---|---|
| **CVE ID** | CVE-2026-55255 |
| **Vulnerability Name** | Langflow — Authorization Bypass Through User-Controlled Key (IDOR) |
| **Affected Vendor/Product** | Langflow (open-source AI agent/workflow orchestration platform), versions prior to 1.9.2 |
| **CVSS Score** | 9.9 (Critical) |
| **Vulnerable Component** | `/api/v1/responses` endpoint |
| **Date Added to KEV** | 2026-07-07 |
| **CISA Remediation Due Date** | 2026-07-10 (3-day emergency mandate under BOD 26-04) |
| **Exploitation Type** | Authorization bypass / Insecure Direct Object Reference — authenticated attacker executes another user's AI agent flow by specifying the victim's flow ID |

## Exploitation Summary
Langflow is a widely adopted open-source, low-code platform for building and deploying AI-powered agents and workflows, commonly used to orchestrate LLM calls, tool invocations, and multi-step autonomous tasks. CVE-2026-55255 is an IDOR/authorization-bypass flaw in the `/api/v1/responses` endpoint: any authenticated user can execute a flow belonging to a different user simply by supplying that user's flow ID in the request, with no ownership check enforced. Because Langflow flows are frequently configured with tool access — code execution, API integrations, file system operations, credentials for upstream services — hijacking another user's flow means hijacking the authorized actions and access that flow carries. CISA added the CVE to its KEV catalog on 2026-07-07 based on confirmed active exploitation and set a 3-day remediation deadline (2026-07-10) under BOD 26-04. Multiple outlets noted this as the first AI agent platform to appear in the KEV catalog.

## Threat Context — Agentic AI Risk Precedent
This finding does not exist in isolation. Sysdig has documented the first confirmed case of "agentic ransomware": a human operator exploited an earlier, related Langflow vulnerability (CVE-2025-3248) to deploy an AI agent and provision the infrastructure necessary to let that agent independently run an entire extortion operation, start to finish. That precedent is directly relevant to CVE-2026-55255 — it demonstrates that compromise of an AI-agent-orchestration platform is not a conventional data-exposure event but a hand-off of autonomous, tool-enabled capability to an attacker.

## Framework Mapping
- **NIST AI RMF:** GOVERN 1.1 (AI risk management processes), MAP 4.1 (risks/benefits mapped for third-party AI components), MANAGE 2.3 (AI system incidents responded to and managed), MANAGE 4.1 (post-deployment AI risks monitored)
- **ISO/IEC 42001:2023:** Clause 6.1.2 (AI risk assessment), Clause 8.1 (Operational planning/control of AI system risk)
- **NIST CSF 2.0:** PR.AA-05 (Access permissions/authorizations managed), DE.CM-09 (Computing hardware/software monitored)
- **NIST 800-53 Rev 5:** AC-3 (Access Enforcement), IA-2 (Identification/Authentication), SI-2 (Flaw Remediation)
- **EU AI Act:** Article 9 (Risk management system) and Article 15 (Accuracy, robustness, and cybersecurity) — relevant where the affected Langflow instance is in scope of a high-risk AI system
- **MITRE ATLAS:** ML Model Access (unauthorized access to another user's agent/flow); relevant to Exfiltration and Impact tactics given tool-enabled flows

## Recommended Immediate Action
Upgrade all Langflow instances to version 1.9.2 or later immediately. Inventory every deployed flow for tool/credential access scope; rotate any credentials embedded in or reachable from flows on affected instances; review Langflow audit/access logs for cross-user flow-ID execution since 2026-07-07 (or earlier if logs permit).

## Risk Rating
**Critical** — CVSS 9.9, confirmed active exploitation, 3-day federal remediation mandate, and a documented real-world precedent (agentic ransomware) for what a hijacked AI agent can be made to do.

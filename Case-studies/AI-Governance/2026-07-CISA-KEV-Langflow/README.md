# Case Study: Langflow AI Agent Platform — Authorization Bypass (CVE-2026-55255)

**Category:** AI-Governance (duplicated in Cloud-Security — see note below)
**Source:** CISA KEV
**CVE ID:** CVE-2026-55255
**KEV Added:** 2026-07-07 | **Federal Due Date:** 2026-07-10 (BOD 26-04, 3-day emergency mandate)
**Risk Rating:** Critical
**Bundle Date:** 2026-07-13

## Summary
Langflow — an open-source, low-code platform for building and deploying AI-powered agents and workflows — carries an Insecure Direct Object Reference (IDOR) / authorization-bypass flaw (CVE-2026-55255, CVSS 9.9) in its `/api/v1/responses` endpoint. An authenticated attacker can execute any other user's flow by supplying the victim's flow ID, effectively hijacking that user's configured AI agent — including any tools, credentials, or data sources the flow is wired to. CISA added the CVE to the KEV catalog on 2026-07-07 under a 3-day emergency remediation mandate (BOD 26-04), and multiple outlets flagged it as the first AI agent platform to appear in the KEV catalog.

## Why This Is Flagged as Highest Priority
Per the GRC Intelligence Monitoring program's standing instruction, AI/LLM and AI-agent platform vulnerabilities are treated as highest priority regardless of category. This finding is significant beyond its CVSS score: Langflow flows can be configured with tool access (code execution, API calls, file operations), so hijacking another user's flow is not just a data-exposure event — it is hijacking of an autonomous agent's authorized actions. Sysdig has separately documented the first confirmed case of "agentic ransomware," in which a human operator weaponized an AI agent (via an earlier Langflow flaw, CVE-2025-3248) to independently execute an entire extortion operation, including infrastructure provisioning. That precedent materially raises the impact ceiling for any authorization-bypass flaw in an agent-orchestration platform.

## Multi-Category Duplication
This finding is relevant to both **AI-Governance** (AI agent/system risk and incident management, autonomous-action accountability) and **Cloud-Security** (application authorization flaw, credential/tool-access exposure). Per program policy, this bundle is fully duplicated — not symlinked — under both `Case-studies/AI-Governance/2026-07-CISA-KEV-Langflow/` and `Case-studies/Cloud-Security/2026-07-CISA-KEV-Langflow/`.

## Artifacts in This Bundle
1. `01_Threat_Intelligence.md`
2. `02_Risk_Assessment.md`
3. `03_BIA.md`
4. `04_Control_Mapping.md`
5. `05_Executive_Summary.md`
6. `06_POAM_Remediation.md`
7. `README.md` — This file

## Risk Register Reference
See `Risk_Register/GRC_Intelligence_Risk_Register.xlsx`, Risk ID **RR-028**.

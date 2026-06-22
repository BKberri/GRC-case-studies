# Case Study: LiteLLM AI Gateway Multiple Vulnerabilities

**Category:** Cloud-Security (duplicated in AI-Governance — see note below)
**Source:** Obsidian Security disclosure / CISA KEV (related CVEs)
**CVE IDs:** CVE-2026-42271 (primary), CVE-2026-47101, CVE-2026-47102, CVE-2026-40217
**Disclosure Date:** 2026-06-11 (active exploitation reporting continued through 2026-06-16/06-18)
**Risk Rating:** Critical
**Bundle Date:** 2026-06-22

## Summary
A vulnerability chain in the LiteLLM AI gateway/proxy, led by a critical authentication bypass (CVE-2026-42271, CVSS 9.1), was disclosed by Obsidian Security on 2026-06-11. CISA subsequently added related CVEs to the KEV catalog following confirmed active exploitation. The gateway sits between applications and upstream LLM providers, making compromise a risk to provider credentials, model usage authorization, and potentially internal network resources via SSRF.

## Judgment Call — Inclusion Despite Timing
This case's primary disclosure date falls just before this run's strict 7-day lookback window (2026-06-15–2026-06-22). It is included per the GRC Intelligence Monitoring program's standing instruction to treat AI/LLM platform vulnerabilities as highest priority, and because active-exploitation reporting continued into the monitoring window. This is a documented, deliberate judgment call — see the Step 9 run summary for full rationale.

## Multi-Category Duplication
This finding is relevant to both **AI-Governance** (AI system risk/incident management) and **Cloud-Security** (gateway infrastructure security). Per program policy, this bundle is fully duplicated — not symlinked — under both `Case-studies/AI-Governance/2026-06-CISA-KEV-LiteLLM-AIGateway/` and `Case-studies/Cloud-Security/2026-06-CISA-KEV-LiteLLM-AIGateway/`.

## Artifacts in This Bundle
1. `01_Threat_Intelligence.md`
2. `02_Risk_Assessment.md`
3. `03_BIA.md`
4. `04_Control_Mapping.md`
5. `05_Executive_Summary.md`
6. `06_POAM_Remediation.md`
7. `README.md` — This file

## Risk Register Reference
See `Risk_Register/GRC_Intelligence_Risk_Register.xlsx`, Risk ID **RR-022**.

# Case Study: Langflow AI Agent Platform — Unauthenticated Root RCE via `exec_globals` (CVE-2026-0770)

**Category:** AI-Governance (duplicated in Cloud-Security — see note below)
**Source:** CISA KEV
**CVE ID:** CVE-2026-0770
**KEV Added:** 2026-07-21 | **Federal Due Date:** 2026-07-24 (BOD 26-04, 3-day emergency mandate)
**Risk Rating:** Critical
**Bundle Date:** 2026-07-27

## Summary
Langflow — the same open-source AI agent/workflow orchestration platform behind Risk Register entry RR-028 (CVE-2026-55255, logged 2026-07-13) — has a second, unrelated critical flaw now in the CISA KEV catalog. CVE-2026-0770 (CVSS 9.8) is an unauthenticated remote code execution vulnerability in the handling of the `exec_globals` parameter passed to the `/api/v1/validate/code` endpoint, allowing an attacker with no credentials at all to execute arbitrary code as root. KEVIntel telemetry recorded in-the-wild exploitation attempts starting 2026-06-27 — over 220 attempts from 64 unique source IPs — weeks before CISA's 2026-07-21 KEV addition. Observed payloads attempted to deploy malware and harvest AWS credentials, environment variables, and container instance metadata from compromised hosts.

## Why This Is Flagged as Highest Priority
Per the GRC Intelligence Monitoring program's standing instruction, AI/LLM and AI-agent platform vulnerabilities are treated as highest priority regardless of category. This is Langflow's **fourth** actively-exploited KEV entry in roughly fourteen months (CVE-2025-3248 in May 2025 — since weaponized by the JadePuffer ransomware gang to dump Langflow PostgreSQL databases; CVE-2026-33017 in March 2026; CVE-2026-55255 in July 2026; and now CVE-2026-0770). Unlike RR-028's authorization-bypass flaw, this vulnerability requires no authentication whatsoever and grants root — the most severe access tier available on the host. The recurring pattern of critical, unauthenticated flaws in a single AI agent platform that enterprises are rapidly adopting for autonomous workflows is itself a governance signal: organizations treating Langflow as a trusted internal tool are exposing root-level infrastructure access and cloud credentials to any unauthenticated internet scanner.

## Multi-Category Duplication
This finding is relevant to both **AI-Governance** (AI agent/system risk, vendor security debt in agentic tooling, autonomous-action accountability) and **Cloud-Security** (unauthenticated RCE leading directly to AWS credential and container metadata theft). Per program policy, this bundle is fully duplicated — not symlinked — under both `Case-studies/AI-Governance/2026-07-CISA-KEV-Langflow-ExecGlobals-RCE/` and `Case-studies/Cloud-Security/2026-07-CISA-KEV-Langflow-ExecGlobals-RCE/`.

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
- **CVE/Advisory ID:** CVE-2026-0770 (GHSA-g22f-v6f7-2hrh, ZDI-CAN-27325, ZDI-26-036)
- **CVSS Score:** 9.8 Critical (AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H)
- **Affected Technology:** Langflow (open-source AI agent/workflow builder), versions 0 through 1.7.3
- **Frameworks Applied:** NIST AI RMF, ISO/IEC 42001:2023, NIST CSF 2.0, NIST 800-53 Rev 5, EU AI Act, MITRE ATT&CK, MITRE ATLAS
- **Exploitation Status:** Actively exploited since at least 2026-06-27 (220+ recorded attempts from 64 source IPs)
- **CISA Due Date:** 2026-07-24 (BOD 26-04 emergency mandate)

## Related Cases
- Risk Register RR-028 / `2026-07-CISA-KEV-Langflow` — prior Langflow authorization-bypass (IDOR) finding, CVE-2026-55255, logged 2026-07-13. Distinct vulnerability, same vendor, reinforces the pattern noted above.

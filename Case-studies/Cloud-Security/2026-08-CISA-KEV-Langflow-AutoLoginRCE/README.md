# 2026-08-CISA-KEV-Langflow-AutoLoginRCE
**Date:** 2026-08-10 | **Source:** CISA KEV | **Category:** AI-Governance / Cloud-Security (dual) | **Risk Rating:** Critical

## Summary
IBM Langflow OSS versions 1.0.0-1.10.0 contain a code injection vulnerability (CVE-2026-9198, CVSS 9.8) that lets an unauthenticated attacker chain two API endpoints into full remote code execution on a default deployment. The `/api/v1/auto_login` endpoint fails to enforce authentication and mints SUPERUSER tokens for any network caller; the attacker then presents that forged token to `/api/v1/validate/code`, which evaluates attacker-supplied Python directly through `exec()`. IBM disclosed and patched the flaw on 2026-07-17 (fixed in 1.10.1); CISA confirmed active exploitation and added it to the KEV catalog on 2026-08-04. This is the third distinct Langflow CVE logged in this register in under three months (see RR-028, RR-035), reinforcing a persistent pattern of AI agent/workflow platforms shipping insecure-by-default authentication on their management APIs.

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
- **CVE/Advisory ID:** CVE-2026-9198
- **CVSS Score:** 9.8 (Critical)
- **Affected Technology:** IBM Langflow OSS 1.0.0-1.10.0 (fixed in 1.10.1)
- **Frameworks Applied:** NIST AI RMF, ISO 42001, NIST CSF 2.0, NIST 800-53 Rev 5, ISO 27001:2022, CIS Controls v8
- **Exploitation Status:** Actively exploited (CISA KEV, added 2026-08-04)
- **CISA Due Date:** 2026-08-25 (standard 21-day KEV remediation window for non-emergency-tier additions; confirm against catalog entry at remediation)

## Related Cases
Third entry in a recurring pattern: `AI-Governance/2026-07-CISA-KEV-Langflow` (CVE-2026-55255) and `AI-Governance/2026-07-CISA-KEV-Langflow-ExecGlobals-RCE` (CVE-2026-0770). All three findings share a root cause class — insecure-by-default authentication or code-execution surfaces on Langflow's REST API — and should be read together when briefing leadership on AI agent platform risk exposure.

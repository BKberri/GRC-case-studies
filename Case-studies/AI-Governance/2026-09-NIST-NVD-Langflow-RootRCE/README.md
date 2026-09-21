# 2026-09-NIST-NVD-Langflow-RootRCE
**Date:** 2026-09-21 | **Source:** NIST NVD | **Category:** AI-Governance (dual: Cloud-Security) | **Risk Rating:** Critical

## Summary
IBM Langflow OSS, a visual builder for LLM/AI-agent workflows this program has tracked across four prior findings since June, disclosed CVE-2026-12944 (CVSS 9.6) — arbitrary Python code execution as root (UID 0) via socket/urllib imports permitted in user-submitted workflow components. Exploitation enables AWS credential theft via IMDSv1 SSRF, arbitrary file exfiltration, and lateral movement from any host running an affected Langflow instance. This is the fifth Langflow security finding logged by this program in under 90 days (following LiteLLM/AI-Gateway in June, two separate CVEs in July, and an auto-login RCE in August), establishing Langflow as this program's single most frequently-recurring vendor-specific risk pattern.

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
- **CVE/Advisory ID:** CVE-2026-12944
- **CVSS Score:** 9.6 (Critical) — CWE-918 (Server-Side Request Forgery, chained with unsafe code execution)
- **Affected Technology:** IBM Langflow OSS, versions 1.0.0-1.10.0
- **Frameworks Applied:** NIST AI RMF, ISO 42001, NIST CSF 2.0, NIST 800-53 Rev 5, MITRE ATLAS
- **Exploitation Status:** No CISA KEV listing as of this sweep; published to NVD 2026-09-14. Given Langflow's history of rapid weaponization (its prior four findings all reached active exploitation or KEV status within weeks), this program treats it as high-likelihood-imminent rather than purely theoretical.
- **Vendor Due Date:** No KEV listing; vendor fix available in versions beyond 1.10.0 per NVD record

## Related Cases
Fifth consecutive Langflow finding this program has tracked: `2026-06-CISA-KEV-Langflow`, `2026-07-CISA-KEV-Langflow`, `2026-07-CISA-KEV-Langflow-ExecGlobals-RCE`, `2026-08-CISA-KEV-Langflow-AutoLoginRCE`, and now this finding. Given this frequency, this program recommends organizations running Langflow in any environment with AWS credential access treat it as a standing high-risk asset requiring compensating network controls regardless of patch status, not solely a per-CVE remediation exercise.

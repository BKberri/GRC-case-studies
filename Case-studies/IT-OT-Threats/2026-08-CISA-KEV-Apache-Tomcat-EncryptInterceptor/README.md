# 2026-08-CISA-KEV-Apache-Tomcat-EncryptInterceptor
**Date:** 2026-08-10 | **Source:** CISA KEV | **Category:** IT-OT-Threats | **Risk Rating:** Critical

## Summary
Apache Tomcat versions 11.0.20, 10.1.53, and 9.0.116 contain a missing-encryption vulnerability (CVE-2026-34486, CVSS 7.5) in the optional clustering EncryptInterceptor component. The prior fix for a related flaw (CVE-2026-29146) altered message processing in a way that allows EncryptInterceptor to be bypassed entirely, so messages exchanged between Tomcat cluster nodes that should be pre-shared-key encrypted are instead forwarded in the clear. CISA added the CVE to its KEV catalog on 2026-08-04 with an August 7 remediation deadline, and Unit 42 has reported a Chinese-speaking threat actor actively exploiting the flaw as part of an AI-assisted attack campaign that deploys Java deserialization-based reverse shells against vulnerable servers. Apache Tomcat is one of the most widely deployed Java application servers in enterprise environments, making this a broad-surface finding.

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
- **CVE/Advisory ID:** CVE-2026-34486
- **CVSS Score:** 7.5 (High)
- **Affected Technology:** Apache Tomcat 11.0.20, 10.1.53, 9.0.116 (fixed in 11.0.21, 10.1.54, 9.0.117)
- **Frameworks Applied:** NIST CSF 2.0, NIST 800-53 Rev 5, ISO 27001:2022, CIS Controls v8
- **Exploitation Status:** Actively exploited (CISA KEV, added 2026-08-04); AI-assisted attack campaign observed by Unit 42
- **CISA Due Date:** 2026-08-07 (per public reporting of the CISA deadline)

## Related Cases
No direct prior Apache Tomcat entries in this register. Notable for being one of the first cases in this program explicitly tied to an AI-assisted attacker tradecraft campaign rather than purely automated or manual exploitation — worth flagging in the Executive Summary's AI Governance Watch section as a threat-actor-side AI use case, distinct from the AI-platform-vulnerability cases (Langflow, CoreBreak) logged elsewhere this week.

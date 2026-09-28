# 2026-09-CISA-KEV-F5-BigIP-APM-OAuthRCE
**Date:** 2026-09-28 | **Source:** CISA KEV (added 2026-09-22) | **Category:** Cloud-Security | **Risk Rating:** Critical

## Summary
F5 BIG-IP Access Policy Manager (APM) contains a heap-based buffer overflow (CVE-2026-94127, CWE-122) that allows an unauthenticated attacker to achieve remote code execution when APM is configured as an OAuth Authorization Server. CISA added the CVE to the KEV catalog on 2026-09-22 with a three-day remediation deadline of 2026-09-25, confirming active exploitation. CVSS 4.0 rates the flaw 9.3, Critical (AV:N/AC:L/AT:N/PR:N/UI:N/VC:H/VI:H/VA:H/SC:N/SI:N/SA:N). Because BIG-IP APM commonly serves as the identity-aware proxy fronting VPN, SSO, and OAuth-based application access, unauthenticated code execution on the device compromises the authentication chokepoint for the entire application portfolio it protects, not just the device itself. F5's advisory scopes the vulnerability precisely: deployments using APM strictly as an OAuth Client or Resource Server, without an Authorization Server profile configured, are not affected, which makes an accurate configuration inventory the necessary first step before remediation.

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
- **CVE/Advisory ID:** CVE-2026-94127
- **CVSS Score:** 9.3 Critical (CVSS 4.0, CVSS-B)
- **Affected Technology:** F5 BIG-IP Access Policy Manager (APM) configured as an OAuth Authorization Server; versions 21.1.0 before Hotfix-BIGIP-21.1.0.2.0.30.22-ENG, 17.5.0 before Hotfix-BIGIP-17.5.1.9.0.160.12-ENG, and 17.1.0 before Hotfix-BIGIP-17.1.3.5.0.41.14-ENG
- **Frameworks Applied:** NIST CSF 2.0, NIST SP 800-53 Rev 5, ISO 27001:2022, CIS Controls v8
- **Exploitation Status:** Actively exploited; CISA KEV addition 2026-09-22
- **CISA Remediation Due Date:** 2026-09-25

## Related Cases
Continues this program's recurring pattern of identity-aware proxy and access-gateway KEV entries, the class of infrastructure this program treats as top priority because compromise there cascades into every application and session the device authenticates. Cross-referenced to Risk Register entry RR-082. Report period: 2026-09-21 to 2026-09-28.

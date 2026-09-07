# 2026-09-CISA-KEV-PaperCut-NGMF-AuthBypassRCE
**Date:** 2026-09-07 | **Source:** CISA KEV (added 2026-08-31) | **Category:** IT-OT-Threats | **Risk Rating:** Critical

## Summary
PaperCut NG/MF print-management server software contains two chained vulnerabilities added to the CISA KEV catalog on 2026-08-31. CVE-2026-81578 is a missing-authentication flaw in the web management interface that lets an unauthenticated remote attacker modify system configuration parameters. CVE-2026-82078 is an unsafe reflection vulnerability that allows an attacker who can manipulate configuration parameters to execute arbitrary Java bytecode residing on the application classpath, in the security context of the PaperCut server process. CISA's own catalog notes the two are designed to be chained. Public reporting identifies more than 1,000 internet-exposed PaperCut instances. PaperCut print-management software has prior, well-documented history as a ransomware initial-access vector (the 2023 Cl0p/Bl00Dy campaigns exploiting earlier PaperCut CVEs), which materially raises the priority of this finding beyond what the CVSS-independent "chained auth-bypass-to-RCE" pattern alone would suggest.

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
- **CVE/Advisory ID:** CVE-2026-81578 (missing authentication) and CVE-2026-82078 (unsafe reflection / RCE)
- **CVSS Score:** Not published by CISA in the KEV catalog entry; independently assessed as Critical given the unauthenticated-config-modification-to-arbitrary-code-execution chain
- **Affected Technology:** PaperCut NG/MF (see PaperCut security bulletin dated 2026-08-27 for exact affected version ranges)
- **Frameworks Applied:** NIST CSF 2.0, NIST 800-53 Rev 5, ISO 27001:2022, CIS Controls v8
- **Exploitation Status:** KEV-listed 2026-08-31 (confirmed exploited or credible near-term exploitation risk per CISA's KEV inclusion criteria); >1,000 internet-exposed instances reported
- **CISA Remediation Due Date:** 2026-09-14

## Related Cases
PaperCut has a documented history in this threat category — earlier PaperCut MF/NG vulnerabilities (CVE-2023-27350/27351) were the confirmed initial-access vector for Cl0p and Bl00Dy ransomware campaigns against print-management infrastructure in 2023. This case should be read alongside that history: print-management servers are a recurring, often under-prioritized enterprise infrastructure category that this program flags as warranting the same patch-SLA discipline typically reserved for perimeter network appliances.

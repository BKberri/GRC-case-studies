# 2026-09-CISA-KEV-SharePoint-CodeInjection
**Date:** 2026-09-28 | **Source:** CISA KEV (added 2026-09-25) | **Category:** IT-OT-Threats | **Risk Rating:** High

## Summary
CISA added CVE-2026-65660, a code injection vulnerability in on-premises Microsoft SharePoint Server, to the Known Exploited Vulnerabilities catalog on 2026-09-25, confirming active exploitation. Microsoft rates the flaw 8.8 (High) on CVSS 3.1, with a vector of AV:N/AC:L/PR:L/UI:N/S:U/C:H/I:H/A:H — notably, exploitation requires the attacker to already hold low-privilege, authenticated access to the SharePoint environment; this is not an unauthenticated, pre-auth RCE. The most realistic attack scenario is a compromised low-privilege internal account, or an external party with limited guest/collaboration access, escalating that foothold to full code execution. Affected products are SharePoint Enterprise Server 2016, SharePoint Server 2019, and SharePoint Server Subscription Edition — on-premises only; SharePoint Online/Microsoft 365 is unaffected. Third-party research firm Previdian reports observing a two-stage exploitation pattern in real-world attempts. CISA's federal remediation deadline is 2026-09-28 — the same date as this report's publication — meaning the deadline has just elapsed for any organization that has not yet patched.

## Artifact Index
| File | Description |
|---|---|
| 01_Threat_Intelligence.md | Full technical threat intelligence report |
| 02_Risk_Assessment.md | Risk scoring, inherent/residual risk, and risk model implications |
| 03_BIA.md | Business impact analysis |
| 04_Control_Mapping.md | Framework control mapping |
| 05_Executive_Summary.md | Board/CISO-level summary |
| 06_POAM_Remediation.md | Plan of Action & Milestones |

## Key Facts
- **CVE/Advisory ID:** CVE-2026-65660 (Microsoft SharePoint Code Injection, CWE-94)
- **CVSS Score:** 8.8 HIGH — CVSS:3.1/AV:N/AC:L/PR:L/UI:N/S:U/C:H/I:H/A:H (note: PR:L — low privileges required, not unauthenticated)
- **Affected Technology:** SharePoint Enterprise Server 2016 (before 16.0.5565.1001), SharePoint Server 2019 (before 16.0.10417.20198), SharePoint Server Subscription Edition (before 16.0.19725.20522) — on-premises only
- **Frameworks Applied:** NIST CSF 2.0, NIST SP 800-53 Rev 5, ISO 27001:2022, CIS Controls v8
- **Exploitation Status:** Actively exploited; CISA KEV addition 2026-09-25; two-stage exploitation pattern reported by Previdian
- **CISA Remediation Due Date:** 2026-09-28 (elapsed as of report publication)

## Related Cases
Logged against Risk Register row RR-084, report period 2026-09-21 to 2026-09-28. This is at least the program's second-or-third distinct SharePoint on-premises KEV finding of 2026, continuing directly from the July 2026 case study on SharePoint machine-key theft (2026-07-CISA-KEV-SharePoint-MachineKeyTheft) and consistent with this program's earlier tracking that a third of four related SharePoint CVEs disclosed earlier this year were confirmed exploited. Taken together, these findings establish on-premises SharePoint Server as a recurring, high-value attacker target throughout 2026 — a pattern discussed in Section 5.3 of 02_Risk_Assessment.md, with a corresponding strategic recommendation to evaluate migration to SharePoint Online/Microsoft 365 set out in 06_POAM_Remediation.md §6.3. This case also lands in the same reporting week as the sibling Citrix NetScaler zero-day (CS-ITOT-2026-09-001) and Check Point Quantum Gateway (CS-ITOT-2026-09-002) case studies.

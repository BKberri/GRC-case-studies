# Case Study: Microsoft SharePoint Server Deserialization RCE with Machine Key Theft (CVE-2026-50522)

**Category:** IT-OT-Threats
**Source:** CISA KEV
**CVE ID:** CVE-2026-50522
**KEV Added:** 2026-07-22 | **Federal Due Date:** 2026-07-25 (BOD 26-04, 3-day emergency mandate)
**Risk Rating:** Critical
**Bundle Date:** 2026-07-27

## Summary
On-premises Microsoft SharePoint Server carries a critical deserialization vulnerability (CVE-2026-50522, CVSS 9.8) that allows an attacker authenticated as at least a Site Owner to write and execute arbitrary code remotely. A public proof-of-concept exploit landed 2026-07-20, and active exploitation began within hours — with confirmed attacker behavior pulling SharePoint IIS machine keys in a single request, then forging authentication tokens that survive a subsequent patch. This is the third SharePoint Server vulnerability exploited in an ongoing wave of attacks this July, following CVE-2026-56164 and CVE-2026-58644 (both weaponized as zero-days ahead of the July Patch Tuesday fix), and a fourth vulnerability, CVE-2026-45659, was also confirmed exploited earlier in the month.

## Why This Case Requires Special Remediation Guidance
Standard vulnerability remediation guidance ("apply the patch") is insufficient here and, if followed alone, is actively misleading: patching CVE-2026-50522 closes the code-execution vector but does **not** invalidate machine keys an attacker may have already stolen. An attacker holding stolen keys can forge valid authentication tokens indefinitely, regardless of patch status, until the keys are specifically rotated. Security researchers (watchTowr) have explicitly warned that "patching is not enough" for this vulnerability — this case's POA&M reflects that guidance directly.

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
- **CVE/Advisory ID:** CVE-2026-50522
- **CVSS Score:** 9.8 Critical (AV:N/AC:L/PR:H(SiteOwner)/UI:N/S:U/C:H/I:H/A:H — network-exploitable, low complexity per Microsoft's own assessment)
- **Affected Technology:** Microsoft SharePoint Server — all supported on-premises versions (Subscription Edition, 2019, 2016)
- **Frameworks Applied:** NIST CSF 2.0, NIST 800-53 Rev 5, ISO 27001, CIS Controls v8
- **Exploitation Status:** Actively exploited since public PoC release on 2026-07-20; part of a broader wave of SharePoint zero-day exploitation this month
- **CISA Due Date:** 2026-07-25 (BOD 26-04 emergency mandate)

## Related Cases
- `2026-06-MSRC-PatchTuesday-WormableKernel` (prior reporting period) — same July Patch Tuesday cycle context
- Related but not separately bundled this period: CVE-2026-56164, CVE-2026-58644, CVE-2026-45659 — additional SharePoint Server vulnerabilities exploited in the same ongoing attack wave, referenced in the Threat Intelligence artifact for context

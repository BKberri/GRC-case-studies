# 2026-09-CISA-KEV-AdobeCommerce-Magento-AuthzBypass
**Date:** 2026-09-28 | **Source:** CISA KEV (added 2026-09-24) | **Category:** Cloud-Security | **Risk Rating:** Critical

## Summary
CVE-2026-71362, an Incorrect Authorization vulnerability in the core platform logic shared by Adobe Commerce and Magento Open Source, was added to the CISA Known Exploited Vulnerabilities (KEV) Catalog on 2026-09-24 with a reported 3-day federal remediation due date of 2026-09-27. Independent vulnerability-intelligence trackers (Tenable, IONIX, Strix, cve-security.com) score the flaw 9.1 (CRITICAL) and describe it as enabling privilege escalation through a broken authorization check — an attacker reaching functionality or data a properly enforced authorization control should have blocked, potentially including admin-panel functions, customer PII, or payment-card-scoped storefront logic depending on which check is broken. SecurityWeek reported that exploitation attempts began essentially immediately after public disclosure, and Belgium's national CERT (CCB Belgium) independently issued a critical-severity patch-now advisory, underscoring both the speed of weaponization and the multi-jurisdictional attention this finding drew. This is the second Adobe Commerce/Magento KEV entry this program has logged in roughly 3.5 months, following the June 2026 Mirasvit extension RCE case study, and confirms the e-commerce platform as a recurring, payment-card-relevant risk surface.

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
- **CVE/Advisory ID:** CVE-2026-71362 — "Adobe Commerce and Magento Incorrect Authorization Vulnerability"
- **CVSS Score:** 9.1 (CRITICAL) as reported by third-party vulnerability-intelligence trackers (Tenable, IONIX, Strix, cve-security.com); not yet cross-verified against NVD/Adobe's official security bulletin at time of publication — see 02_Risk_Assessment.md for the verification caveat before this figure is used for SLA-bound remediation commitments.
- **Affected Technology:** Adobe Commerce (Cloud and on-premise) and Magento Open Source — core platform authorization logic
- **Frameworks Applied:** NIST CSF 2.0, NIST SP 800-53 Rev 5, ISO 27001:2022, CIS Controls v8, PCI-DSS v4.0
- **Exploitation Status:** Actively exploited; reported near-immediate exploitation following public disclosure
- **CISA KEV Addition Date:** 2026-09-24 | **Reported Remediation Due Date:** 2026-09-27
- **Risk Register Cross-Reference:** RR-083
- **Report Period:** 2026-09-21 to 2026-09-28

## Related Cases
This is the **second** Adobe Commerce/Magento KEV entry this program has logged in approximately 3.5 months, and it confirms the platform as a recurring finding class rather than an isolated event:

- **2026-06-CISA-KEV-Magento-Mirasvit** (Cloud-Security) — the precedent case: an actively exploited unauthenticated RCE in a third-party Magento/Adobe Commerce extension (Mirasvit), which is where this program first mapped PCI-DSS v4.0 alongside the standard NIST/ISO/CIS stack, on the basis that e-commerce-platform findings carry payment-industry compliance obligations the core IT/OT framework track does not capture on its own. This case study applies that same precedent — PCI-DSS v4.0 is mapped again in 04_Control_Mapping.md (Section 3.5), citing Requirement 6.3.3 (patching critical/high vulnerabilities within defined timeframes) and Requirement 11.3 (vulnerability scanning).
- Unlike the Mirasvit case, CVE-2026-71362 sits in the **core platform authorization logic** itself rather than a third-party extension — a materially broader blast radius, since it affects every Adobe Commerce/Magento deployment regardless of installed extensions.
- **2026-09-CISA-KEV-WSO2-MultiProduct-PathTraversal** (Cloud-Security) — a sibling case study from the same KEV disclosure batch this week (per The Hacker News' joint reporting on both flaws). The two were disclosed and added to KEV in close proximity but are unrelated technically; this case study does not duplicate the WSO2 technical analysis, which is covered separately.

Any organization operating Adobe Commerce or Magento Open Source — particularly those serving EU customers, given CCB Belgium's independent advisory — should treat this as confirmation that e-commerce platform patching cadence needs to be tracked as its own risk category, not folded into general application patching SLAs.

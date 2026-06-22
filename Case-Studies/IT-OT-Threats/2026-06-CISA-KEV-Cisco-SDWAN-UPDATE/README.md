# Case Study: Cisco Catalyst SD-WAN Manager — Second KEV Entry (CVE-2026-20262)

**Category:** IT-OT-Threats
**Source:** CISA KEV
**Date Added to KEV:** 2026-06-15
**Risk Rating:** High (escalated from base CVSS 6.5 due to active exploitation, root impact, and critical asset)
**Bundle Date:** 2026-06-22

## Change Since Original
- **Original bundle date:** 2026-06-15 (`IT-OT-Threats/2026-06-CISA-KEV-Cisco-SDWAN`, CVE-2026-20245)
- **What changed:** A second, independent Cisco Catalyst SD-WAN Manager vulnerability (CVE-2026-20262 — path traversal leading to arbitrary file write and root escalation) was added to the CISA KEV catalog on 2026-06-15, with new Cisco-issued fixed software released this week.
- **Why this qualifies for a new bundle:** Per the monitoring program's escalation rules, a new vendor patch was released this week for a newly-added KEV entry referencing the same affected product (Cisco Catalyst SD-WAN Manager). This is tracked as a distinct UPDATE bundle rather than merged into the original case because the two CVEs represent independent attack chains requiring independent remediation tracking.

## Summary
CISA added CVE-2026-20262, a path-traversal vulnerability in Cisco Catalyst SD-WAN Manager, to its Known Exploited Vulnerabilities catalog on 2026-06-15. An authenticated attacker can write arbitrary files to the underlying OS and escalate to root, gaining full control of the enterprise WAN management plane. This is the second Cisco SD-WAN Manager KEV entry within two weeks. Cisco has released fixed software; no workaround exists.

## Artifacts in This Bundle
1. `01_Threat_Intelligence.md` — Vulnerability detail, exploitation summary, framework mapping
2. `02_Risk_Assessment.md` — Likelihood/impact scoring, residual risk
3. `03_BIA.md` — Business impact across confidentiality/integrity/availability
4. `04_Control_Mapping.md` — Control mapping to NIST CSF 2.0, NIST 800-53, ISO 27001, CIS Controls v8
5. `05_Executive_Summary.md` — Plain-English summary for CISO/board audience
6. `06_POAM_Remediation.md` — Remediation plan with owners and target dates
7. `README.md` — This file

## Risk Register Reference
See `Risk_Register/GRC_Intelligence_Risk_Register.xlsx`, Risk ID **RR-017**.

## Related Case
`IT-OT-Threats/2026-06-CISA-KEV-Cisco-SDWAN` (CVE-2026-20245, original bundle, 2026-06-15)

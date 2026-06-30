# Case Study: PTC Windchill/FlexPLM Unauthenticated RCE (CVE-2026-12569)

**Category:** IT-OT-Threats
**Source:** CISA KEV
**Date Added to KEV:** 2026-06-23
**Risk Rating:** Critical
**Bundle Date:** 2026-06-29

## Summary
CISA added CVE-2026-12569, a critical (CVSS 9.8) unauthenticated remote code execution vulnerability in PTC's Windchill and FlexPLM product lifecycle management platforms, to its KEV catalog on 2026-06-23, with confirmed active exploitation and an accelerated 3-day federal remediation deadline (2026-06-28) under BOD 26-04. These platforms typically store sensitive engineering IP, CAD data, bills of materials, and supplier/partner data, making this a high-value target for industrial espionage in addition to standard extortion risk.

## Artifacts in This Bundle
1. `01_Threat_Intelligence.md`
2. `02_Risk_Assessment.md`
3. `03_BIA.md`
4. `04_Control_Mapping.md`
5. `05_Executive_Summary.md`
6. `06_POAM_Remediation.md`
7. `README.md` — This file

## Risk Register Reference
See `Risk_Register/GRC_Intelligence_Risk_Register.xlsx`, Risk ID **RR-025**.

## Key Risk Driver
Unauthenticated RCE on a platform storing high-value intellectual property, with confirmed active exploitation and a compressed 3-day federal remediation window — elevated further for defense/aerospace organizations subject to CMMC/DFARS CUI-handling obligations.

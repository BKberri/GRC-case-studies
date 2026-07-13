# Case Study: Joomla! Extension Ecosystem — Mass Unauthenticated File-Upload RCE (4 CVEs)

**Category:** IT-OT-Threats
**Source:** CISA KEV
**CVE IDs:** CVE-2026-48908 (JoomShaper SP Page Builder), CVE-2026-56290 (Joomlack Page Builder), CVE-2026-48939 (iCagenda), CVE-2026-56291 (Balbooa Forms)
**KEV Added:** 2026-07-07 (CVE-2026-48908, CVE-2026-56290) and 2026-07-10 (CVE-2026-48939, CVE-2026-56291)
**Federal Due Dates:** 2026-07-10 and 2026-07-13 respectively (BOD 26-04, 3-day emergency mandate on each)
**Risk Rating:** Critical
**Bundle Date:** 2026-07-13

## Summary
Within a single 7-day window, CISA added four separate, unrelated Joomla! extensions to the KEV catalog for the same vulnerability class: unauthenticated arbitrary file upload leading to remote code execution (all four rated CVSS 10.0). The affected extensions — JoomShaper's SP Page Builder, Joomlack's Page Builder, iCagenda, and Balbooa Forms — are independently developed, third-party components with no shared codebase, indicating this is a pattern of convergent zero-day discovery/exploitation across the Joomla extension ecosystem rather than a single supply-chain event. Each flaw allows an unauthenticated attacker to upload a PHP web shell (or equivalent) directly to the web root and execute it, achieving full remote code execution on the underlying host.

## Why This Is Bundled as One Case
Per program methodology, findings sharing a common root-cause pattern, common remediation strategy, and common disclosure window are consolidated into a single analytical case rather than published as near-duplicate bundles. Each CVE remains individually risk-registered (own Risk ID, own row) because each is a distinct finding on a distinct product — but the threat intelligence, business impact, and remediation guidance below apply uniformly across all four, and a combined narrative avoids diluting analytical value across four nearly identical write-ups.

## Relationship to Prior Case
This is a **distinct finding**, not a revision, relative to the existing `IT-OT-Threats/2026-06-CISA-KEV-Joomla-JCE` case (CVE-2026-48907, JCE Editor plugin) — same CMS ecosystem and same broad vulnerability class (unauthenticated file-upload RCE in a Joomla extension), but different vendor, different plugin, different CVE, and its own Risk Register row. The two cases are cross-referenced in each other's README so the pattern (repeated file-upload zero-days across the Joomla extension ecosystem) is visible without implying one supersedes the other.

## Artifacts in This Bundle
1. `01_Threat_Intelligence.md`
2. `02_Risk_Assessment.md`
3. `03_BIA.md`
4. `04_Control_Mapping.md`
5. `05_Executive_Summary.md`
6. `06_POAM_Remediation.md`
7. `README.md` — This file

## Risk Register Reference
See `Risk_Register/GRC_Intelligence_Risk_Register.xlsx`, Risk IDs **RR-030, RR-031, RR-032, RR-033** (one row per CVE).

# Case Study: Adobe ColdFusion RDS Path Traversal — Remote Code Execution (CVE-2026-48282)

**Category:** IT-OT-Threats
**Source:** CISA KEV
**CVE ID:** CVE-2026-48282
**KEV Added:** 2026-07-07 | **Federal Due Date:** 2026-07-10 (BOD 26-04, 3-day emergency mandate)
**Risk Rating:** Critical
**Bundle Date:** 2026-07-13

## Summary
CVE-2026-48282 is a maximum-severity (CVSS 10.0) path traversal vulnerability in Adobe ColdFusion's Remote Development Services (RDS) FILEIO handler (`/CFIDE/main/ide.cfm?ACTION=FILEIO`). Insufficient path validation allows an attacker to write arbitrary files to the underlying file system — including a CFML web shell containing `cfexecute` tags — achieving full remote code execution as the ColdFusion service account (`NT AUTHORITY\SYSTEM` on Windows deployments). No authentication is required when RDS authentication is disabled, which is common in production deployments. Adobe patched the flaw on 2026-06-30 (APSB26-68; ColdFusion 2025 Update 10 / ColdFusion 2023 Update 21), but active exploitation was detected within roughly two hours of technical analysis going public, and CISA added the CVE to the KEV catalog on 2026-07-07 under a 3-day remediation mandate.

## Why This Matters
ColdFusion remains widely deployed for enterprise web applications, often with long operational lifespans and infrequent patch cycles — a profile that makes CVSS 10.0, unauthenticated RCE flaws in it disproportionately dangerous. The speed of exploitation here (hours, not days, after public technical detail) is consistent with this run's broader pattern of near-immediate weaponization of newly disclosed critical flaws.

## Artifacts in This Bundle
1. `01_Threat_Intelligence.md`
2. `02_Risk_Assessment.md`
3. `03_BIA.md`
4. `04_Control_Mapping.md`
5. `05_Executive_Summary.md`
6. `06_POAM_Remediation.md`
7. `README.md` — This file

## Risk Register Reference
See `Risk_Register/GRC_Intelligence_Risk_Register.xlsx`, Risk ID **RR-029**.

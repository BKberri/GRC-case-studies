# Case Study: Cisco Unified Communications Manager Static Credential RCE (CVE-2026-20384)

**Category:** IT-OT-Threats
**Source:** CISA KEV
**Date Added to KEV:** 2026-06-24
**Risk Rating:** Critical
**Bundle Date:** 2026-06-29

## Summary
CISA added CVE-2026-20384, a critical (CVSS 10.0) static/undocumented credential vulnerability in Cisco Unified Communications Manager and Unified CM Session Management Edition, to its KEV catalog on 2026-06-24. The flaw allows authentication bypass and root-level command execution on the enterprise call-control platform. CISA confirmed active exploitation and set an expedited 3-day federal remediation deadline (2026-06-27) under BOD 26-04. Root-level compromise of voice infrastructure carries both confidentiality (call interception) and availability (voice service disruption) risk.

## Artifacts in This Bundle
1. `01_Threat_Intelligence.md`
2. `02_Risk_Assessment.md`
3. `03_BIA.md`
4. `04_Control_Mapping.md`
5. `05_Executive_Summary.md`
6. `06_POAM_Remediation.md`
7. `README.md` — This file

## Risk Register Reference
See `Risk_Register/GRC_Intelligence_Risk_Register.xlsx`, Risk ID **RR-026**.

## Key Risk Driver
A static, vendor-introduced credential enabling unauthenticated root-level access to enterprise voice infrastructure, with confirmed active exploitation, an expedited 3-day federal remediation window, and potential communications-privacy/wiretapping regulatory exposure.

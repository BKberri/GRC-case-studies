# Case Study: Lantronix EDS5000 OS Command Injection (CVE-2025-67038)

**Category:** IT-OT-Threats
**Source:** CISA KEV
**Date Added to KEV:** 2026-06-23
**Risk Rating:** Critical
**Bundle Date:** 2026-06-29

## Summary
CISA added CVE-2025-67038 (CVSS 9.8) to its Known Exploited Vulnerabilities catalog on 2026-06-23. The flaw allows unauthenticated attackers to inject OS commands via the username field of the HTTP RPC module's failed-login logging routine, executing arbitrary commands as root on Lantronix EDS5000 series device servers — hardware that bridges legacy OT serial equipment to IP networks. Federal remediation due date: 2026-06-26 (3-day mandate).

## Artifacts in This Bundle
1. `01_Threat_Intelligence.md`
2. `02_Risk_Assessment.md`
3. `03_BIA.md`
4. `04_Control_Mapping.md`
5. `05_Executive_Summary.md`
6. `06_POAM_Remediation.md`
7. `README.md` — This file

## Risk Register Reference
See `Risk_Register/GRC_Intelligence_Risk_Register.xlsx`, Risk ID **RR-023**.

## Key Risk Driver
Pre-authentication, root-level command injection on a device class deployed at the IT/OT boundary — no credentials or user interaction required, and active exploitation already confirmed by CISA.

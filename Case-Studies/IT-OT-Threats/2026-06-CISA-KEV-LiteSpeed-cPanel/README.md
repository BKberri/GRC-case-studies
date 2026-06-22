# Case Study: LiteSpeed cPanel Plugin Symlink Privilege Escalation (CVE-2026-54420)

**Category:** IT-OT-Threats
**Source:** CISA KEV
**Date Added to KEV:** 2026-06-15
**Risk Rating:** Critical
**Bundle Date:** 2026-06-22

## Summary
CISA added CVE-2026-54420 (CVSS 8.5) to its Known Exploited Vulnerabilities catalog on 2026-06-15. The flaw allows an attacker with FTP or web-shell access to a single shared hosting account to escalate to root by exploiting improper symlink handling in the LiteSpeed cPanel plugin — defeating CloudLinux/CageFS tenant isolation in the process. The federal remediation due date (2026-06-18) has already passed.

## Artifacts in This Bundle
1. `01_Threat_Intelligence.md`
2. `02_Risk_Assessment.md`
3. `03_BIA.md`
4. `04_Control_Mapping.md`
5. `05_Executive_Summary.md`
6. `06_POAM_Remediation.md`
7. `README.md` — This file

## Risk Register Reference
See `Risk_Register/GRC_Intelligence_Risk_Register.xlsx`, Risk ID **RR-018**.

## Key Risk Driver
This vulnerability specifically defeats the standard tenant-isolation control (CloudLinux/CageFS) used on shared hosting infrastructure, meaning a single compromised account can lead to full multi-tenant compromise.

# Case Study: Ubiquiti UniFi OS Unauthenticated Takeover Chain (CVE-2026-34908/-34909/-34910)

**Category:** IT-OT-Threats
**Source:** CISA KEV
**Date Added to KEV:** 2026-06-23
**Risk Rating:** Critical
**Bundle Date:** 2026-06-29

## Summary
CISA added three chained, maximum-severity (CVSS 10.0 each) vulnerabilities in Ubiquiti UniFi OS to its KEV catalog on 2026-06-23. Chained together, an improper access control flaw, a path traversal flaw, and a command injection flaw allow a fully unauthenticated attacker to take complete control of any UniFi OS-powered device — network controllers, surveillance NVRs, access control hubs, and Talk appliances. Active exploitation via a Mirai/Gafgyt-class botnet campaign is confirmed. Federal remediation due date: 2026-06-26 (3-day mandate).

## Artifacts in This Bundle
1. `01_Threat_Intelligence.md`
2. `02_Risk_Assessment.md`
3. `03_BIA.md`
4. `04_Control_Mapping.md`
5. `05_Executive_Summary.md`
6. `06_POAM_Remediation.md`
7. `README.md` — This file

## Risk Register Reference
See `Risk_Register/GRC_Intelligence_Risk_Register.xlsx`, Risk ID **RR-024**.

## Key Risk Driver
A pre-authentication, maximum-severity exploit chain affecting network, video surveillance, and physical access-control infrastructure simultaneously — with confirmed botnet-based active exploitation and a known one-month patch-deployment gap.

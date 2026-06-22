# Case Study: Rockwell Automation FactoryTalk Historian SE Multiple Vulnerabilities

**Category:** IT-OT-Threats
**Source:** CISA ICS Advisory (ICSA-26-167-02)
**CVE IDs:** CVE-2025-13036, CVE-2025-44019, CVE-2025-36539
**Advisory Date:** 2026-06-16
**Risk Rating:** High
**Bundle Date:** 2026-06-22

## Summary
CISA published advisory ICSA-26-167-02 on 2026-06-16 disclosing three chained vulnerabilities in Rockwell Automation's FactoryTalk Historian SE: a critical insecure deserialization flaw (CVE-2025-13036, CVSS 9.8), hardcoded credentials (CVE-2025-44019, CVSS 8.4), and improper access control (CVE-2025-36539, CVSS 7.5). No confirmed active exploitation as of this report; not yet KEV-listed.

## Artifacts in This Bundle
1. `01_Threat_Intelligence.md`
2. `02_Risk_Assessment.md`
3. `03_BIA.md`
4. `04_Control_Mapping.md`
5. `05_Executive_Summary.md`
6. `06_POAM_Remediation.md`
7. `README.md` — This file

## Risk Register Reference
See `Risk_Register/GRC_Intelligence_Risk_Register.xlsx`, Risk ID **RR-020**.

## Key Risk Driver
FactoryTalk Historian's position at the IT/OT network boundary means a compromised historian server represents both a direct foothold and a pivot point into broader OT/ICS infrastructure.

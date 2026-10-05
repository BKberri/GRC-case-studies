# Case Study: Fortinet FortiMail Unauthenticated Path Traversal (CVE-2026-104286)

**Category:** IT-OT-Threats | **Date Identified:** 2026-10-01 | **Risk Rating:** Critical

## Overview

This case study documents CVE-2026-104286, a CVSS 9.8 unauthenticated path-traversal vulnerability in Fortinet's FortiMail secure email gateway that is under active, confirmed exploitation and, unusually, has **no vendor patch available** at the time of analysis, only an interim workaround. CISA added the CVE to its Known Exploited Vulnerabilities catalog on 2026-10-01 with a federal remediation deadline of 2026-10-04, which has already elapsed without a shipped fix.

## Why This Case Was Selected

FortiMail sits at the network perimeter as an internet-facing mail security control, meaning this flaw is remotely exploitable with no authentication and no user interaction. The combination of (1) confirmed active exploitation, (2) a perimeter/mail-infrastructure target, and (3) the absence of a vendor patch makes this a high-value case study in emergency compensating-control decision-making, a scenario GRC and security architecture professionals must be able to reason through when "apply the patch" is not yet an option.

## Artifacts in This Bundle

1. [01_Threat_Intelligence.md](01_Threat_Intelligence.md), Vulnerability technical details, exploitation timeline, framework mapping
2. [02_Risk_Assessment.md](02_Risk_Assessment.md), Likelihood/impact scoring and residual risk analysis
3. [03_BIA.md](03_BIA.md), Business impact analysis across confidentiality/integrity/availability/regulatory/reputational dimensions
4. [04_Control_Mapping.md](04_Control_Mapping.md), NIST CSF 2.0, NIST 800-53, ISO 27001, CIS Controls v8 mapping
5. [05_Executive_Summary.md](05_Executive_Summary.md), Plain-English summary for CISO/board audiences
6. [06_POAM_Remediation.md](06_POAM_Remediation.md), Plan of Action & Milestones with specific remediation steps and owners

## Key Sources

- Fortinet PSIRT Advisory FG-IR-26-175
- CISA Known Exploited Vulnerabilities Catalog (dateAdded 2026-10-01)
- SecurityWeek, "Exploited Fortinet FortiMail Zero-Day Calls for Urgent Action"
- SOCRadar, "FortiMail Zero-Day Under Active Exploitation"

---
*Part of the Blaise Kingko GRC Intelligence Program. Updated weekly with current threat intelligence and framework guidance as of the listed date.*

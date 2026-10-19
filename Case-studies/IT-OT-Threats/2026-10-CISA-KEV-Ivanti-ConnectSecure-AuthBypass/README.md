# Case Study: Ivanti Connect Secure Authentication Bypass to Command Execution (CVE-2026-104935)

**Category:** IT-OT-Threats | **Date Identified:** 2026-10-13 | **Risk Rating:** Critical

## Overview

This case study documents CVE-2026-104935, a CVSS 8.6 authentication-bypass-by-spoofing vulnerability in Ivanti Connect Secure that allowed an unauthenticated, remote attacker to execute arbitrary commands on the perimeter SSL VPN gateway. Volexity detected active exploitation in early October 2026, before Ivanti's public disclosure on 2026-10-13, and CISA added the CVE to its Known Exploited Vulnerabilities catalog the same day with a federal remediation deadline of 2026-10-16, which has already elapsed as of this report.

## Why This Case Was Selected

Connect Secure is a perimeter remote-access gateway, meaning this flaw gave attackers a pre-authentication path directly into the trusted internal network of every exposed organization, with confirmed real-world exploitation predating the vendor's own disclosure. The observed attack chain also used a second, still-unpatched privilege-escalation weakness, making this a valuable case study in the limits of "patch and consider it closed" thinking when an intrusion chain outpaces a single vendor fix.

## Artifacts in This Bundle

1. [01_Threat_Intelligence.md](01_Threat_Intelligence.md), Vulnerability technical details, exploitation timeline, framework mapping
2. [02_Risk_Assessment.md](02_Risk_Assessment.md), Likelihood/impact scoring and residual risk analysis
3. [03_BIA.md](03_BIA.md), Business impact analysis across confidentiality/integrity/availability/regulatory/reputational dimensions
4. [04_Control_Mapping.md](04_Control_Mapping.md), NIST CSF 2.0, NIST 800-53, ISO 27001, CIS Controls v8 mapping
5. [05_Executive_Summary.md](05_Executive_Summary.md), Plain-English summary for CISO/board audiences
6. [06_POAM_Remediation.md](06_POAM_Remediation.md), Plan of Action & Milestones with specific remediation steps and owners

## Key Sources

- Ivanti security advisory (CVE-2026-104935)
- CISA Known Exploited Vulnerabilities Catalog (dateAdded 2026-10-13)
- Rapid7, "Ivanti Connect Secure zero-day exploited in the wild (CVE-2026-104935)"
- CSOonline, "Hackers abuse the Ivanti Connect Secure bug to gain access without accounts"
- The Hacker News, "CISA urges immediate Ivanti Connect Secure patching"

---
*Part of the Blaise Kingko GRC Intelligence Program. Updated weekly with current threat intelligence and framework guidance as of the listed date.*

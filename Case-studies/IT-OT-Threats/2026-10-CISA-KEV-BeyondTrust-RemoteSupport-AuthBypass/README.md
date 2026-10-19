# Case Study: BeyondTrust Remote Support Authentication Bypass Exploited by Suspected Nation-State Actor (CVE-2026-102764)

**Category:** IT-OT-Threats | **Date Identified:** 2026-10-16 | **Risk Rating:** Critical

## Overview

This case study documents CVE-2026-102764, an authentication-bypass vulnerability in BeyondTrust Remote Support that a suspected China-nexus espionage actor, tracked by Mandiant as Armory Castle (formerly UNC5221) and by CrowdStrike as Warp Panda, exploited as a zero-day for approximately seven weeks before public disclosure. The attacker escalated to root, deployed the Sawfly web shell and Bareclaw tunneler malware, wiped logs, and moved laterally using compromised administrator credentials. BeyondTrust patched SaaS customers on 2026-10-08, and CISA added the CVE to its Known Exploited Vulnerabilities catalog on 2026-10-16.

## Why This Case Was Selected

This case combines three high-value elements for a GRC case study: confirmed nation-state attribution, a privileged remote-access tool as the compromised asset (meaning the blast radius extends to everything that tool was ever used to touch), and a demonstrated anti-forensic technique (log wiping) that directly challenges an organization's ability to establish a clean recovery point. Over 1,400 internet-exposed instances were identified by Shadowserver, indicating broad potential exposure.

## Artifacts in This Bundle

1. [01_Threat_Intelligence.md](01_Threat_Intelligence.md), Vulnerability technical details, exploitation timeline, framework mapping
2. [02_Risk_Assessment.md](02_Risk_Assessment.md), Likelihood/impact scoring and residual risk analysis
3. [03_BIA.md](03_BIA.md), Business impact analysis across confidentiality/integrity/availability/regulatory/reputational dimensions
4. [04_Control_Mapping.md](04_Control_Mapping.md), NIST CSF 2.0, NIST 800-53, ISO 27001, CIS Controls v8 mapping
5. [05_Executive_Summary.md](05_Executive_Summary.md), Plain-English summary for CISO/board audiences
6. [06_POAM_Remediation.md](06_POAM_Remediation.md), Plan of Action & Milestones with specific remediation steps and owners

## Key Sources

- BeyondTrust advisory BT26-05 (CVE-2026-102764)
- Canadian Centre for Cyber Security Alert AL26-025
- CISA Known Exploited Vulnerabilities Catalog (dateAdded 2026-10-16)
- BleepingComputer, "BeyondTrust patches zero-day exploited in attacks since August"
- Mandiant / Google Threat Intelligence Group reporting on Armory Castle (UNC5221) / Warp Panda

---
*Part of the Blaise Kingko GRC Intelligence Program. Updated weekly with current threat intelligence and framework guidance as of the listed date.*

# Case Study: Cisco Catalyst SD-WAN Manager Authentication Bypass (CVE-2026-76504)

**Category:** IT-OT-Threats | **Date Identified:** 2026-09-30 | **Risk Rating:** Critical

## Overview

This case study documents CVE-2026-76504, a CVSS 9.8 unauthenticated authentication-bypass vulnerability in Cisco Catalyst SD-WAN Manager (vManage) that grants attackers full administrative access via a hex-encoding trick against the web authentication endpoint. Cisco's own PSIRT discovered the flaw while investigating active exploitation reported through a customer TAC case, meaning attacker activity preceded public disclosure. No workaround exists; affected organizations must upgrade.

## Why This Case Was Selected

This is the latest in a recurring 2026 pattern of Cisco SD-WAN findings logged by this program (see the June 2026 Cisco SD-WAN case studies in this same category), reinforcing SD-WAN management infrastructure as a persistent, high-value target. The case also illustrates a GRC-relevant theme: a vulnerability discovered through incident response rather than proactive disclosure, where "patch promptly" must be paired with a retrospective compromise assessment rather than treated as sufficient on its own.

## Artifacts in This Bundle

1. [01_Threat_Intelligence.md](01_Threat_Intelligence.md), Vulnerability technical details, exploitation timeline, framework mapping
2. [02_Risk_Assessment.md](02_Risk_Assessment.md), Likelihood/impact scoring and residual risk analysis
3. [03_BIA.md](03_BIA.md), Business impact analysis across confidentiality/integrity/availability/regulatory/reputational dimensions
4. [04_Control_Mapping.md](04_Control_Mapping.md), NIST CSF 2.0, NIST 800-53, ISO 27001, CIS Controls v8 mapping
5. [05_Executive_Summary.md](05_Executive_Summary.md), Plain-English summary for CISO/board audiences
6. [06_POAM_Remediation.md](06_POAM_Remediation.md), Plan of Action & Milestones with specific remediation steps and owners

## Key Sources

- Cisco Security Advisory cisco-sa-sdwan-webauth-xr8beuuU
- Cisco "Remediate Catalyst SD-WAN Security" guidance (September 2026)
- CISA Known Exploited Vulnerabilities Catalog (dateAdded 2026-09-30)
- The Hacker News, "Cisco Warns of Attackers Exploiting Critical Authentication Bypass in SD-WAN Manager"

---
*Part of the Blaise Kingko GRC Intelligence Program. Updated weekly with current threat intelligence and framework guidance as of the listed date.*

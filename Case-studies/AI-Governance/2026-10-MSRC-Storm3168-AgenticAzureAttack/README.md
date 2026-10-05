# Case Study: Storm-3168 (JADEPUFFER), First Documented Agentic/AI-Orchestrated Destructive Cloud Attack

**Category:** AI-Governance / Cloud-Security (dual-category) | **Date Identified:** 2026-09-25 | **Risk Rating:** Critical

## Overview

This case study documents a confirmed, real-world incident disclosed by Microsoft in which the threat actor Storm-3168 (JADEPUFFER) used a single exposed Azure service-principal credential to enumerate and then destroy a substantial portion of a victim's cloud infrastructure, including deliberately sabotaging backup and recovery controls, in approximately seven minutes. Microsoft characterizes the speed and coordination of the attack as consistent with AI-orchestrated, "agentic" automation rather than manual, human-paced operation.

## Why This Case Was Selected

This is a first-of-its-kind documented incident directly at the intersection of this program's two core focus areas: AI governance (the emergence of agentic/automated attack tradecraft as a distinct risk category) and cloud security (identity governance, service-principal least privilege, and backup/recovery control integrity). It is logged as a program catch-up entry, the original Microsoft disclosure (2026-09-25) fell inside the prior week's report window but was not captured at the time, consistent with this program's no-silent-drop principle for identified coverage gaps.

## Artifacts in This Bundle

1. [01_Threat_Intelligence.md](01_Threat_Intelligence.md), Attack chain, TTPs, IOCs, and the "agentic" significance of the incident
2. [02_Risk_Assessment.md](02_Risk_Assessment.md), Likelihood/impact scoring and residual risk analysis
3. [03_BIA.md](03_BIA.md), Business impact analysis across confidentiality/integrity/availability/business-continuity/regulatory dimensions
4. [04_Control_Mapping.md](04_Control_Mapping.md), NIST AI RMF, NIST CSF 2.0, NIST 800-53, ISO 42001, CIS Controls v8 mapping
5. [05_Executive_Summary.md](05_Executive_Summary.md), Plain-English summary for CISO/board audiences
6. [06_POAM_Remediation.md](06_POAM_Remediation.md), Plan of Action & Milestones with specific remediation steps and owners

## Key Sources

- Microsoft Security Blog, "Storm-3168: Agentic-driven cloud attacks using compromised service principals" (2026-09-25)
- WorkOS, "Storm-3168 explained: How compromised service principals deleted Azure resources in seven minutes"
- CyberPress, "Storm-3168 Uses Compromised Service Principals to Launch Agentic Attacks on Azure Cloud"

**Note:** This bundle is duplicated in full under both `Case-studies/AI-Governance/` and `Case-studies/Cloud-Security/` per this program's multi-category case convention.

---
*Part of the Blaise Kingko GRC Intelligence Program. Updated weekly with current threat intelligence and framework guidance as of the listed date.*

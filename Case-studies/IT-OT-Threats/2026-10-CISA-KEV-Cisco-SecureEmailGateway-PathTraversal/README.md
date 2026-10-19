# Case Study: Cisco Secure Email Gateway Path Traversal to Root Command Execution (CVE-2026-76519)

**Category:** IT-OT-Threats | **Date Identified:** 2026-10-14 | **Risk Rating:** Critical

## Overview

This case study documents CVE-2026-76519, a CVSS 9.8 relative path-traversal vulnerability in Cisco Secure Email Gateway's File Reputation (AMP) attachment scanning that allows an unauthenticated attacker to plant files and execute commands as root using nothing more than a crafted email attachment. Cisco PSIRT confirmed in-the-wild exploitation before disclosing the flaw on 2026-10-14, and CISA added it to the Known Exploited Vulnerabilities catalog the same day with a federal remediation deadline of 2026-10-17, which has already elapsed as of this report. Critically, **no workaround exists**; the fix is the only remediation path.

## Why This Case Was Selected

This is a security-scanning feature being the vulnerability itself, the appliance's own malware-scanning logic is the attack surface, making it a strong case study in the limits of "the security tool will catch it" thinking. Combined with root-level impact, confirmed active exploitation, an elapsed federal deadline, and the complete absence of a workaround, this case meets this program's highest-priority criteria for a full bundle.

## Artifacts in This Bundle

1. [01_Threat_Intelligence.md](01_Threat_Intelligence.md), Vulnerability technical details, exploitation timeline, framework mapping
2. [02_Risk_Assessment.md](02_Risk_Assessment.md), Likelihood/impact scoring and residual risk analysis
3. [03_BIA.md](03_BIA.md), Business impact analysis across confidentiality/integrity/availability/regulatory/reputational dimensions
4. [04_Control_Mapping.md](04_Control_Mapping.md), NIST CSF 2.0, NIST 800-53, ISO 27001, CIS Controls v8 mapping
5. [05_Executive_Summary.md](05_Executive_Summary.md), Plain-English summary for CISO/board audiences
6. [06_POAM_Remediation.md](06_POAM_Remediation.md), Plan of Action & Milestones with specific remediation steps and owners

## Key Sources

- Cisco PSIRT advisory cisco-sa-esa-afw-zqYJkjxp (CVE-2026-76519)
- CISA Known Exploited Vulnerabilities Catalog (dateAdded 2026-10-14)
- BetaNews, "Cisco Email Gateway CVE-2026-76519 exploited" (2026-10-15)

---
*Part of the Blaise Kingko GRC Intelligence Program. Updated weekly with current threat intelligence and framework guidance as of the listed date.*

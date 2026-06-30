# Case Study: CVE-2026-20262 — Cisco Catalyst SD-WAN Manager Path Traversal (Root Escalation)
## GRC Intelligence Program — Blaise Kingko
**Category:** IT-OT-Threats | **Sub-Category:** Network Infrastructure / WAN Management Plane
**Run Date:** 2026-06-22 | **Report Period:** 2026-06-15 to 2026-06-22

---

## Case Overview

CVE-2026-20262 is a path-traversal vulnerability (CWE-22) in Cisco Catalyst SD-WAN Manager (vManage) that allows an authenticated attacker to write arbitrary files to the underlying OS and escalate to root, via the SD-WAN Manager web UI/API file-upload flow. CISA added it to the Known Exploited Vulnerabilities catalog on 2026-06-15 — the **second** Cisco Catalyst SD-WAN Manager KEV entry within two weeks. Cisco has released fixed software; no workaround exists.

**CVSS v3.1:** 6.5 (Base) — note: base score understates operational risk; chained with file-write-to-root escalation, practical impact is Critical.
**Risk Rating (this program):** Critical (Likelihood 4 × Impact 5 = 20)

---

## Related Finding — Not a Revision

This case is **independently tracked** from `IT-OT-Threats/2026-06-CISA-KEV-Cisco-SDWAN` (CVE-2026-20245, RR-016, KEV-added 2026-06-09), which covers an authenticated local OS command injection in the same product. The two CVEs are separate attack chains with separate CWE classes, separate patch trains, and separate Risk Register entries. Organizations that remediated CVE-2026-20245 are **not** protected against CVE-2026-20262 — both must be patched independently. This case was filed as a standalone case study (rather than appended as an "Update" to the original) specifically to preserve that distinction and RR-017's own audit trail.

---

## Artifacts Included

| File | Description |
|---|---|
| `01_Threat_Intelligence.md` | CVE details, exploitation summary, relationship to the related (non-duplicate) finding, framework mapping |
| `02_Risk_Assessment.md` | Likelihood/impact scoring, residual risk |
| `03_BIA.md` | Business impact across confidentiality/integrity/availability |
| `04_Control_Mapping.md` | Control mapping to NIST CSF 2.0, NIST 800-53, ISO 27001, CIS Controls v8 |
| `05_Executive_Summary.md` | Board/CISO brief — management-plane compromise risk |
| `06_POAM_Remediation.md` | 9-action remediation plan: patch, account audit, MFA, segmentation, SIEM, log review |

---

## Risk Register Entry

**Risk ID:** RR-017 | Likelihood: 4 | Impact: 5 | Score: 20 | Rating: Critical

---

## Related Case

`IT-OT-Threats/2026-06-CISA-KEV-Cisco-SDWAN` (CVE-2026-20245, RR-016, original case, 2026-06-15) — same platform, independent vulnerability, not a revision.

---

## Key Frameworks Applied
- NIST CSF 2.0 (PR.AA-05, PR.PS-04, DE.CM-03)
- NIST SP 800-53 Rev 5 (SI-2, AC-6, AC-2, CM-3, AU-9)
- ISO/IEC 27001:2022 Annex A (A.8.8, A.5.15, A.8.22, A.8.32)
- CIS Controls v8 (Control 5, Control 7, Control 8, Control 12)

## GRC Skills Demonstrated
- Network management-plane security risk assessment
- Distinguishing a genuinely new finding from a revision in risk-register governance (avoiding both over-merging and duplicate-finding inflation)
- Privileged access management (PAM) control design for network infrastructure
- SIEM alert design for network management event monitoring

---
*GRC Intelligence Program v2.1 | Case built: 2026-06-22 | Run: Weekly Monday sweep*

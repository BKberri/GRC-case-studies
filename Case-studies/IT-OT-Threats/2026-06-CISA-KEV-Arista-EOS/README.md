# Case Study: CVE-2026-7473 — Arista Networks EOS Tunnel Traffic Policy Bypass (No Patch Planned)
## GRC Intelligence Program — Blaise Kingko
**Category:** IT-OT-Threats | **Sub-Category:** Network Infrastructure
**Run Date:** 2026-06-15 | **Report Period:** 2026-06-08 to 2026-06-15

---

## Case Overview

Arista Networks EOS contains an incomplete comparison vulnerability (CWE-697) that causes the OS to process network traffic from tunnel endpoints not configured in the tunnel policy, effectively bypassing intended network segment isolation. CISA added CVE-2026-7473 to the Known Exploited Vulnerabilities catalog on June 9, 2026, confirming active exploitation. **Arista has confirmed no patch will be developed**, citing deployment impact concerns.

This case is notable for demonstrating the GRC challenge of a permanently unpatched actively exploited vulnerability requiring compensating control design and formal risk acceptance rather than the standard patch-and-close remediation path.

**CVSS v3.1:** 6.9 Medium (KEV listing indicates real-world exploitation severity exceeds CVSS score)
**Risk Rating (this program):** High (Likelihood 4 × Impact 4 = 16)

---

## Artifacts Included

| File | Description |
|---|---|
| `01_Threat_Intelligence.md` | CVE details, no-patch status, TTPs, compensating control recommendations |
| `02_Risk_Assessment.md` | Risk scoring with permanent-unpatched-state analysis; formal risk acceptance requirement |
| `03_BIA.md` | Segment isolation failure scenarios; OT/financial impact; regulatory compliance risk |
| `04_Control_Mapping.md` | Framework mapping; compensating control design (no patch available) |
| `05_Executive_Summary.md` | Board/CISO brief; no-patch status; risk acceptance decision request |
| `06_POAM_Remediation.md` | 7-milestone compensating control and risk acceptance plan |

---

## Risk Register Entry

**Risk ID:** RR-014 | Likelihood: 4 | Impact: 4 | Score: 16 | Rating: High

---

## Key Frameworks Applied

- NIST CSF 2.0 (PR.IR-01, DE.CM-01, GV.RM-06)
- NIST SP 800-53 Rev 5 (SC-7, AC-4, SI-4, RA-3)
- ISO 27001:2022 (A.8.22, A.8.16, A.8.9)
- CIS Controls v8 (Control 12, Control 13)
- IEC 62443 (Zone/Conduit model — OT environments)

## GRC Skills Demonstrated

- Permanent unpatched vulnerability risk treatment design
- Compensating control architecture for no-fix scenarios
- Formal risk acceptance documentation process
- IEC 62443 OT zone model application
- Network security architecture gap analysis

---

*GRC Intelligence Program v2.1 | Case built: 2026-06-15 | Run: Weekly Monday sweep*

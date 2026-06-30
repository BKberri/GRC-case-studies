# Risk Assessment
## Case: CVE-2026-20245 — Cisco Catalyst SD-WAN Manager Command Injection (root)
**Date:** 2026-06-15 | **Analyst:** Blaise Kingko | **Classification:** High

---

| Field | Value |
|---|---|
| **Risk ID** | RR-016 |
| **CVE ID** | CVE-2026-20245 |
| **CVSS** | 7.8 High |
| **Threat Category** | IT-OT-Threats — Network Management Infrastructure Command Injection |
| **Affected Asset** | Cisco Catalyst SD-WAN Manager (vManage) |
| **Attack Prerequisite** | Local authenticated access to SD-WAN Manager |

---

## Risk Scoring

| Metric | Rating | Rationale |
|---|---|---|
| **Likelihood** | 4 / 5 | Actively exploited in wild; authentication requirement is a partial barrier but insider threats, credential compromise, and shared admin accounts in real environments reduce this barrier significantly |
| **Impact** | 5 / 5 | Root on SD-WAN Manager = control of entire WAN fabric. Attacker can redirect traffic, exfiltrate configurations, deploy malicious policies to all edge routers, or deny WAN connectivity across the enterprise |
| **Risk Score** | 20 | |
| **Risk Rating** | **Critical** | Score 20 per this program's rating scale |

---

## Existing Controls

| Control | Status | Effectiveness |
|---|---|---|
| SD-WAN Manager patching | Requires Cisco security patch deployment | Low until patched |
| Role-based access control (RBAC) on vManage | Typically in place | Moderate — reduces user count but any authenticated user can exploit |
| Network-level restriction of vManage access | Variable — should be management segment only | High if implemented |
| MFA on SD-WAN Manager admin accounts | Variable by org | High if implemented |
| Audit logging on vManage | Typically enabled | Moderate — detective only |

---

## Treatment
TREAT — Patch immediately. Harden access controls on SD-WAN Manager (MFA, PAW, management segment restriction) as complementary controls.

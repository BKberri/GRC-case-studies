# Risk Assessment
## Case: CVE-2026-7473 — Arista EOS Tunnel Traffic Bypass (No Patch Planned)
**Date:** 2026-06-15 | **Analyst:** Blaise Kingko | **Classification:** High

---

| Field | Value |
|---|---|
| **Risk ID** | RR-014 |
| **CVE ID** | CVE-2026-7473 |
| **CVSS** | 6.9 Medium (actively exploited; KEV listing elevates practical risk) |
| **Threat Category** | IT-OT-Threats — Network Infrastructure Policy Bypass |
| **Affected Asset** | Arista EOS network devices (switches, routers) with tunnel configurations |
| **Special Risk Factor** | NO VENDOR PATCH PLANNED — permanent unpatched state; compensating controls are the only remediation path |

---

## Risk Scoring

| Metric | Rating | Rationale |
|---|---|---|
| **Likelihood** | 4 / 5 | Actively exploited in wild (CISA KEV); no patch available means exposure is permanent unless redesign occurs |
| **Impact** | 4 / 5 | Network boundary bypass enabling lateral movement between isolated segments; if deployed in financial services or OT environments, integrity of zone separation is compromised |
| **Risk Score** | 16 | |
| **Risk Rating** | **High** | |
| **Inherent Risk** | High |  |

---

## Permanent Risk Consideration

Unlike most KEV entries where "patch and close" is the remediation path, CVE-2026-7473 requires a long-term risk acceptance or network redesign decision. Organizations must either:
1. Accept residual risk with compensating controls documented and reviewed periodically
2. Redesign network architecture to remove reliance on Arista EOS tunnel policy enforcement as a security control
3. Replace affected EOS versions with platforms that provide patched tunnel enforcement

This is a permanent open risk until one of the above is implemented.

---

## Recommended Treatment
TREAT + ACCEPT (residual): Implement all compensating controls immediately. Document formal risk acceptance for residual unmitigatable risk with CISO/CRO sign-off. Reassess annually or upon any change in exploitation activity.

# Plan of Action & Milestones (POA&M)
## Case: CVE-2026-7473 — Arista EOS Tunnel Traffic Bypass
**Date:** 2026-06-15 | **Analyst:** Blaise Kingko | **Risk Rating:** High | **Patch Available:** NO

---

| Field | Value |
|---|---|
| **Weakness** | CVE-2026-7473 — Arista EOS tunnel endpoint comparison flaw enabling policy bypass |
| **Vendor Patch** | NONE — Arista has confirmed no patch will be developed |
| **Treatment Path** | Compensating controls + formal risk acceptance |
| **CISA KEV Due Date** | June 30, 2026 (BOD 26-04) |

---

## Milestones

| Milestone | Action | Owner | Due Date | Status |
|---|---|---|---|---|
| **M1 — Device Audit** | Inventory all Arista EOS devices with tunnel configurations (GRE, VXLAN, IPsec). Document: device name, OS version, tunnel type, tunnel endpoints, segments separated by tunnel policy. | Network Engineering | 2026-06-18 | Immediate |
| **M2 — Interface ACL Deployment** | For each affected Arista device: implement `ip access-list` rules denying unexpected tunnel source IPs at all ingress/egress interfaces associated with tunnel configurations. Test in lab before production deployment. | Network Engineering | 2026-06-22 | Pending |
| **M3 — NetFlow / sFlow Enablement** | Enable NetFlow/sFlow on all Arista EOS devices identified in M1. Send telemetry to SIEM. Create detection rule: alert on tunnel traffic from any source IP not in the documented expected tunnel endpoint list. | Network Security / SOC | 2026-06-22 | Pending |
| **M4 — Critical Boundary Assessment** | Assess all network boundaries protected by Arista tunnel policy. Classify each as: (a) compensating controls sufficient, or (b) requires additional inline firewall for defense-in-depth. | Network Architecture / Cloud Security | 2026-06-25 | Pending |
| **M5 — Inline Firewall Deployment (Priority Boundaries)** | For boundaries classified as (b) in M4: plan and deploy inline stateful firewall (Palo Alto/Fortinet) at conduit. This is a project-level initiative; initial design and budget required. | Network Architecture | 2026-08-15 | Planned |
| **M6 — Formal Risk Acceptance** | Document residual risk after M2/M3 compensating controls. Prepare risk acceptance memorandum for CISO and CRO signature. Include: CVE description, exploitation status, compensating controls implemented, residual risk rating, annual review schedule. | GRC / Risk Management | 2026-06-30 | Pending |
| **M7 — Annual Review** | Annual review of risk acceptance documentation, compensating control effectiveness, and Arista vendor roadmap for any new guidance on CVE-2026-7473. | GRC / Network Engineering | 2027-06-15 | Scheduled |

---

## Success Metrics

| Metric | Target |
|---|---|
| Arista device audit complete | 100% inventory by June 18 |
| Interface ACLs deployed | 100% of affected devices by June 22 |
| NetFlow alerts configured in SIEM | 100% of affected devices by June 22 |
| Formal risk acceptance signed | By June 30 (CISA BOD 26-04 deadline) |

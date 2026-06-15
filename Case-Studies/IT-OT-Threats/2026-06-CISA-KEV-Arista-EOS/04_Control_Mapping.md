# Control Mapping Matrix
## Case: CVE-2026-7473 — Arista EOS Tunnel Traffic Bypass
**Date:** 2026-06-15 | **Analyst:** Blaise Kingko

---

| Control Domain | NIST CSF 2.0 | NIST 800-53 Rev 5 | ISO 27001:2022 | CIS Controls v8 | Status |
|---|---|---|---|---|---|
| **Network Boundary Protection** | PR.IR-01 | SC-7 (Boundary Protection), AC-4 (Information Flow Enforcement) | A.8.22 (Segregation of Networks) | Control 12.2 | IMPAIRED by CVE — compensating controls required |
| **Traffic Monitoring / Detection** | DE.CM-01, DE.CM-03 | SI-4 (System Monitoring), AU-12 | A.8.16 (Monitoring Activities) | Control 13.6 (Network Traffic Monitoring) | Deploy NetFlow/sFlow on all affected Arista devices; alert on unexpected tunnel endpoint traffic |
| **Configuration Hardening** | PR.PS-02 | CM-6, CM-7 | A.8.9 (Configuration Management) | Control 4.2 | Audit all tunnel configurations; add explicit interface ACLs to deny unexpected tunnel sources |
| **Risk Acceptance Documentation** | GV.RM-06 | RA-3 (Risk Assessment), RA-9 | A.6.1.1 (Information Security Roles) | N/A | Formal risk acceptance required — no patch available; document with CISO signature |
| **OT Zone Integrity (if applicable)** | PR.IR-01 | SC-7, PL-8 | A.8.22 | IEC 62443 SL-2 Conduit | OT environments: supplement EOS tunnel control with inline firewall at zone conduit |

---

## Compensating Control Design (No Patch Available)

Since no vendor patch exists, the following compensating controls constitute the complete risk treatment:

| Control | Implementation | Effectiveness |
|---|---|---|
| Interface-level ACLs on Arista EOS | `ip access-list` denying unexpected tunnel source IPs at ingress/egress interfaces | High — blocks specific attack vector even though tunnel policy is bypassed |
| NetFlow/sFlow telemetry with SIEM alerting | Enable on all EOS devices with tunnel config; baseline expected flows; alert on deviations | High (detective); SIEM correlation required |
| Inline firewall at critical segment boundaries | Deploy separate stateful firewall (Palo Alto, Fortinet) in addition to EOS tunnel policy | High (preventive); adds defense-in-depth layer independent of EOS flaw |
| Formal risk acceptance with periodic review | Document residual risk, approved controls, and review cycle in GRC tool | Compliance requirement — ensures accountability |
| Arista EOS upgrade roadmap | Evaluate whether EOS upgrade path addresses the underlying architectural issue in newer versions | Long-term — pursue vendor roadmap clarification |

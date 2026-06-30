# Business Impact Analysis (BIA)
## Case: CVE-2026-20245 — Cisco Catalyst SD-WAN Manager Command Injection (root)
**Date:** 2026-06-15 | **Analyst:** Blaise Kingko

---

## Summary

SD-WAN Manager is the single pane of glass for enterprise WAN policy. Root access to SD-WAN Manager gives an attacker control equivalent to owning the entire WAN fabric — they can see, modify, or disrupt all WAN traffic across every connected branch, data center, and cloud on-ramp.

---

## Business Impact Scenarios

### Scenario A — WAN Configuration Exfiltration
Attacker with root on SD-WAN Manager exports all device templates, routing policies, security policies, and stored credentials. **Impact:** Complete network topology disclosure; stored credentials for edge devices compromised; attacker can reconstruct full WAN architecture for future attacks.

### Scenario B — Malicious WAN Policy Deployment
Attacker uses root access to push malicious routing or security policy to all SD-WAN edge routers simultaneously. **Impact:** Possible traffic redirection (man-in-the-middle across WAN), blackholing of branch connectivity, or insertion of malicious traffic inspection rules. Enterprise-wide WAN disruption.

### Scenario C — WAN Availability Attack
Attacker uses root access to issue destabilizing configuration changes causing SD-WAN edge devices to lose controller connectivity or enter fail-open/fail-closed state. **Impact:** Branch office WAN outages; cloud on-ramp disruption; business continuity impact if branches rely on SD-WAN for primary connectivity.

---

## Financial Exposure

| Scenario | Low | High |
|---|---|---|
| Configuration / credential exfiltration | $500K | $5M |
| Traffic redirection / MitM | $1M | $15M |
| WAN availability disruption | $1M | $20M (branch productivity, SLA penalties) |

---

## Regulatory Note
WAN management system compromise may constitute a material cybersecurity incident under SEC disclosure rules. If traffic interception results in exposure of regulated data (financial transactions, PII), additional breach notification obligations apply.

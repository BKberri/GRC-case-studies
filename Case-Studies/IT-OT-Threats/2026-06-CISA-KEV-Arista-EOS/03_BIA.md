# Business Impact Analysis (BIA)
## Case: CVE-2026-7473 — Arista EOS Tunnel Traffic Bypass
**Date:** 2026-06-15 | **Analyst:** Blaise Kingko

---

## Summary

The business impact of CVE-2026-7473 depends heavily on how Arista EOS tunnel configurations are used as security boundaries in the organization's network architecture. In environments where tunnel policy enforcement is a primary control for segment isolation — particularly financial services trading networks, OT/ICS zone separation, or government classified/unclassified boundary enforcement — the business impact is severe. In environments where tunnel policy is a management convenience rather than a security boundary, impact is lower.

---

## Affected Business Processes

| Business Process | Arista Tunnel Use | Impact of Bypass |
|---|---|---|
| Data center segment isolation | VXLAN/GRE between compute zones | Cross-segment lateral movement risk; compliance boundary failure |
| OT/IT network separation | Tunnel between OT DMZ and IT network | OT zone boundary integrity failure; IEC 62443 zone model undermined |
| Financial trading network isolation | Tunnel between trading systems and corporate | Potential data exfiltration across what was believed to be an isolated path |
| Cloud on-ramp / WAN connectivity | IPsec/GRE tunnels to cloud | Unintended traffic injection into cloud-bound traffic flows |

---

## Financial Exposure Estimate

| Scenario | Low | High |
|---|---|---|
| Data exfiltration via tunnel bypass | $1M | $10M |
| OT disruption via lateral movement through zone boundary | $500K | $50M (OT downtime, physical consequences) |
| Compliance violation (network isolation requirement failed) | $500K | $5M (regulatory fines, audit findings) |
| Network redesign cost (remediation without patch) | $200K | $2M |

---

## Regulatory Compliance Impact

| Requirement | Risk |
|---|---|
| **IEC 62443 Zone/Conduit model** | Zone boundary failure if EOS tunnel is a conduit control; SL requirement may be unmet |
| **NIST 800-82 (ICS Security)** | Defense-in-depth architecture undermined |
| **PCI-DSS v4.0 Req 1.2** | Network security controls — tunnel bypass may violate cardholder data environment isolation |
| **HIPAA Security Rule (§164.312(e)(1))** | Transmission security — if PHI flows through affected tunnels |

---

## Business Continuity Note

No immediate availability impact. The vulnerability is a traffic policy bypass, not a denial-of-service. Business continuity impact arises from the secondary effects of exploitation (breach, lateral movement, OT disruption) rather than direct service disruption from the CVE itself.

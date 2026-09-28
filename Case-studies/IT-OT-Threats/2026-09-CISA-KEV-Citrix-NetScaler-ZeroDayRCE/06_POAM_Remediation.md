# Citrix NetScaler ADC/Gateway Zero-Day RCE Chain — Plan of Action & Milestones (POA&M)

| Field | Details |
|---|---|
| **Case Study ID** | CS-ITOT-2026-09-001 |
| **Risk Register Cross-Reference** | RR-079 |
| **Report Period** | 2026-09-21 to 2026-09-28 |
| **Date** | 2026-09-28 |
| **Author** | Blaise Kingko |
| **CISA KEV Remediation Due Date** | 2026-09-30 |

This POA&M reformats this program's standard immediate / short-term / strategic remediation structure into a formal Plan of Action & Milestones. Target dates are anchored to the disclosure date (2026-09-27) and the CISA KEV due date (2026-09-30). Owners are expressed as functional roles; organizations should map these to named individuals internally.

---

## Plan of Action & Milestones

| POA&M ID | Weakness | Framework Ref | Remediation Action | Resources Required | Milestone / Target Date | Status | Owner |
|---|---|---|---|---|---|---|---|
| **POAM-2026-09-001-01** | Unknown/unconfirmed NetScaler ADC/Gateway asset inventory and version exposure | NIST CSF ID.AM-01; NIST 800-53 CM-8; ISO 27001 A.8.8; CIS 7.1 | Inventory all NetScaler ADC/Gateway instances (physical, virtual, cloud) and confirm exact firmware build against fixed versions (14.1-73.37 / 13.1-64.23 / FIPS-NDcPP equivalents) | Asset management/CMDB access; network scanning tooling; 2–4 FTE-hours per environment | 2026-09-28 (T+1 day) | Open | Vulnerability Management |
| **POAM-2026-09-002-02** | Unknown compromise status prior to patching (forensic evidence loss risk) | NIST CSF DE.CM-09, RS.AN-03; NIST 800-53 IR-4; ISO 27001 A.8.16 | Review NetScaler Console logs and known IoCs per Citrix guidance (CTX694799) on every in-scope appliance **before** applying firmware update | SOC/IR analyst time; NetScaler Console/log access; Citrix IoC reference material | 2026-09-29 (T+2 days), prior to patch execution | Open | SOC / Incident Response |
| **POAM-2026-09-003-03** | Unauthenticated RCE exposure via improper input validation (CVE-2026-88771, CVE-2026-88772) | NIST CSF PR.PS-02; NIST 800-53 SI-2; ISO 27001 A.8.8; CIS 7.5 | Apply Citrix firmware update to 14.1-73.37 / 13.1-64.23 (or later) across all in-scope appliances, addressing the full CTX697096 bulletin (all 8 CVEs), not the 2 KEV entries alone | Emergency change window; appliance downtime allowance; patching/engineering staff; rollback plan | 2026-09-30 (T+3 days) — CISA KEV due date | Open | Perimeter Security Engineering |
| **POAM-2026-09-004-04** | No post-patch verification of appliance integrity | NIST CSF PR.PS-04; NIST 800-53 CM-6; ISO 27001 A.8.16 | Validate post-patch configuration against last known-good baseline; confirm no unauthorized configuration changes, accounts, or persistence mechanisms were introduced during the exposure window | Configuration backups; SOC review time | 2026-10-01 (T+4 days) | Open | Perimeter Security Engineering / SOC |
| **POAM-2026-09-005-05** | Management/gateway interface exposure not minimized | NIST CSF PR.AA-05; NIST 800-53 SC-7; ISO 27001 A.8.20; CIS 4.1, 12.6 | Restrict NetScaler management-plane reachability to trusted management networks; review and tighten firewall/ACL rules for the affected interfaces | Network engineering time; firewall change window | 2026-10-05 (T+8 days) | Open | Network Security Engineering |
| **POAM-2026-09-006-06** | Vulnerability scanning may not distinguish affected sub-versions | NIST CSF ID.RA-01; NIST 800-53 RA-5; CIS 7.6 | Update vulnerability scanner signatures/plugins to accurately detect NetScaler ADC/Gateway builds affected by CVE-2026-88771–88778; re-scan full estate to confirm zero remaining exposure | Scanning tool license/update; scan window | 2026-10-08 (T+11 days) | Open | Vulnerability Management |
| **POAM-2026-09-007-07** | No documented emergency-change procedure specific to perimeter appliances | NIST CSF GV.RM-04; NIST 800-53 CP-2; ISO 27001 A.5.37 | Draft and socialize a pre-approved emergency-change runbook for perimeter VPN/ADC appliances, including the IoC-review-before-patch sequencing as a mandatory step | Policy/procedure owner time; change advisory board review | 2026-10-20 (T+23 days) | Open | GRC / Change Management |
| **POAM-2026-09-008-08** | No standing incident-response playbook for perimeter-appliance compromise scenarios | NIST CSF RS.MA-01; NIST 800-53 IR-4; ISO 27001 A.5.24; CIS 17.4 | Develop/update IR playbook specific to NetScaler and comparable perimeter-appliance compromise, incorporating vendor-published IoC guidance as a standard first step | IR team time; tabletop exercise scheduling | 2026-11-15 (T+49 days) | Open | Incident Response / SOC |
| **POAM-2026-09-009-09** | Single point of failure — no redundancy/failover for remote-access function | NIST CSF RC.RP-01; NIST 800-53 CP-2; CIS 12.1 | Assess feasibility of HA/clustered NetScaler deployment or alternate failover remote-access path to reduce availability risk during future emergency patch cycles | Architecture review; potential capital budget for HA licensing/hardware | 2026-12-15 (T+79 days) | Open | Infrastructure Architecture |
| **POAM-2026-09-010-10** | Recurring perimeter-appliance exploitation pattern not addressed at program level | NIST CSF GV.RM-05; ISO 27001 A.5.24 | Present this incident alongside 2026's broader perimeter-appliance KEV pattern (Ivanti, SonicWall, Progress, Check Point) to risk leadership; propose standing risk-register treatment for "internet-facing remote-access appliance" as an asset category | Risk committee time; this case study and related cases as supporting evidence | 2026-10-31 (T+34 days) | Open | CISO / Risk Committee |
| **POAM-2026-09-011-11** *(conditional)* | Undetermined whether any NetScaler instance brokers access into an OT-adjacent environment | NIST CSF ID.AM-03; IEC 62443-3-3 SR 1.13 / SR 2.6 (where applicable) | Confirm whether any in-scope NetScaler instance mediates remote access into an OT/ICS environment; if so, apply this POA&M with elevated priority and coordinate with OT security team | OT asset inventory cross-check; OT security team engagement | 2026-10-05 (T+8 days) | Open — pending scope confirmation | OT Security / IT Security (joint) |

---

## Status Legend

| Status | Meaning |
|---|---|
| **Open** | Not yet started or in progress; no milestone completed |
| **In Progress** | Remediation actively underway |
| **Completed** | Milestone met and verified |
| **Overdue** | Target date passed without completion — requires escalation |
| **Risk Accepted** | Remediation deferred with documented, leadership-approved risk acceptance |

*All items in this POA&M are logged as Open as of the report date (2026-09-28), reflecting the incident's freshness relative to the CISA KEV remediation due date (2026-09-30). This table should be updated in place as milestones are completed, with dated status changes tracked in the case study's revision history.*

---

## References

| Source | URL |
|---|---|
| CISA Alert (2026-09-27) | https://www.cisa.gov/news-events/alerts/2026/09/27/critical-zero-day-vulnerabilities-exploited-citrix-netscaler-adc-gateway |
| CISA KEV Catalog | https://www.cisa.gov/known-exploited-vulnerabilities-catalog |
| Citrix Security Bulletin CTX697096 | https://support.citrix.com/support-home/kbsearch/article?articleNumber=CTX697096 |
| Citrix, "Steps to Take if NetScaler ADC is Suspected to be Compromised" (CTX694799) | https://support.citrix.com/external/article/CTX694799/steps-to-take-if-netscaler-adc-is-suspec.html |

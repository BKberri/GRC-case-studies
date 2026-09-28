# Plan of Action & Milestones — F5 BIG-IP APM OAuth Authorization Server RCE (CVE-2026-94127)

**Case Study ID:** CS-CLOUD-2026-09-002 | **Risk Register Entry:** RR-082 | **Date:** 2026-09-28
**CISA KEV Due Date:** 2026-09-25 (elapsed as of this report's publication)

This POA&M reformats the recommended controls and remediation actions into a formal tracking structure. Target dates are set relative to the CISA KEV disclosure date (2026-09-22) and this report's publication date (2026-09-28); an organization applying this POA&M should recalculate target dates from its own confirmed discovery date where that differs.

---

## Immediate Actions (0–7 Days from Disclosure)

| POAM ID | Weakness | Framework Ref | Remediation Action | Resources Required | Milestone / Target Date | Status | Owner |
|---|---|---|---|---|---|---|---|
| POAM-2026-09-002-01 | BIG-IP APM instances of unconfirmed OAuth Authorization Server status create ambiguous remediation scope | CSF ID.AM-02, NIST 800-53 CM-6 | Inventory all BIG-IP APM instances across the estate; confirm which have an OAuth Authorization Server profile configured and attached to a virtual server | Cloud/network engineering time; access to BIG-IP configuration management console or config export | 2026-09-24 | Overdue — In Progress | Network Security Engineering |
| POAM-2026-09-002-02 | Confirmed in-scope BIG-IP APM instances running vulnerable firmware (pre-hotfix builds) | NIST 800-53 SI-2, ISO 27001 A.8.8, CIS Control 7 | Apply F5 hotfix builds (Hotfix-BIGIP-21.1.0.2.0.30.22-ENG, Hotfix-BIGIP-17.5.1.9.0.160.12-ENG, or Hotfix-BIGIP-17.1.3.5.0.41.14-ENG as applicable) to all confirmed in-scope instances, internet-facing instances first | Change-management emergency approval; maintenance window; F5 support entitlement for hotfix download | 2026-09-25 | Overdue — In Progress | Cloud Security Engineering |
| POAM-2026-09-002-03 | Internet-facing or broadly internally-reachable virtual servers with OAuth Authorization Server profiles and no interim compensating control while awaiting patch | NIST 800-53 SC-7, CSA CCM IVS-09 | Restrict network reachability of affected virtual servers via IP allow-listing or WAF-layer filtering as an interim measure anywhere the hotfix cannot be applied within 24 hours | Network/firewall change access; WAF rule authoring capability | 2026-09-24 | Overdue — In Progress | Network Security Engineering |
| POAM-2026-09-002-04 | OAuth tokens and sessions issued during the exposure window (2026-09-22 through confirmed patch timestamp) of unverified trust status | NIST 800-53 IA-5, CSF RC.RP-01 | Force invalidation and rotation of OAuth tokens/sessions issued by confirmed in-scope instances during the exposure window; notify relying-party application owners | IAM/identity team coordination; relying-party application inventory | 2026-09-26 | In Progress | IAM Engineering |

## Short-Term Actions (8–30 Days)

| POAM ID | Weakness | Framework Ref | Remediation Action | Resources Required | Milestone / Target Date | Status | Owner |
|---|---|---|---|---|---|---|---|
| POAM-2026-09-002-05 | Absence of documented OAuth scope governance for Authorization Server profiles | CSF PR.AA-05, ISO 27001 A.8.5 | Review OAuth scopes issued by each confirmed Authorization Server profile for least-privilege alignment; remediate overly broad grants | IAM policy review time; relying-party application coordination | 2026-10-12 | Planned | IAM Engineering |
| POAM-2026-09-002-06 | Self-managed appliance firmware not covered by existing vulnerability scanning tooling | NIST 800-53 RA-5, CIS Control 7 | Extend vulnerability management process and scanning coverage to explicitly include BIG-IP and equivalent network appliance firmware, with defined SLA for KEV-catalog entries | Vulnerability management platform configuration; process documentation update | 2026-10-15 | Planned | GRC / Vulnerability Management |
| POAM-2026-09-002-07 | No documented emergency change process for KEV-driven appliance patching | CSF PR.PS-01, GV.RM-04 | Formalize an emergency change process specific to CISA KEV-catalog additions, with SLA targets faster than the standard patch cycle | Change management process owner; CAB approval | 2026-10-20 | Planned | GRC / Risk Management |
| POAM-2026-09-002-08 | Detection tooling does not distinguish anomalous OAuth request patterns or unexpected process behavior on APM instances from routine traffic | CSF DE.CM-01 | Implement detection logic/alerting for anomalous OAuth request volume, malformed request patterns, and unexpected process behavior on BIG-IP APM instances | SIEM/detection engineering time; BIG-IP logging integration | 2026-10-22 | Planned | Security Operations |

## Strategic Recommendations (31–90 Days)

| POAM ID | Weakness | Framework Ref | Remediation Action | Resources Required | Milestone / Target Date | Status | Owner |
|---|---|---|---|---|---|---|---|
| POAM-2026-09-002-09 | No architectural standard for network segmentation around identity-aware proxy infrastructure | NIST 800-53 SC-7, CSA CCM IVS-09 | Define and implement a segmentation standard isolating identity-aware proxy/access-gateway infrastructure (BIG-IP APM and equivalents) from general application network segments, limiting lateral-movement blast radius for future findings in this device class | Network architecture review; segmentation project resourcing | 2026-11-30 | Planned | Network Architecture |
| POAM-2026-09-002-10 | No standing cross-functional owner for identity-aware access proxy infrastructure risk | CSF GV.RM-04 | Establish a named, accountable owner (or working group) for BIG-IP APM and equivalent access-proxy infrastructure risk, covering patch currency, configuration governance, and KEV monitoring on an ongoing basis rather than per-incident | Executive sponsorship; role/responsibility documentation | 2026-12-15 | Planned | CISO Office |
| POAM-2026-09-002-11 | CIS Benchmark and CSPM coverage gap for self-managed appliance software deployed via cloud marketplace images | AWS Well-Architected SEC01/SEC05, CSA CCM | Evaluate and, where available, adopt vendor or third-party hardening benchmarks for BIG-IP marketplace deployments; document the gap formally where no benchmark exists, rather than assuming marketplace deployment implies equivalent hardening | Cloud security architecture review time | 2026-12-20 | Planned | Cloud Security Architecture |

---

## Status Legend

- **Overdue — In Progress:** Target date has passed; remediation is actively underway.
- **In Progress:** Actively being worked, target date not yet reached.
- **Planned:** Scoped and scheduled, work not yet started.
- **Not Started:** No resourcing or scheduling confirmed.
- **Closed:** Remediation verified complete.

*Owners listed reflect functional roles for portfolio and reference purposes; map to actual named owners and ticket/tracking IDs when applying this POA&M within a live GRC or vulnerability management system.*

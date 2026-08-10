# Plan of Action & Milestones (POA&M)
## 2026-08-CISA-KEV-Progress-LoadMaster-CommandInjection
**Date Opened:** 2026-08-10 | **Source:** CISA KEV | **Risk Rating:** Critical | **Target Closure:** 2026-08-13

## POA&M Table
| Item ID | Weakness / Finding | Affected System | Control Reference | Responsible Role | Planned Action | Milestone 1 | Milestone 2 | Milestone 3 | Target Date | Status |
|---|---|---|---|---|---|---|---|---|---|---|
| POA-202608-016 | Pre-auth root command injection (CVE-2026-8037) | Progress Kemp LoadMaster appliance(s) | NIST 800-53 SI-10, SI-2 | Network Engineering Lead | Upgrade to LoadMaster GA 7.2.63.2 or LTSF 7.2.54.18 | 2026-08-11: Confirm current firmware version on all appliances | 2026-08-12: Apply upgrade in maintenance window with HA failover | 2026-08-12: Validate appliance and application traffic post-upgrade | 2026-08-12 | Open |
| POA-202608-017 | Extended active-exploitation window since 2026-06-29 predating this KEV addition | Progress Kemp LoadMaster appliance(s) | NIST 800-53 AU-6, IR-4 | Security Operations | Review appliance logs back to 2026-06-29 for exploitation indicators | 2026-08-11: Pull logs for full exposure window | 2026-08-13: Complete log analysis for /accessv2 anomalies | 2026-08-13: Escalate to IR if compromise indicators found | 2026-08-13 | Open |
| POA-202608-018 | Management API reachable from untrusted networks | Progress Kemp LoadMaster appliance(s) | NIST 800-53 AC-4, CIS 12.2 | Network Engineering | Restrict management/API interface to defined administrative network segment | 2026-08-12: Define access-restriction policy | 2026-08-13: Implement firewall/ACL changes | 2026-08-13: Verify no unintended external access remains | 2026-08-13 | Open |

## Remediation Narrative
Upgrade all Progress Kemp LoadMaster appliances to GA 7.2.63.2 or LTSF 7.2.54.18, whichever branch applies, coordinating the maintenance window with any high-availability failover pair to avoid production traffic disruption. There is no supported workaround for the underlying code defect; network-level access restriction to the `/accessv2` endpoint is a compensating control, not a substitute for patching. Following the upgrade, review appliance logs back to 2026-06-29 (the earliest confirmed exploitation date) for any indicators of successful command injection prior to remediation.

## Compensating Controls
Until patched, restrict access to the `/accessv2` endpoint and the broader management interface to a defined internal administrative network segment via firewall/ACL rules, removing direct internet reachability. Enable enhanced logging on the appliance for the affected endpoint if not already active.

## Verification & Closure Criteria
Closure requires: (1) confirmed LoadMaster firmware version at or above the fixed release; (2) documented completion of the log review covering the full exposure window with no unresolved indicators of compromise, or an escalated incident record if compromise is confirmed; (3) confirmed removal of unrestricted internet access to the management interface, verified via external scan. Evidence artifacts should be retained in the case file for audit purposes.

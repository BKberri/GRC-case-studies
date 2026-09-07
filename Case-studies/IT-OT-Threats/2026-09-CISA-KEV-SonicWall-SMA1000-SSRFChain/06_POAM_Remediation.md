# Plan of Action & Milestones (POA&M)
## 2026-09-CISA-KEV-SonicWall-SMA1000-SSRFChain
**Date Opened:** 2026-09-07 | **Source:** CISA KEV | **Risk Rating:** Critical | **Target Closure:** 2026-09-09

## POA&M Table
| Item ID | Weakness / Finding | Affected System | Control Reference | Responsible Role | Planned Action | Milestone 1 | Milestone 2 | Milestone 3 | Target Date | Status |
|---|---|---|---|---|---|---|---|---|---|---|
| POA-202609-007 | Chained pre-auth SSRF + OS command injection (CVE-2026-83548, CVE-2026-83549) | SonicWall SMA1000 appliance(s) | NIST 800-53 SC-7, AC-4, SI-10 | Network Engineering Lead | Upgrade to firmware 12.4.3 build 03526+ or 12.5.0 build 02952+ | 2026-09-08: Confirm current firmware build on all appliances | 2026-09-08: Apply upgrade (accelerated, ahead of 09-05 federal deadline which has already passed by publication) | 2026-09-09: Validate appliance and remote-access session integrity post-upgrade | 2026-09-09 | Open — Overdue Risk (federal due date 2026-09-05 predates this report) |
| POA-202609-008 | Confirmed active exploitation prior to patch availability | SonicWall SMA1000 appliance(s) | NIST 800-53 AU-6, IR-4 | Security Operations | Engage SonicWall support; review logs for compromise indicators | 2026-09-08: Open vendor support case | 2026-09-10: Complete log/forensic review | 2026-09-10: Escalate to IR if compromise indicators found | 2026-09-10 | Open |
| POA-202609-009 | Administrative console reachable via unauthenticated request path | SonicWall SMA1000 appliance(s) | NIST 800-53 SC-7, AC-4 | Network Engineering | Verify network segmentation between Work Place and AMC interfaces beyond the vendor patch | 2026-09-11: Review network architecture for administrative-plane isolation | 2026-09-11: Implement additional segmentation if gaps found | N/A | 2026-09-11 | Open |

## Remediation Narrative
Upgrade all SonicWall SMA1000 appliances to the fixed firmware builds without delay — note that CISA's own remediation deadline (2026-09-05) falls before this report's publication date, meaning any unpatched appliance is already past the federal due date and should be treated as a top-priority overdue item, not a routine patch task. Given confirmed active exploitation, engage vendor support for a compromise assessment on any appliance that was running vulnerable firmware at any point during the exploitation window, in parallel with — not sequenced after — the firmware upgrade.

## Compensating Controls
Where immediate patching is not yet complete, restrict access to the appliance's Work Place and AMC interfaces to the minimum necessary source networks via upstream firewall rules, and increase monitoring for anomalous authentication or configuration-change events on the appliance.

## Verification & Closure Criteria
Closure requires: (1) confirmed firmware upgrade to a fixed build on every SMA1000 appliance; (2) a vendor-supported or internal compromise assessment covering the full exploitation window with no unresolved indicators, or an escalated incident record if compromise is confirmed; (3) documented verification that the administrative console is not reachable via any unauthenticated request path, independent of the firmware fix; (4) if applicable, confirmation of remediation status for the organization's exposure (if any) to the July 2026 SonicWall configuration-backup incident.

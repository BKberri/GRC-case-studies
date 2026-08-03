# Plan of Action & Milestones (POA&M)
## 2026-08-CISA-KEV-Arista-VeloCloud-CommandInjection
**Date Opened:** 2026-08-03 | **Source:** CISA KEV | **Risk Rating:** Critical | **Target Closure:** 2026-08-10

## POA&M Table
| Item ID | Weakness / Finding | Affected System | Control Reference | Responsible Role | Planned Action | Milestone 1 | Milestone 2 | Milestone 3 | Target Date | Status |
|---|---|---|---|---|---|---|---|---|---|---|
| POA-202608-001 | Unauthenticated OS command injection (CVE-2026-16812) in VeloCloud Orchestrator | VeloCloud Orchestrator (on-prem) | NIST 800-53 SI-2, SI-10 | Network Engineering Lead | Upgrade VCO to 5.2.3.14 / 6.1.3.4 / 6.4.2.4 / 7.0.0.1+ per current branch | 2026-08-04: Confirm current VCO version and target upgrade path | 2026-08-05: Apply patch in maintenance window | 2026-08-06: Validate orchestrator functionality post-patch | 2026-08-06 | Open |
| POA-202608-002 | Orchestrator management interface reachable from the open internet | VeloCloud Orchestrator (on-prem) | NIST 800-53 SC-7, CIS 12.2 | Security Architecture | Restrict management interface to admin VPN / allow-listed source ranges | 2026-08-04: Define allow-list and access model | 2026-08-06: Implement firewall/ACL changes | 2026-08-07: Verify no unintended access paths remain | 2026-08-07 | Open |
| POA-202608-003 | Unknown pre-patch exposure window — potential unauthorized access | VeloCloud Orchestrator (on-prem) | NIST 800-53 AU-6, IR-4 | Security Operations | Review orchestrator and edge-device logs for indicators of compromise predating patch | 2026-08-04: Pull orchestrator access/command logs for prior 30 days | 2026-08-06: Complete log analysis and IOC sweep | 2026-08-08: Document findings, escalate if compromise confirmed | 2026-08-08 | Open |

## Remediation Narrative
Upgrade all VeloCloud Orchestrator instances to the fixed release for their branch: 5.2.3.14 for the 5.2.x line, 6.1.3.4 for the 6.1.x line, 6.4.2.4 for the 6.4.x line, or migrate to 7.0.0.1 or later, which is unaffected. Apply the patch through Arista's standard software distribution channel and validate orchestrator-to-edge connectivity after the upgrade. In parallel, reconfigure network ACLs/firewall rules so the Orchestrator's web management interface is reachable only from a defined administrative network or VPN — do not rely on the vendor patch alone as the sole control, since internet-facing management planes remain a standing risk for future vulnerabilities in this product class. There is no supported workaround short of patching; do not attempt to mitigate via WAF or reverse-proxy filtering alone, as Arista has not validated that approach against this specific injection vector.

## Compensating Controls
Until patched, restrict inbound access to the Orchestrator's management port to known administrative source IPs at the perimeter firewall, and enable enhanced logging/alerting on the orchestrator for command-execution and configuration-push events. If immediate patching is not feasible, consider taking the orchestrator's public-facing interface offline and managing edges through an alternate secure channel until the patch window opens.

## Verification & Closure Criteria
Closure requires: (1) confirmed VCO version at or above the fixed release across all instances, verified via `show version` or the orchestrator admin console; (2) confirmed removal of unrestricted internet exposure to the management interface, verified via external port scan; (3) documented completion of the log review with no unresolved indicators of compromise, or an escalated incident record if compromise is confirmed. Evidence artifacts (version confirmation, firewall rule change record, log review summary) should be retained in the case file for audit purposes.

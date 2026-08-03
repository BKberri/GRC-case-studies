# Plan of Action & Milestones (POA&M)
## 2026-08-CISA-KEV-Cisco-FMC-HardcodedPassword
**Date Opened:** 2026-08-03 | **Source:** CISA KEV | **Risk Rating:** High | **Target Closure:** 2026-08-08

## POA&M Table
| Item ID | Weakness / Finding | Affected System | Control Reference | Responsible Role | Planned Action | Milestone 1 | Milestone 2 | Milestone 3 | Target Date | Status |
|---|---|---|---|---|---|---|---|---|---|---|
| POA-202608-004 | Hard-coded credential (CVE-2026-20316) in Cisco Secure FMC | Cisco Secure Firewall Management Center | NIST 800-53 IA-5, CM-6 | Network Security Lead | Upgrade FMC to 7.0.9+ / 7.2.11+ / 7.4.6+ per current branch; apply Cisco hot fix if immediate upgrade not feasible | 2026-08-04: Identify FMC version and applicable upgrade path | 2026-08-05: Apply patch/hot fix in maintenance window | 2026-08-06: Validate FMC functionality and managed-device connectivity post-patch | 2026-08-06 | Open |
| POA-202608-005 | Potential credential exposure prior to patch | Cisco Secure Firewall Management Center | NIST 800-53 IA-5, AC-2 | IT Operations | Rotate all credentials, certificates, and keys managed by the affected FMC instance | 2026-08-05: Inventory all credentials/certs managed by FMC | 2026-08-07: Complete rotation | 2026-08-07: Confirm no residual use of old credentials | 2026-08-07 | Open |
| POA-202608-006 | Unknown pre-patch access — potential unauthorized policy visibility or tampering | Cisco Secure Firewall Management Center | NIST 800-53 AU-6, CM-3 | Security Operations | Audit firewall policy change history for unauthorized modifications | 2026-08-05: Pull change logs for prior 30 days | 2026-08-07: Complete policy integrity review | 2026-08-08: Document findings; escalate to IR if tampering found | 2026-08-08 | Open |

## Remediation Narrative
Upgrade Cisco Secure FMC to the fixed release for the current branch: 7.0.9 or later for the 6.4.0.13–6.4.0.18 and 7.0.x branches, 7.2.11 or later for the 7.1.x–7.2.x branch, and 7.4.6 or later for the 7.3.x–7.4.x branch. Cisco has also published branch-specific hot fixes through the Cisco Software Center for organizations that cannot complete a full version upgrade immediately. There is no supported workaround — Cisco explicitly states no configuration-based mitigation exists — so patching or hot-fixing is mandatory. Following the patch, rotate all credentials, TLS certificates, and API keys managed by or stored within the affected FMC instance, consistent with Cisco's guidance for any instance where compromise is suspected.

## Compensating Controls
Until patched, restrict FMC web-interface access to a defined administrative network segment and enable heightened logging/alerting on all authentication events to the platform, with particular attention to logins from accounts not present in the organization's own administrator roster.

## Verification & Closure Criteria
Closure requires: (1) confirmed FMC version at or above the fixed release, verified via the platform's About page or CLI version check; (2) documented completion of credential/certificate rotation; (3) completed firewall policy change-log review with no unresolved indicators of unauthorized modification, or an escalated incident record if tampering is confirmed. Evidence artifacts should be retained in the case file for audit purposes.

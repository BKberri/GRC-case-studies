# Plan of Action & Milestones (POA&M)
## Check Point SmartConsole Authentication Bypass (CVE-2026-16232)
**Date Opened:** 2026-07-27 | **Source:** CISA KEV | **Risk Rating:** Critical | **Target Closure:** 2026-08-08

## POA&M Table
| Item ID | Weakness / Finding | Affected System | Control Reference | Responsible Role | Planned Action | Milestone 1 | Milestone 2 | Milestone 3 | Target Date | Status |
|---|---|---|---|---|---|---|---|---|---|---|
| POA-202607-008 | Authentication bypass in SmartConsole login process | Check Point Security Management / MDSM, R77.30–R82.10 | IA-2, SC-7 | Security Architecture / Network Engineering | Apply July 22 Jumbo hotfix to all Management Servers | 2026-07-28: Inventory all Check Point Management Servers | 2026-07-31: Apply hotfix to all servers | 2026-08-04: Confirm patched version on all servers | 2026-08-04 | Open — Emergency |
| POA-202607-009 | Management Server reachable from internet without Trusted Client IP restriction | Check Point Management Server network configuration | SC-7, AC-6 | Network Engineering | Restrict Trusted Clients (GUI clients) to known administrative IP ranges; place behind VPN/firewall if not already | 2026-07-29: Audit current Trusted Client configuration | 2026-08-01: Apply IP restrictions | 2026-08-05: Verify restriction via external scan | 2026-08-05 | Open — Emergency |
| POA-202607-010 | Potential silent firewall policy tampering during exposure window | All gateways managed by affected Management Servers | CIS Control 12 | Security Operations | Compare current firewall policy and admin account list against last known-good baseline | 2026-08-01: Pull current policy/account state | 2026-08-05: Compare against baseline | 2026-08-08: Remediate any discrepancies found | 2026-08-08 | Open |
| POA-202607-011 | CVE-2026-62144 / CVE-2026-62145 patched preventively in same cycle | Check Point Security Management / MDSM, R77.30–R82.10 | IA-2, AC-6 | Security Architecture | Confirm same Jumbo hotfix (applied for CVE-2026-16232) also addresses these two CVEs | 2026-07-31: Confirm hotfix coverage | — | — | 2026-07-31 | Open |

## Remediation Narrative
Apply the Check Point July 22 Jumbo hotfix to every affected Security Management and Multi-Domain Security Management server (versions R77.30 through R82.10), which addresses CVE-2026-16232 along with the related CVE-2026-62144 and CVE-2026-62145 discovered in the same review. Independent of and in addition to patching, restrict Trusted Clients (the GUI client IP allowlist controlling who can reach SmartConsole) to known administrative IP ranges, and ensure the Management Server sits behind a VPN or dedicated firewall rather than being directly internet-reachable — this closes the exploitation prerequisite Check Point itself identified, providing defense-in-depth beyond the patch alone. Because full administrative compromise could include silent policy modification, pull the current live firewall policy and administrator account list from every managed Management Server and diff it against the most recent known-good configuration backup to rule out tampering during any period the exposure condition existed.

## Compensating Controls
Until Trusted Client restrictions and the hotfix are both confirmed in place, consider temporarily requiring in-person or break-glass VPN-only access for any SmartConsole administrative session.

## Verification & Closure Criteria
Closure requires: (1) confirmed hotfix applied to all in-scope Management Servers, (2) confirmed Trusted Client restriction verified via external network scan showing the Management Server is not reachable without the restriction, (3) completed firewall-policy and admin-account integrity comparison with no unresolved discrepancies, and (4) no indicators of compromise found in Check Point's published IOC list (151.241.99[.]207, 151.241.99[.]233, 158.62.198[.]182, 192.142.10[.]99, 139.28.37[.]250, 194.213.18[.]137) against management-plane access logs.

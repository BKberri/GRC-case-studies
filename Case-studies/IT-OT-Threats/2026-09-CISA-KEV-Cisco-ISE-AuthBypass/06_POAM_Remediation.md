# Plan of Action & Milestones (POA&M)
## 2026-09-CISA-KEV-Cisco-ISE-AuthBypass
**Date Opened:** 2026-09-21 | **Source:** Cisco PSIRT cisco-sa-ISE-ABP-VNSW7Tn5 / CISA KEV | **Risk Rating:** Critical | **Target Closure:** 2026-09-28

## POA&M Table
| Item ID | Weakness / Finding | Affected System | Control Reference | Responsible Role | Planned Action | Milestone 1 | Milestone 2 | Milestone 3 | Target Date | Status |
|---|---|---|---|---|---|---|---|---|---|---|
| POA-202609-007 | Unauthenticated API bypass grants full admin access (CVE-2026-76460, actively exploited) | Cisco ISE / ISE-PIC 3.1–3.5 | NIST 800-53 IA-2, AC-3 | Network/Identity Infrastructure Lead | Emergency patch to fixed release per version track | 2026-09-22: Inventory all ISE/ISE-PIC nodes and current patch levels | 2026-09-24: Patch internet/DMZ-facing nodes | 2026-09-25: Patch remaining internal nodes | 2026-09-25 | Open |
| POA-202609-008 | Six companion vulnerabilities (injection, access control, credential protection, input validation, DoS) in same platform release | Cisco ISE / ISE-PIC | NIST 800-53 SI-2 | Network/Identity Infrastructure Lead | Apply full patch bundle, not KEV CVE alone | 2026-09-24: Confirm patch bundle includes all 7 CVEs | 2026-09-25: Validate patch application via Cisco software check | N/A | 2026-09-25 | Open |
| POA-202609-009 | Possible pre-patch unauthorized administrative access during active-exploitation window | ISE admin/audit logs | NIST 800-53 AU-6 | Security Operations | Forensic review of admin access and policy-change logs since 2026-09-16 | 2026-09-23: Pull ISE audit logs for all nodes | 2026-09-26: Complete anomaly analysis | 2026-09-26: Escalate to IR if unauthorized change found | 2026-09-26 | Open |
| POA-202609-010 | API-level authentication parity not independently verified for other Tier-0 identity platforms | IAM/NAC architecture broadly | NIST CSF 2.0 PR.AA-01 | AI/Cloud Architecture & GRC | Add API-authentication-parity check to standing identity-infrastructure architecture review | 2026-09-28: Present as agenda item at next architecture review | N/A | N/A | 2026-09-28 | Open |

## Remediation Narrative
Patch all Cisco ISE and ISE-PIC nodes to the fixed release for their version track (3.1 Patch 12, 3.2 Patch 11, 3.3 Patch 12, 3.4 Patch 7, or 3.5 Patch 4), prioritizing any instance reachable from the internet or a DMZ segment given confirmed active exploitation. Because exploitation may already be underway against unpatched instances, treat the patch cycle and the forensic log review as parallel, not sequential, workstreams.

## Compensating Controls
Until patched, restrict ISE management-interface access to a dedicated out-of-band management network or VPN, and enable/verify heightened logging on all administrative API endpoints. These reduce but do not eliminate exposure — the underlying API authentication gap remains present until the vendor patch is applied.

## Verification & Closure Criteria
Closure requires: (1) confirmed patch deployment to the fixed release across all ISE/ISE-PIC nodes; (2) completed forensic log review with no unresolved anomalies, or an escalated incident record if unauthorized access is found; (3) documented confirmation that the full 7-CVE patch bundle was applied, not the KEV CVE in isolation; (4) API-authentication-parity review item logged for the next standing architecture review.

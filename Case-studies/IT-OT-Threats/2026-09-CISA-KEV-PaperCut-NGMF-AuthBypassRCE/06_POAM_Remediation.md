# Plan of Action & Milestones (POA&M)
## 2026-09-CISA-KEV-PaperCut-NGMF-AuthBypassRCE
**Date Opened:** 2026-09-07 | **Source:** CISA KEV | **Risk Rating:** Critical | **Target Closure:** 2026-09-14

## POA&M Table
| Item ID | Weakness / Finding | Affected System | Control Reference | Responsible Role | Planned Action | Milestone 1 | Milestone 2 | Milestone 3 | Target Date | Status |
|---|---|---|---|---|---|---|---|---|---|---|
| POA-202609-010 | Missing authentication + unsafe reflection chain to unauthenticated RCE (CVE-2026-81578, CVE-2026-82078) | PaperCut NG/MF server(s) | NIST 800-53 IA-2, CM-6 | IT Infrastructure Lead | Apply PaperCut fix per 2026-08-27 security bulletin | 2026-09-08: Confirm current PaperCut version against bulletin | 2026-09-10: Apply patch to all instances | 2026-09-11: Validate patched instances reject unauthenticated configuration changes | 2026-09-11 | Open |
| POA-202609-011 | Print-management interface unnecessarily internet-exposed | PaperCut NG/MF server(s) | CIS Control 12.2 | Network Engineering | Restrict management interface to internal administrative network | 2026-09-09: Audit current network exposure | 2026-09-11: Implement firewall/ACL restriction | 2026-09-11: Verify no external reachability via scan | 2026-09-11 | Open |
| POA-202609-012 | Potential compromise from exposure window given product's ransomware-initial-access history | PaperCut NG/MF server(s) | NIST 800-53 AU-6, IR-4 | Security Operations | Review logs for indicators of compromise or lateral movement | 2026-09-11: Pull logs for exposure window (since 2026-08-31 KEV listing) | 2026-09-14: Complete lateral-movement indicator review | 2026-09-14: Escalate to IR if any indicator found | 2026-09-14 | Open |

## Remediation Narrative
Apply PaperCut's fix per the 2026-08-27 security bulletin across all NG/MF instances, and independently restrict the management web interface to internal administrative networks regardless of patch status, since the underlying exposure pattern (an internet-facing management interface) is itself a standing risk beyond this specific CVE pair. Given the product's documented ransomware-initial-access history, the log review milestone should specifically check for lateral-movement indicators, not only local server compromise indicators.

## Compensating Controls
Until the patch is applied, restrict all access to the PaperCut management interface to a defined internal administrative network via firewall/ACL rules, and enable enhanced logging on the server if not already active.

## Verification & Closure Criteria
Closure requires: (1) confirmed patch application per the vendor bulletin across all instances; (2) confirmed removal of unrestricted internet access to the management interface, verified via external scan; (3) a completed log review covering the full exposure window (since 2026-08-31) with no unresolved indicators of compromise or lateral movement, or an escalated incident record if found. Evidence artifacts should be retained in the case file for audit purposes, consistent with this program's standard closure documentation practice.

# POA&M / Remediation Plan — CVE-2026-20262 (Cisco Catalyst SD-WAN Manager)

| # | Action | Owner | Target Date | Status |
|---|---|---|---|---|
| 1 | Identify all Cisco Catalyst SD-WAN Manager instances in inventory (CMDB cross-check) | Network Engineering | 2026-06-23 | Open |
| 2 | Apply Cisco fixed-software release addressing CVE-2026-20262 to all instances | Network Engineering | 2026-06-29 | Open — Emergency |
| 3 | Confirm CVE-2026-20245 (original case) remediation is complete on all instances before closing this POA&M | Network Engineering / GRC | 2026-06-29 | Open |
| 4 | Audit all vManage user accounts; disable inactive/shared accounts | IAM | 2026-06-25 | Open |
| 5 | Enforce MFA on all vManage administrative accounts | IAM | 2026-06-25 | Open |
| 6 | Restrict vManage management interface to dedicated, non-internet-routable network segment | Network Engineering | 2026-06-30 | Open |
| 7 | Forward vManage audit logs to SIEM; create alert rules for file-upload and config-change events | SOC | 2026-06-26 | Open |
| 8 | Review vManage logs from 2026-06-01 onward for indicators of exploitation predating patch | SOC / IR | 2026-06-24 | Open |
| 9 | Document closure evidence (patch version, account audit results, segmentation confirmation) | GRC | 2026-06-30 | Open |

## Specific Remediation
Apply the Cisco-published fixed software train for CVE-2026-20262 (per Cisco Security Advisory) to every Catalyst SD-WAN Manager appliance; there is no registry key, ACL, or configuration workaround that fully mitigates this path-traversal flaw — upgrade is mandatory.

## Risk Acceptance
Not applicable — a vendor patch is available and a federal due date (2026-06-29) applies. No risk acceptance pathway is appropriate while remediation is achievable within the compliance window.

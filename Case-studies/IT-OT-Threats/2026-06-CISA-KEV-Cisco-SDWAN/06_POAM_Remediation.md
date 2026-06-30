# Plan of Action & Milestones (POA&M)
## Case: CVE-2026-20245 — Cisco Catalyst SD-WAN Manager Command Injection (root)
**Date:** 2026-06-15 | **Analyst:** Blaise Kingko | **Risk Rating:** Critical

| Milestone | Action | Owner | Due Date | Status |
|---|---|---|---|---|
| **M1 — Patch Deployment** | Apply Cisco security patch for CVE-2026-20245 to all Catalyst SD-WAN Manager instances. Follow Cisco upgrade guide; test in lab environment first if non-production is available. | Network Engineering | 2026-06-18 | Immediate |
| **M2 — Admin Account Audit** | Enumerate all local and federated accounts with access to SD-WAN Manager. Remove all inactive, service, or shared accounts. Document all remaining accounts with owner and business justification. | Network Security / IAM | 2026-06-18 | Immediate |
| **M3 — MFA Enforcement** | Enforce MFA on all SD-WAN Manager administrator accounts. Integrate with enterprise IdP (Okta/AAD/Duo) if not already. | IAM / Network Engineering | 2026-06-20 | Priority |
| **M4 — Management Network Restriction** | Verify SD-WAN Manager UI and API are accessible only from dedicated management network segment. Block any direct internet or corporate-network routes to SD-WAN Manager management interfaces. | Network Engineering | 2026-06-20 | Priority |
| **M5 — SIEM Alert Configuration** | Forward SD-WAN Manager audit logs to SIEM. Create alert rule: notify SOC on any configuration policy change, user account creation, or file upload event on SD-WAN Manager. | SOC / Network Security | 2026-06-22 | Pending |
| **M6 — Post-Patch Validation** | After patch deployment, run vulnerability scan against SD-WAN Manager. Review audit logs from June 1–15 for anomalous file uploads or command executions indicative of exploitation. | Vulnerability Mgmt / SOC | 2026-06-22 | Pending |

## Success Metrics
| Metric | Target |
|---|---|
| SD-WAN Manager patched | 100% instances by June 18 |
| Unauthorized accounts removed | 0 stale/unused accounts by June 18 |
| MFA enforced on all admin accounts | 100% by June 20 |
| SIEM alerts active for vManage | By June 22 |

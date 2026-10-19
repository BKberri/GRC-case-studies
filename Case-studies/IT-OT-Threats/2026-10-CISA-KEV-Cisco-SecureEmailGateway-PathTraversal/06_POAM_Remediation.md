# POA&M / Remediation Plan, CVE-2026-76519 (Cisco Secure Email Gateway Path Traversal)

**Case ID:** 2026-10-CISA-KEV-Cisco-SecureEmailGateway-PathTraversal

| # | Weakness | Action | Resource | Milestone / Due Date | Status |
|---|---|---|---|---|---|
| 1 | Path traversal in File Reputation (AMP) attachment scanning (CVE-2026-76519) | Update Content Scanner Tools to 25.3.0.5525 or later via `contentscannerupdate` (no reboot required) | Email/Messaging team | Within 24 hours (emergency, CISA deadline already elapsed) | Open, Emergency |
| 2 | Underlying AsyncOS branch vulnerable | Upgrade AsyncOS to 15.5.5-014 (15.5 branch) or 16.5.0-780 (16.5 and below); migrate any 16.0 appliance, since no fixed 16.0 build exists | Email/Messaging team | Within 5 business days | Open |
| 3 | Unknown prior-exploitation exposure | Run `grep "System Security" system_logs` across every appliance in each cluster; escalate any indicator to Cisco TAC | SOC / IR team | Within 48 hours | Open, Emergency |
| 4 | No workaround available during remediation window | Document the absence of a workaround in the change record and prioritize this patch ahead of lower-severity work in the current patch cycle | Vulnerability Management | Immediate | Open |
| 5 | Residual exposure during remediation window | Re-validate appliance integrity (file-integrity check, root-account audit) after patching and before removing heightened monitoring | Email/Messaging + SOC | Within 5 business days of patch application | Planned |

**Specific Patch / Configuration Reference:** Content Scanner Tools 25.3.0.5525 or later (Cisco advisory cisco-sa-esa-afw-zqYJkjxp); AsyncOS 15.5.5-014 for the 15.5 branch; AsyncOS 16.5.0-780 for 16.5 and below; 16.0 appliances must migrate, as no fixed build exists for that branch.

**Owner of Record:** Blaise Kingko (Program POA&M Owner) | **Last Updated:** 2026-10-19

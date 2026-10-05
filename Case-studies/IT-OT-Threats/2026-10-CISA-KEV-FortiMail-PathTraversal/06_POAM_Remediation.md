# POA&M / Remediation Plan, CVE-2026-104286 (FortiMail Path Traversal)

**Case ID:** 2026-10-CISA-KEV-FortiMail-PathTraversal

| # | Weakness | Action | Resource | Milestone / Due Date | Status |
|---|---|---|---|---|---|
| 1 | Unauthenticated path traversal in FortiMail HTTP/HTTPS handling (CVE-2026-104286) | Disable Identity-Based Encryption (IBE) support via FortiMail CLI (interim compensating control) | Email/Messaging team | Within 24 hours of identification | Open, Emergency |
| 2 | Management interface reachable from the internet | Restrict FortiMail management interface to a trusted, out-of-band management network; remove any public-facing ACL allowing admin access | Network Security team | Within 24 hours | Open, Emergency |
| 3 | Unknown prior-exploitation exposure | Review FortiMail system and access logs for unauthorized file writes, unexpected admin accounts, or anomalous configuration changes since vulnerability disclosure window opened | SOC / IR team | Within 72 hours | Open |
| 4 | No vendor patch currently available | Monitor Fortinet PSIRT advisory FG-IR-26-175 for release of 8.0.2 / 7.6.7 / 7.4.9; apply immediately upon release | Vulnerability Management | Upon vendor release (tracking) | Tracking |
| 5 | Residual exposure during workaround window | Re-validate gateway integrity (file-integrity check, admin-account audit) after patch is applied and before removing heightened monitoring | Email/Messaging + SOC | Within 5 business days of patch application | Planned |

**Specific Patch / Configuration Reference:** Fixed releases 8.0.2, 7.6.7, 7.4.9 (per Fortinet PSIRT FG-IR-26-175); FortiMail 7.2.x must migrate to a supported branch, as 7.2 does not receive a direct fix.

**Owner of Record:** Blaise Kingko (Program POA&M Owner) | **Last Updated:** 2026-10-05

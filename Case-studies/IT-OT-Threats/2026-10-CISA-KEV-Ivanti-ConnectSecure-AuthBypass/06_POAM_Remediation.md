# POA&M / Remediation Plan, CVE-2026-104935 (Ivanti Connect Secure Authentication Bypass)

**Case ID:** 2026-10-CISA-KEV-Ivanti-ConnectSecure-AuthBypass

| # | Weakness | Action | Resource | Milestone / Due Date | Status |
|---|---|---|---|---|---|
| 1 | Authentication bypass by spoofing in Connect Secure (CVE-2026-104935) | Apply vendor fix (25.1.1.2, or 25.1.3.0/25.1.3.1, or 22.8R2.5 depending on active branch) to every internet-facing appliance | Network Security team | Within 24 hours (emergency, CISA deadline already elapsed) | Open, Emergency |
| 2 | Possible pre-disclosure compromise | Review appliance logs and session history against Volexity's published indicators of compromise for activity predating 2026-10-13 | SOC / IR team | Within 48 hours | Open, Emergency |
| 3 | Companion unpatched privilege-escalation flaw used in observed attack chain | Track Ivanti's forthcoming fix for the related privilege-escalation weakness and apply on release; in the interim, monitor for unexpected privilege changes on the appliance | Vulnerability Management | Upon vendor release (tracking) | Tracking |
| 4 | Credential exposure risk from any prior compromise | Rotate credentials for any accounts that authenticated through a Connect Secure appliance later confirmed exploited, and review for anomalous internal lateral-movement indicators | IAM / SOC | Within 5 business days of confirmed compromise | Planned |
| 5 | Recurrence risk | Add emergency out-of-cycle patch authority for perimeter VPN appliances to the standing change-management policy, given this is the second major remote-access-gateway KEV entry this program has logged in recent months | Security Architecture | Within 30 days | Planned |

**Specific Patch / Configuration Reference:** Ivanti Connect Secure 25.1.1.2 (for the 25.1.1.x line), 25.1.3.0 or 25.1.3.1 (for the 25.1.2.x line), 22.8R2.5 (for the 22.8R2.x line); 22.7.x and earlier are not affected by this CVE.

**Owner of Record:** Blaise Kingko (Program POA&M Owner) | **Last Updated:** 2026-10-19

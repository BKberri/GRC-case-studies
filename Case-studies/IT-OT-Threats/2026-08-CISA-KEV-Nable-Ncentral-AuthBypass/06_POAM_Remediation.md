# Plan of Action & Milestones (POA&M)
## 2026-08-CISA-KEV-Nable-Ncentral-AuthBypass
**Date Opened:** 2026-08-10 | **Source:** CISA KEV | **Risk Rating:** Critical | **Target Closure:** 2026-08-14

## POA&M Table
| Item ID | Weakness / Finding | Affected System | Control Reference | Responsible Role | Planned Action | Milestone 1 | Milestone 2 | Milestone 3 | Target Date | Status |
|---|---|---|---|---|---|---|---|---|---|---|
| POA-202608-010 | Authentication bypass, second incomplete-fix variant (CVE-2026-18577) | N-able N-central server | NIST 800-53 IA-2 | RMM Platform Owner | Apply N-central 2026.3 Hotfix 1 (build 2026.3.1.7) or later | 2026-08-11: Confirm current build version | 2026-08-11: Apply hotfix in maintenance window | 2026-08-12: Verify build version and platform functionality | 2026-08-12 | Open |
| POA-202608-011 | Unauthorized "Take Control" session risk during exposure window | N-central server and all managed endpoints | NIST 800-53 AC-17, AU-6 | Security Operations | Audit all Take Control session logs since 2026-08-01 for unattributed activity | 2026-08-11: Pull full session history | 2026-08-13: Cross-reference against help-desk/change records | 2026-08-14: Document findings; escalate to IR for any unattributed session | 2026-08-14 | Open |
| POA-202608-012 | Potential Cloudflare Tunnel persistence on managed endpoints | All endpoints managed by N-central | NIST 800-53 SC-7, SI-4 | Security Operations | Scan N-central server and all managed endpoints for unauthorized cloudflared processes/binaries | 2026-08-11: Deploy detection query fleet-wide | 2026-08-13: Complete scan and triage results | 2026-08-14: Remediate any confirmed unauthorized tunnels | 2026-08-14 | Open |

## Remediation Narrative
Apply N-able N-central 2026.3 Hotfix 1 (build 2026.3.1.7) or later immediately — this is the vendor's corrected fix following the incomplete initial patch (2026.2) for CVE-2026-18556. There is no supported workaround; the authentication bypass exists in the platform's core logic. Following the hotfix, conduct a full audit of "Take Control" session history since 2026-08-01 (the earliest confirmed exploitation date) cross-referenced against legitimate help-desk tickets and change records, and scan both the N-central server and every managed endpoint for unauthorized Cloudflare Tunnel (cloudflared) processes, which is the observed persistence mechanism.

## Compensating Controls
Until the hotfix is applied, consider temporarily restricting network access to the N-central server's administrative interface to a defined internal management network, and increase logging verbosity on "Take Control" session initiation events. If operationally feasible, disable "Take Control" functionality fleet-wide until the audit is complete.

## Verification & Closure Criteria
Closure requires: (1) confirmed N-central build at or above 2026.3.1.7; (2) completed Take Control session audit with no unattributed sessions, or an escalated multi-tenant incident record if unauthorized access is confirmed; (3) completed Cloudflare Tunnel sweep across the server and all managed endpoints with any unauthorized instances removed and root-caused. For MSP deployments, closure also requires documented client notification per contractual/regulatory obligations if any client endpoint shows evidence of unauthorized access.

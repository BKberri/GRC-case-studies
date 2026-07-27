# Plan of Action & Milestones (POA&M)
## Langflow Unauthenticated Root RCE via `exec_globals` (CVE-2026-0770)
**Date Opened:** 2026-07-27 | **Source:** CISA KEV | **Risk Rating:** Critical | **Target Closure:** 2026-08-10

## POA&M Table
| Item ID | Weakness / Finding | Affected System | Control Reference | Responsible Role | Planned Action | Milestone 1 | Milestone 2 | Milestone 3 | Target Date | Status |
|---|---|---|---|---|---|---|---|---|---|---|
| POA-202607-001 | Unauthenticated RCE via `exec_globals` param, `/api/v1/validate/code` | Langflow instances (all versions ≤1.7.3) | SI-2, IA-2, AC-3 | AI/Platform Engineering | Upgrade to patched Langflow release; restrict `/validate` endpoint to authenticated/internal-network access | 2026-07-28: Inventory all Langflow instances | 2026-07-31: Patch/upgrade all identified instances | 2026-08-04: Confirm endpoint access restriction deployed | 2026-08-04 | Open — Emergency |
| POA-202607-002 | Potential AWS credential / container metadata theft | Cloud compute hosting Langflow | SC-7, IA-5 | Security Operations / Cloud Engineering | Rotate all credentials reachable by affected instances; restrict IAM roles attached to hosts | 2026-07-28: Identify credentials/IAM roles in scope | 2026-08-01: Rotate credentials | 2026-08-04: Verify old credentials revoked | 2026-08-04 | Open — Emergency |
| POA-202607-003 | No formal AI-tooling asset inventory | AI/ML Center of Excellence deployments | NIST AI RMF MAP 4.1 | AI Governance / GRC | Establish intake process requiring security review before internal AI agent tools reach production or internet-facing status | 2026-08-01: Draft intake process | 2026-08-08: Review with AI CoE stakeholders | 2026-08-15: Publish and enforce | 2026-08-15 | Open |

## Remediation Narrative
Upgrade every Langflow deployment to the vendor-patched release addressing CVE-2026-0770 (consult the Langflow release notes/GHSA-g22f-v6f7-2hrh for the specific fixed version once published, and monitor ZDI-26-036 for confirmation). Where immediate upgrade is not possible, place the `/api/v1/validate/code` endpoint behind network-layer access control (VPN, private subnet, or authentication proxy) so it is not reachable from the public internet — this closes the exploitation path even before the patch is applied. In parallel, treat every AWS access key, environment variable, and credential reachable from an affected host as potentially compromised: rotate them, and review CloudTrail/IAM activity logs for anomalous API calls originating from the affected instance's associated role since 2026-06-27.

## Compensating Controls
Until patched, restrict inbound network access to the Langflow host to a known-good IP allowlist or VPN; disable or firewall the `/validate` endpoint specifically if the platform allows granular route control; attach a minimally-scoped IAM role (or none) to the host to limit blast radius of any credential theft.

## Verification & Closure Criteria
Closure requires: (1) confirmation via version check that all identified instances run a patched release, (2) confirmation that the validation endpoint is not reachable without authentication from an external network scan, (3) documented evidence of credential rotation for all identified in-scope credentials, and (4) a completed log review with no indicators of successful exploitation, or — if indicators are found — a completed incident response with root-cause closure.

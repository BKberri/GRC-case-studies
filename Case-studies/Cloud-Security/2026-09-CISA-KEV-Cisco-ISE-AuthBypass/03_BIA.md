# Business Impact Analysis
## 2026-09-CISA-KEV-Cisco-ISE-AuthBypass

## Illustrative Organization Profile
A mid-to-large enterprise using Cisco ISE as its centralized network access control (NAC) and 802.1X policy engine across corporate wired, wireless, and remote-access VPN segments, integrated with Active Directory for identity lookups.

## Impact Assessment
| Impact Category | Description | Severity |
|---|---|---|
| Operational | An attacker with administrative ISE access can rewrite network access policy, disable posture checks, or grant unauthorized devices trusted-segment access — directly affecting network availability and integrity for every segment ISE governs | Critical |
| Financial | Incident response, forensic log review across all ISE-mediated segments, policy re-validation, and potential downstream breach costs if the access gained was used for lateral movement | High |
| Reputational | If exploited to enable a broader network intrusion, the fact that the intrusion routed through the organization's own identity-governance platform is a materially worse disclosure narrative than a peripheral system compromise | High |
| Regulatory/Legal | Organizations subject to SOC 2, ISO 27001 certification, FedRAMP, or sector-specific regulation (e.g., NYDFS Part 500 for financial services) that rely on ISE-mediated access control as an audited control may face control-failure findings requiring remediation evidence in their next audit cycle | Medium-High |
| Data | Scope is bounded by what ISE-governed network segments and integrated identity stores (AD/LDAP) expose — potentially broad, since ISE integrates with the organization's core identity directory | High |

## Recovery Objectives
| Objective | Target |
|---|---|
| RTO (Recovery Time Objective) | 72 hours (emergency patch deployment across all ISE/ISE-PIC nodes, prioritizing internet/DMZ-facing instances first) |
| RPO (Recovery Point Objective) | Last known-good ISE policy configuration prior to the KEV disclosure date (2026-09-16) |
| MTTR (Mean Time to Recover) | 3-5 business days including patch deployment, admin log forensic review, and policy configuration validation |

## Regulatory Exposure
Given confirmed active exploitation, organizations running unpatched, internet-reachable ISE management interfaces should treat this as a potential incident requiring investigation rather than a routine patch cycle. If forensic review identifies unauthorized administrative access or policy changes, standard breach-notification analysis applies based on what data or network access was affected — document the investigation regardless of outcome, since "we checked and found no evidence of compromise" is itself required audit evidence for identity-infrastructure control assurance.

## Business Continuity Considerations
Because ISE is frequently a single point of policy control for an entire network's admission decisions, emergency patching carries its own availability risk — a botched ISE upgrade can lock out legitimate network access organization-wide. Recommend a staged rollout (non-production/lab ISE nodes first, then a canary production node, then full fleet) with a validated rollback plan, rather than a simultaneous fleet-wide upgrade, even under the 3-day CISA emergency window.

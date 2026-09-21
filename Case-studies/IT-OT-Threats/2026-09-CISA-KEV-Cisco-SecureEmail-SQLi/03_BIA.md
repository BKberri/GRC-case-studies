# Business Impact Analysis
## 2026-09-CISA-KEV-Cisco-SecureEmail-SQLi

## Illustrative Organization Profile
An enterprise using Cisco Secure Email Gateway appliances at the network perimeter to filter inbound/outbound email traffic for the organization's primary mail domains.

## Impact Assessment
| Impact Category | Description | Severity |
|---|---|---|
| Operational | Root compromise of the mail gateway can disrupt email delivery, enable traffic interception/modification, and provide a network pivot point | High |
| Financial | Incident response, appliance rebuild/reimaging, forensic email-traffic review, and potential costs if the appliance was used to intercept sensitive correspondence | High |
| Reputational | Email interception at the gateway level can expose sensitive business communications; disclosure narrative is materially worse if attacker dwell time was extended past the missed patch deadline | Medium-High |
| Regulatory/Legal | If regulated data (PII, financial, health) traversed a compromised gateway during the exposure window, standard breach-notification analysis applies | Medium |
| Data | Scope includes any email content processed by the affected gateway during the exposure window, plus any lateral-movement access gained from the appliance's network position | High |

## Recovery Objectives
| Objective | Target |
|---|---|
| RTO (Recovery Time Objective) | 24-48 hours given the deadline has already passed — treat as emergency, not routine, patching |
| RPO (Recovery Point Objective) | Last known-good gateway configuration prior to 2026-09-14 (KEV addition date) |
| MTTR (Mean Time to Recover) | 3-5 business days including patch deployment and forensic log/traffic review |

## Regulatory Exposure
Given the CISA deadline has already elapsed, organizations should document both the patch action taken and the rationale/timeline for any delay, since this becomes relevant evidence in any subsequent audit or incident investigation regarding patch-management control effectiveness.

## Business Continuity Considerations
Email gateway patching can typically be performed with minimal service disruption via standard maintenance windows, but organizations should prioritize this above routine patch cycles given the confirmed active-exploitation status and the missed federal remediation deadline.

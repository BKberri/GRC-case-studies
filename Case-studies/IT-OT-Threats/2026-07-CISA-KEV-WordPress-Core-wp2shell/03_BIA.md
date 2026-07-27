# Business Impact Analysis
## WordPress Core "wp2shell" Unauthenticated RCE Chain (CVE-2026-63030 + CVE-2026-60137)

## Illustrative Organization Profile
A mid-size retail/consumer brand operates its public marketing site and a customer-facing blog/support-content portal on self-hosted WordPress, integrated with a customer database for newsletter signups and support ticket references.

## Impact Assessment
| Impact Category | Description | Severity |
|---|---|---|
| Operational | Compromised site requires takedown, forensic imaging, and rebuild from clean backups; potential extended outage of public-facing web presence | High |
| Financial | Incident response, forensic investigation, and potential SEO/search-blacklist recovery costs; lost e-commerce or lead-generation revenue during outage | Medium-High |
| Reputational | Defacement, malware-serving, or data-breach disclosure directly damages customer and partner trust — the public website is often a brand's most visible surface | High |
| Regulatory/Legal | If the WordPress database or connected systems held customer PII (newsletter emails, support tickets), state breach-notification laws apply; GDPR if EU residents are affected | Medium-High |
| Data | Newsletter subscriber emails, support ticket metadata, and any credentials stored in `wp-config.php` (database credentials, authentication keys) are directly at risk given observed attacker TTPs | High |

## Recovery Objectives
| Objective | Target |
|---|---|
| RTO (Recovery Time Objective) | 8–24 hours (rebuild from clean backup predating 2026-07-17, patched core) |
| RPO (Recovery Point Objective) | Last clean backup prior to 2026-07-17 23:29 UTC (earliest confirmed probing) |
| MTTR (Mean Time to Recover) | 24–48 hours including compromise assessment and credential rotation |

## Regulatory Exposure
State breach-notification statutes apply if customer PII (newsletter subscriber data, support ticket contact information) was reachable from the compromised database and exfiltration cannot be ruled out. GDPR's 72-hour notification requirement applies if EU-resident data is implicated. If the organization is publicly traded, SEC materiality assessment is warranted if the compromised site is a significant customer-facing channel or if the incident results in meaningful business disruption or data exposure.

## Business Continuity Considerations
Maintain a static, pre-built fallback version of critical public-facing pages (or a documented manual-failover process to a CDN-cached version) so the public web presence can remain available while the primary WordPress instance is taken offline for forensic review and rebuild. Any newsletter or support-ticket integration should be paused or isolated during remediation to prevent further data exposure through a potentially still-compromised database connection.

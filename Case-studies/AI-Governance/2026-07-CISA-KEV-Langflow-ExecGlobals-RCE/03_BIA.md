# Business Impact Analysis
## Langflow Unauthenticated Root RCE via `exec_globals` (CVE-2026-0770)

## Illustrative Organization Profile
A mid-size technology company operates an internal AI Center of Excellence that has stood up Langflow on cloud infrastructure (AWS EC2/ECS) to let data science and product teams prototype LLM-powered agents that call internal APIs, query customer data warehouses, and in some flows hold service-account credentials for downstream SaaS tools.

## Impact Assessment
| Impact Category | Description | Severity |
|---|---|---|
| Operational | Root-level compromise of the Langflow host disrupts every agent workflow running on it and requires full host rebuild, not just a patch, once compromise is confirmed | High |
| Financial | Cloud credential theft (AWS keys, container metadata) can enable resource hijacking (cryptomining, further attack infrastructure) and incident-response/forensic costs | High |
| Reputational | If customer-facing data or downstream SaaS credentials were reachable from compromised flows, disclosure obligations and customer trust impact follow | High |
| Regulatory/Legal | Depending on data types reachable via hijacked flows/credentials, state breach-notification laws and (if EU-resident data is implicated) GDPR 72-hour notification may be triggered | Medium-High |
| Data | Exposure scope depends entirely on what credentials and data sources were wired into flows on the compromised instance — potentially customer PII, internal API keys, or proprietary model/prompt data | High |

## Recovery Objectives
| Objective | Target |
|---|---|
| RTO (Recovery Time Objective) | 24 hours (rebuild Langflow host from clean image, patched version) |
| RPO (Recovery Point Objective) | Last known-clean flow/configuration backup prior to 2026-06-27 (earliest confirmed exploitation date) |
| MTTR (Mean Time to Recover) | 24–48 hours including credential rotation and forensic log review |

## Regulatory Exposure
If the compromised instance held or could reach personal data, GDPR's 72-hour breach notification clock begins at confirmed awareness of the breach, not at patch application. SEC cybersecurity disclosure rules (material incident, 4-business-day Form 8-K) apply if the incident is determined material to a public company's operations or finances — plausible if hijacked cloud credentials enabled broader account compromise. State breach-notification statutes apply if any state-resident personal data was reachable from the compromised flows or credentials.

## Business Continuity Considerations
Until the Langflow instance is rebuilt and credentials rotated, any workflow or automation dependent on that instance should fail over to manual process or be paused — continuing to route production data through a host with unconfirmed compromise status compounds exposure. Compensating controls during remediation: network isolation of the instance, temporary revocation of any cloud IAM role attached to the host, and heightened monitoring on any service account whose credentials may have been reachable.

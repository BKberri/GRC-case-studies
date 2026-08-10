# Business Impact Analysis
## 2026-08-CISA-KEV-Progress-LoadMaster-CommandInjection

## Illustrative Organization Profile
An enterprise using Progress Kemp LoadMaster appliances to load-balance traffic for its customer-facing web applications and internal business-critical services, with the appliance's management API reachable from the internet for remote administration.

## Impact Assessment
| Impact Category | Description | Severity |
|---|---|---|
| Operational | Root compromise of the ADC threatens availability and integrity of every application it load-balances; attacker could redirect, intercept, or disrupt traffic at will | Critical |
| Financial | Incident response, appliance rebuild/reimaging, and potential business disruption for every customer-facing application behind the compromised ADC | Critical |
| Reputational | Compromise of perimeter traffic-management infrastructure serving customer-facing applications carries significant public-facing risk if exploited to redirect or tamper with traffic | High |
| Regulatory/Legal | If the ADC's position in the traffic path allowed interception of customer data (credentials, payment data, PII) in transit, breach-notification and PCI-DSS obligations may apply depending on what traffic it serves | Critical |
| Data | Root-level access to the ADC could enable traffic interception/modification for any application behind it — the data-exposure scope is bounded by what those applications transmit through the appliance | Critical |

## Recovery Objectives
| Objective | Target |
|---|---|
| RTO (Recovery Time Objective) | 6 hours (patch, or rebuild from known-good image if compromise is confirmed) |
| RPO (Recovery Point Objective) | 24 hours (last verified-good appliance configuration backup) |
| MTTR (Mean Time to Recover) | 1-2 business days including full log review back to 2026-06-29 and traffic-integrity verification for applications behind the appliance |

## Regulatory Exposure
Given the ADC's position intercepting traffic for potentially many downstream applications, a confirmed compromise requires assessing whether payment card data (PCI-DSS scope), customer PII, or authentication credentials transiting the appliance during the exposure window (2026-06-29 onward) were captured or manipulated. Organizations processing payment card data through a compromised LoadMaster instance should treat this as a potential PCI-DSS-scoped incident requiring forensic review consistent with card-brand incident-response requirements.

## Business Continuity Considerations
Because the ADC sits directly in the production traffic path, remediation must be carefully sequenced to avoid a wider outage than the vulnerability itself would cause — patching in a maintenance window with validated failover to a secondary appliance (if a high-availability pair exists) is strongly preferred over an emergency mid-traffic patch. Compensating controls during remediation should include restricting management-API access to a defined administrative network and reviewing traffic logs for any signs of redirection or tampering during the confirmed exposure window.

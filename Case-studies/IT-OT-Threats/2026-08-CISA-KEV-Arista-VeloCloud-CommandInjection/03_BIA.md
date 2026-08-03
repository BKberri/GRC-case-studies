# Business Impact Analysis
## 2026-08-CISA-KEV-Arista-VeloCloud-CommandInjection

## Illustrative Organization Profile
A regional multi-site retail chain operating 220 store locations, three distribution centers, and a corporate headquarters, all connected via a VeloCloud SD-WAN fabric managed through a single on-premises Orchestrator instance. Point-of-sale connectivity, inventory synchronization, and corporate VoIP all traverse the SD-WAN fabric.

## Impact Assessment
| Impact Category | Description | Severity |
|---|---|---|
| Operational | Loss of orchestrator control could disrupt WAN connectivity across all 220+ sites simultaneously, halting POS transaction processing, inventory sync, and store-to-corporate connectivity | Critical |
| Financial | Multi-site POS outage during business hours; estimated revenue-at-risk scales with store count and average transaction volume per hour of downtime | Critical |
| Reputational | Customer-facing payment disruption at scale, particularly if paired with public disclosure of a network intrusion, risks brand and franchisee trust | High |
| Regulatory/Legal | If orchestrator compromise is used to pivot toward POS/payment network segments, PCI-DSS scope and breach-notification obligations are triggered | High |
| Data | Orchestrator itself does not typically store cardholder data, but compromised WAN routing/configuration could enable interception or redirection of traffic between stores and payment processors | Medium-High |

## Recovery Objectives
| Objective | Target |
|---|---|
| RTO (Recovery Time Objective) | 4 hours (restore orchestrator to known-good state / failover management plane) |
| RPO (Recovery Point Objective) | 1 hour (last known-good configuration backup) |
| MTTR (Mean Time to Recover) | 6–8 hours including forensic triage of orchestrator and spot-checked edge devices |

## Regulatory Exposure
If forensic review confirms the orchestrator compromise was used to access or exfiltrate cardholder data or other regulated data in transit, PCI-DSS incident response and notification obligations apply, along with applicable state breach-notification laws. Because this is a network-infrastructure compromise rather than a direct data-store breach, the primary regulatory question is scope: whether payment-card network segments were reachable from the compromised orchestrator, which determines whether this becomes a reportable cardholder-data incident under the organization's PCI-DSS QSA relationship.

## Business Continuity Considerations
Retail sites with local store controllers/edge devices can typically fail into a degraded local-processing mode if central orchestrator connectivity is lost, but this depends on whether the attacker used orchestrator access to push malicious configuration to edges (in which case local failover state cannot be trusted). Compensating controls during remediation should include out-of-band verification of edge-device configuration integrity, temporary manual monitoring of WAN traffic patterns for anomalies, and readiness to isolate individual sites from the fabric if store-level compromise indicators appear.

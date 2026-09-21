# Risk Assessment
## 2026-09-NIST-NVD-Langflow-RootRCE

## Risk Scoring
| Method | Score | Rating |
|---|---|---|
| Likelihood x Impact Matrix | 4 x 5 = 20 | Critical |
| CVSS Base Score | 9.6 (Critical) | Critical |
| FAIR Qualitative | High loss exposure — root code execution plus cloud credential theft path, elevated likelihood given Langflow's established rapid-weaponization pattern | Critical |

## Risk Narrative
Likelihood is scored at 4 (PoC public / high-confidence imminent) rather than a lower theoretical score, despite no confirmed KEV listing as of this sweep, because Langflow's documented history — four prior findings, each of which reached active exploitation or KEV status within weeks of disclosure — establishes a base rate this program weighs directly in scoring rather than treating each new Langflow CVE as an independent, un-contextualized data point. Impact is scored at 5 (full system compromise) because root code execution combined with a cloud-metadata-service credential-theft path enables an attacker to pivot from a single compromised Langflow instance into the broader AWS account it runs within.

## Framework Control Gaps
- **NIST 800-53 SC-7 (Boundary Protection) / SC-39 (Process Isolation):** Root cause — user-submitted workflow components are not adequately sandboxed from host-level network and code-execution capability.
- **NIST AI RMF MANAGE 4.1 (Risk treatment prioritized based on impact):** Given Langflow's documented five-finding pattern, this program recommends organizations formally reclassify Langflow as a standing elevated-risk asset in their AI system inventory rather than re-assessing risk fresh with each new CVE.
- **NIST CSF 2.0 PR.PS-01 (Configuration management):** Instance metadata service configuration (IMDSv1 vs IMDSv2) is a directly relevant compensating control this finding specifically implicates.
- **ISO 42001 Clause 6.1.3 (AI risk treatment):** A platform with this recurrence rate warrants documented risk-treatment escalation (e.g., network isolation requirements, mandatory IMDSv2) beyond simple patch-and-close.

## Residual Risk Statement
After upgrading to the fixed Langflow release (beyond 1.10.0), residual risk drops to Medium rather than Low, reflecting this program's assessment that Langflow's structural code-execution surface makes recurrence likely regardless of any single patch. Organizations should pair the version upgrade with enforced IMDSv2 (disabling IMDSv1) on any cloud instance hosting Langflow, and network-level egress restriction from Langflow hosts, as standing compensating controls independent of patch status.

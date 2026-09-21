# Risk Assessment
## 2026-09-CISA-KEV-Cisco-SecureEmail-SQLi

## Risk Scoring
| Method | Score | Rating |
|---|---|---|
| Likelihood x Impact Matrix | 5 x 5 = 25 | Critical |
| CVSS Base Score | 9.8 (Critical) | Critical |
| FAIR Qualitative | Very high loss exposure — unauthenticated, remotely reachable via ordinary email, confirmed active exploitation, root-level outcome | Critical |

## Risk Narrative
Likelihood is scored at 5 (actively exploited) based on CISA's KEV confirmation. Impact is scored at 5 (full system compromise) because successful exploitation yields root-level OS command execution on an appliance that, by design, processes all inbound and outbound organizational email and is frequently granted elevated internal network trust as security infrastructure. The CISA remediation due date (2026-09-17) has already passed as of this report's publication date, meaning any organization that has not yet patched is both out of compliance with the federal emergency window and carries materially elevated risk the longer the gap persists, since exploitation is confirmed ongoing in the broader internet population.

## Framework Control Gaps
- **NIST 800-53 SI-10 (Information Input Validation):** Root cause — the email-parsing logic did not adequately validate/sanitize input before constructing SQL queries.
- **NIST 800-53 SI-2 (Flaw Remediation):** Organizations still unpatched past the 2026-09-17 CISA deadline should treat this as an overdue emergency-patch gap requiring executive escalation.
- **NIST CSF 2.0 PR.PS-06 (Secure software development practices are integrated):** Input-parsing vulnerabilities in security-appliance software reflect a supply-chain quality dependency organizations cannot directly remediate beyond timely patching.
- **ISO 27001:2022 A.8.28 (Secure Coding):** Vendor-side gap; organizational control is limited to patch cadence and network segmentation of the affected appliance.

## Residual Risk Statement
After applying the fixed AsyncOS build for the appropriate release train, residual risk drops to Low. Organizations that remain unpatched past the CISA due date should treat any Secure Email Gateway internet-facing instance as a potential compromise pending forensic review of appliance logs and any observed anomalous outbound traffic, rather than assuming the patch alone resolves prior exposure.

# Business Impact Analysis
## 2026-08-CISA-KEV-Cisco-FMC-HardcodedPassword

## Illustrative Organization Profile
A regional healthcare system operating a hybrid network of hospital campuses and outpatient clinics, using Cisco Secure Firewall appliances managed centrally through a single FMC instance to enforce segmentation between clinical systems, guest networks, and corporate IT.

## Impact Assessment
| Impact Category | Description | Severity |
|---|---|---|
| Operational | Unauthorized access to firewall policy/config data could enable an attacker to map network segmentation ahead of a targeted attack on clinical or PHI-handling systems | High |
| Financial | Incident response, forensic review of firewall policy integrity across all managed appliances, and potential ransomware exposure if segmentation is undermined | High |
| Reputational | Healthcare breaches carry outsized public and regulatory scrutiny; disclosure of a firewall-management compromise ahead of a broader incident compounds reputational harm | High |
| Regulatory/Legal | If attacker access to FMC is later linked to unauthorized PHI access, HIPAA Breach Notification Rule (45 CFR §164.400-414) obligations are triggered, including HHS OCR reporting | Critical |
| Data | FMC itself holds firewall policy, network topology, and event logs — not PHI directly — but exposure of segmentation logic materially aids an attacker targeting PHI-handling segments | Medium-High |

## Recovery Objectives
| Objective | Target |
|---|---|
| RTO (Recovery Time Objective) | 8 hours (patch, credential rotation, and firewall policy integrity verification) |
| RPO (Recovery Point Objective) | 24 hours (last verified-good firewall policy baseline) |
| MTTR (Mean Time to Recover) | 1–2 business days including full policy audit across all managed appliances |

## Regulatory Exposure
HIPAA's Security Rule (45 CFR §164.312) requires access controls and audit controls over systems that protect ePHI, and firewall infrastructure segmenting clinical networks falls within that scope even though FMC does not store PHI directly. If forensic review determines the exposed account was used to weaken segmentation controls protecting PHI-handling systems, the organization's HIPAA breach-risk assessment (45 CFR §164.402) would need to evaluate whether unauthorized access to or disclosure of PHI occurred as a downstream consequence, triggering notification timelines if so.

## Business Continuity Considerations
Firewall enforcement itself is not disrupted by this vulnerability — the risk is unauthorized visibility and potential tampering, not availability. Compensating controls during remediation should include manual review of recent firewall policy change logs for unauthorized modifications, temporary enhanced monitoring of FMC administrative activity, and readiness to fail back to last-known-good policy configurations if tampering is discovered.

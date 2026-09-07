# Control Mapping
## 2026-09-CISA-KEV-PaperCut-NGMF-AuthBypassRCE

## Applicable Frameworks
NIST CSF 2.0 and NIST 800-53 Rev 5 for enterprise risk management and authentication/configuration control specificity; ISO 27001:2022 Annex A for ISMS-aligned organizations; CIS Controls v8 for network architecture and prioritized remediation guidance.

## Control Mapping Table
| Framework | Control ID | Control Name | Applicability | Gap / Status |
|---|---|---|---|---|
| NIST 800-53 | IA-2 | Identification and Authentication | Critical configuration function reachable without authentication (CVE-2026-81578) | Gap (vendor, now fixed) |
| NIST 800-53 | CM-6 | Configuration Settings | Configuration values were not validated against untrusted/reflective-execution input (CVE-2026-82078) | Gap (vendor, now fixed) |
| NIST 800-53 | SI-4 | System Monitoring | Product category historically under-monitored relative to its demonstrated risk (ransomware initial-access history) | Gap (organizational) |
| NIST CSF 2.0 | PR.AA-01 | Identities and credentials are managed | Management interfaces across all infrastructure categories — not only "core" security systems — require baseline authentication enforcement | Gap |
| ISO 27001 | A.8.9 | Configuration Management | Reflection-based configuration handling introduced an unintended code-execution path | Gap (vendor) |
| CIS Controls | CIS 12.2 | Establish and Maintain a Secure Network Architecture | Widespread internet exposure of print-management interfaces indicates a network-segmentation gap beyond this specific product | Gap |

## Control Narrative
This finding combines a straightforward authentication gap (IA-2) with a more subtle configuration-handling flaw (CM-6) that turned configuration data into a code-execution vector — the kind of defect that specifically defeats the mental model "an attacker can change some settings, so what." The control lesson worth elevating to program-level guidance is prioritization: PaperCut's specific, well-documented history as a ransomware initial-access vector (Cl0p/Bl00Dy, 2023) means this product category should be held to the same patch-SLA and internet-exposure discipline this program applies to perimeter VPN and network appliances, not treated as lower-priority "supporting infrastructure." The scale of exposure reported publicly (1,000+ internet-facing instances) suggests this prioritization gap is an industry-wide pattern, not specific to any one organization — which is precisely the kind of finding that should prompt an internal audit of what other "supporting infrastructure" categories may carry disproportionate risk relative to their perceived criticality.

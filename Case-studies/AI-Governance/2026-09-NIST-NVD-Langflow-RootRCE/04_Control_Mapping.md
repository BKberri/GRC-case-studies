# Control Mapping
## 2026-09-NIST-NVD-Langflow-RootRCE

## Applicable Frameworks
NIST AI RMF and ISO 42001 for AI-platform risk-treatment prioritization; NIST CSF 2.0 and NIST 800-53 Rev 5 for the underlying process-isolation and boundary-protection control failures; MITRE ATLAS for AI-specific attack-technique mapping.

## Control Mapping Table
| Framework | Control ID | Control Name | Applicability | Gap / Status |
|---|---|---|---|---|
| NIST 800-53 | SC-39 | Process Isolation | User-submitted workflow components execute with host-level code and network access | Gap (vendor, patched) |
| NIST 800-53 | SC-7 | Boundary Protection | SSRF path to cloud instance metadata service not restricted | Gap (organizational compensating control recommended: IMDSv2) |
| NIST AI RMF | MANAGE 4.1 | Risk treatment prioritized based on impact | Fifth Langflow finding warrants standing elevated-risk classification, not per-CVE reassessment | Organizational — recommended |
| ISO 42001 | 6.1.3 | AI risk treatment | Recurring platform risk pattern warrants documented treatment escalation | Organizational — recommended |
| MITRE ATLAS | ML Attack Staging | Adversarial workflow component submission as the attack entry point | Applicable |

## Control Narrative
This is the fifth Langflow finding this program has logged in under 90 days, and this program's control recommendation this time goes beyond the individual patch: organizations running Langflow should formally document it as a standing elevated-risk AI platform in their asset inventory, with mandatory compensating controls (IMDSv2 enforcement, network egress restriction, no production use without additional sandboxing) applied regardless of current patch level, rather than re-litigating risk treatment with each new CVE. The recurrence rate itself is the control-relevant data point — a platform whose core functionality (executing user-submitted workflow components) inherently resists full sandboxing should be governed accordingly.

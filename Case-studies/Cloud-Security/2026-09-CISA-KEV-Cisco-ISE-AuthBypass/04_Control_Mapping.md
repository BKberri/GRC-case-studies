# Control Mapping
## 2026-09-CISA-KEV-Cisco-ISE-AuthBypass

## Applicable Frameworks
NIST CSF 2.0 and NIST 800-53 Rev 5 for the core authentication/access-enforcement control failure; ISO 27001:2022 for configuration and secure-authentication controls; CIS Controls v8 for prioritized remediation guidance on network infrastructure and identity systems.

## Control Mapping Table
| Framework | Control ID | Control Name | Applicability | Gap / Status |
|---|---|---|---|---|
| NIST 800-53 | IA-2 | Identification and Authentication | A privileged API endpoint did not enforce authentication equivalent to the front-end management interface | Gap (vendor, patched) |
| NIST 800-53 | AC-3 | Access Enforcement | Unauthenticated request could reach privileged administrative functionality | Gap (vendor, patched) |
| NIST 800-53 | SI-2 | Flaw Remediation | Organizational patch cadence for Tier-0 identity infrastructure must support 3-day emergency windows | Organizational — verify |
| NIST CSF 2.0 | PR.AA-01 | Identities and credentials are managed | Centralized NAC/identity platform itself requires hardened, monitored patch and access management | Organizational — verify |
| NIST CSF 2.0 | DE.CM-01 | Networks and network services are monitored | Detection capability for anomalous administrative access to ISE should be independently verified, not assumed | Organizational — verify |
| ISO 27001:2022 | A.8.9 | Configuration Management | Authentication-boundary gap on a privileged API is a configuration/architecture-level control failure | Gap (vendor, patched) |
| CIS Controls v8 | Control 5 | Account Management | Administrative account/API access to network identity infrastructure requires ongoing review | Organizational — verify |
| CIS Controls v8 | Control 12 | Network Infrastructure Management | Network-layer compensating controls (management-plane isolation) reduce exposure pending patch | Recommended |

## Control Narrative
The Cisco-side gap in CVE-2026-76460 is now closed by vendor patch, but this finding surfaces a structural pattern this program flags repeatedly in identity-and-access-management infrastructure: privileged API endpoints are not always held to the same authentication standard as the primary user-facing interface they sit behind, creating a bypass path that traditional "login page" security review does not catch. Organizations running ISE — or any centralized NAC/IAM platform — should treat API-level authentication parity as an explicit architecture review item, not an assumption. The six companion CVEs disclosed in the same advisory (injection, access control, credential protection, input validation, DoS) further indicate the platform underwent a broader internal security review by Cisco, suggesting organizations should apply the full patch bundle rather than cherry-picking the KEV-listed CVE alone.

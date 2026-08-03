# Control Mapping
## 2026-08-MSRC-Azure-CosmosDB-CrossTenantEscape

## Applicable Frameworks
NIST CSF 2.0 and NIST 800-53 Rev 5 for enterprise/third-party risk management controls; ISO 27001:2022 Annex A for ISMS-aligned cloud-service-use controls; CIS Controls v8 for data-protection guidance. This case is framework-atypical in that the primary controls are third-party risk management and cloud governance controls rather than technical remediation controls, since the vulnerability and its fix were entirely provider-side.

## Control Mapping Table
| Framework | Control ID | Control Name | Applicability | Gap / Status |
|---|---|---|---|---|
| NIST 800-53 | SA-9 | External System Services | Requires documented oversight of security controls provided by external/cloud service providers | Addressed (Microsoft's response validates this control's effectiveness) |
| NIST 800-53 | CA-3 | Information Exchange / System Interconnections | Governs risk acceptance for interconnections with external systems including CSP control planes | Partial |
| NIST CSF 2.0 | GV.SC-06 | Planning and due diligence are performed to reduce risks before entering into formal supplier relationships | Supports the case for maintaining a live CSP risk register updated with incidents like this one | Addressed |
| NIST CSF 2.0 | ID.SC-04 (legacy) / GV.SC-07 | Suppliers are monitored to confirm they are meeting contractual obligations | This incident is a monitoring data point to log against Microsoft's Azure obligations | Addressed |
| ISO 27001 | A.5.23 | Information Security for Use of Cloud Services | Requires ongoing monitoring of cloud provider security posture and incident handling | Addressed |
| ISO 27001 | A.5.19 | Information Security in Supplier Relationships | Broader supplier/CSP risk management program this incident feeds into | Addressed |
| CIS Controls | CIS 3.11 | Encrypt Sensitive Data at Rest | Reduces impact of any future control-plane compromise by limiting plaintext data exposure even with key access | Partial (customer-side, defense-in-depth) |

## Control Narrative
The controls in this case are predominantly governance and third-party risk management controls (SA-9, GV.SC-06/07, A.5.23, A.5.19) rather than technical remediation controls, because the vulnerability, exploit chain, and fix were entirely contained within Microsoft's Azure control plane — no customer-deployed configuration, IAM policy, or network control could have prevented or detected this specific exposure. This is precisely the scenario third-party/cloud-provider risk management programs exist to address: the organization's control is not "prevent this vulnerability" but "maintain visibility into and documentation of how well our CSPs handle vulnerabilities like this one when they occur."

A mature control environment treats CSP security advisories — even ones stating "no customer action required" — as inputs to the vendor risk register, tracked alongside SOC 2 report reviews, CSA STAR assessments, and periodic CSP risk reassessments. As a defense-in-depth measure independent of this specific incident, CIS 3.11 (encryption of sensitive data at rest with customer-managed keys where the service supports it) reduces the blast radius of any future control-plane key-exposure scenario, since a compromised platform-wide key would not by itself decrypt customer-managed-key-protected data.

# Control Mapping
## 2026-08-CISA-KEV-Apache-Tomcat-EncryptInterceptor

## Applicable Frameworks
NIST CSF 2.0 and NIST 800-53 Rev 5 for enterprise risk management and data-protection control specificity; ISO 27001:2022 Annex A for ISMS-aligned organizations; CIS Controls v8 for prioritized remediation and vulnerability-management guidance.

## Control Mapping Table
| Framework | Control ID | Control Name | Applicability | Gap / Status |
|---|---|---|---|---|
| NIST 800-53 | SC-8 | Transmission Confidentiality and Integrity | Cluster inter-node traffic encryption is silently bypassed | Gap (vendor regression) |
| NIST 800-53 | SI-2 | Flaw Remediation | Prior CVE fix introduced this regression — patch-verification process gap | Gap (process) |
| NIST 800-53 | SC-7 | Boundary Protection | Cluster network segment should not be reachable by untrusted network positions regardless of encryption status | Partial |
| NIST CSF 2.0 | PR.DS-02 | Data-in-transit is protected | Directly implicated control outcome | Gap |
| NIST CSF 2.0 | DE.CM-01 | Networks are monitored to detect potential adverse events | Unencrypted cluster traffic where encryption is expected should be a detectable anomaly | Gap |
| ISO 27001 | A.8.24 | Use of Cryptography | Requires effective, verified use of cryptographic controls for data in transit | Gap |
| CIS Controls | CIS 7.1 | Establish and Maintain a Vulnerability Management Process | Should include patch-verification steps beyond version-number confirmation for security-relevant components | Gap |

## Control Narrative
This finding is a valuable illustration of a control-verification gap rather than a simple missing-patch gap: the encryption control (EncryptInterceptor) was present and configured correctly, but a *later* patch for an unrelated CVE silently broke its enforcement. Organizations that track "is the patch applied" as their sole verification step for security controls would not have caught this — they would need to independently verify that the control's *behavior* (encrypted cluster traffic) matches its *configuration* (EncryptInterceptor enabled), for example via periodic network captures or automated control-testing scripts run after every patch cycle affecting the relevant component.

This case also reinforces a broader pattern for the AI Governance Watch: Unit 42's attribution of AI-assisted tooling to the threat actor exploiting this flaw is a concrete, dated data point that adversary tradecraft is incorporating AI acceleration for vulnerability discovery and exploitation chaining. Organizations should factor this into patch-SLA risk models — the assumption that "we have a week or two before mass exploitation" is compressing for widely-deployed infrastructure like Tomcat.

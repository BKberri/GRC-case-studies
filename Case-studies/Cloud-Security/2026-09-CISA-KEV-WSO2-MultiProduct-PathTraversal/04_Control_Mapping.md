# WSO2 Multiple Products Path Traversal — Framework Control Mapping

Case Study ID: CS-CLOUD-2026-09-001 | Risk Register Reference: RR-081 | Report Period: 2026-09-21 to 2026-09-28

---

## 3.1 NIST CSF 2.0 Mapping

| CSF Function | Subcategory | Gap or Finding |
|---|---|---|
| **GOVERN** | GV.RM-06 (risk response strategy), GV.SC-04 (supplier/third-party risk) | Vendor risk management processes should flag WSO2 as Tier-0 identity infrastructure requiring an accelerated patch SLA. A KEV addition should trigger a pre-defined governance response, not an ad hoc one. |
| **IDENTIFY** | ID.AM-02 (software inventory), ID.RA-01 (vulnerability identification) | An organization that cannot answer "which of our environments run an affected WSO2 version" within hours of a KEV addition has an asset inventory gap at the exact layer where speed matters most. |
| **PROTECT** | PR.AA-05 (access permissions/authorizations managed), PR.DS-01 (data-at-rest protection) | PR.AA-05 gap: the runtime identity WSO2 executes under should be scoped to least privilege so a path traversal read cannot reach beyond what the application strictly needs. PR.DS-01 gap: configuration files, keystores, and credential stores at rest on the host filesystem were not protected against out-of-bound read access. |
| **DETECT** | DE.CM-01 (network monitoring), DE.AE-02 (event analysis) | Path traversal request patterns against WSO2 management and gateway interfaces should be a defined detection use case. Organizations without this monitoring in place could not have detected exploitation attempts even during the active-exploitation window CISA confirmed. |
| **RESPOND** | RS.MI-02 (incident mitigation) | Mitigation requires both patching and credential/key rotation. A response plan that stops at patching leaves previously exposed secrets valid. |
| **RECOVER** | RC.RP-01 (recovery plan execution) | Recovery planning for identity infrastructure should assume a compromised instance's configuration and key material cannot simply be restored from backup without rotation, per the BIA in 03_BIA.md. |

## 3.2 NIST SP 800-53 Rev 5 Control Mapping

| Control Family | Control ID | Control Name | Finding |
|---|---|---|---|
| Access Control | AC-3 | Access Enforcement | Path traversal defeats intended filesystem access boundaries; access enforcement at the application layer failed to constrain requests to the intended directory scope. |
| Access Control | AC-6 | Least Privilege | The service account/runtime identity WSO2 executes under should be evaluated for least-privilege scoping to limit what a filesystem-level compromise can reach. |
| Identification and Authentication | IA-2 | Identification and Authentication (Organizational Users) | Where exposed credential or key material allows token forgery, IA-2 controls are effectively bypassed downstream of the compromised instance, not defeated directly. |
| Identification and Authentication | IA-5 | Authenticator Management | Signing keys, client secrets, and bind credentials exposed through this flaw fall under authenticator management. Rotation of every potentially exposed authenticator is required, not optional, once exploitation is suspected. |
| System and Communications Protection | SC-28 | Protection of Information at Rest | Configuration files and key material stored unencrypted or under-protected on the host filesystem is the condition this flaw exploits. SC-28 controls (encryption, restricted storage) reduce the value of a successful traversal read. |
| System and Information Integrity | SI-2 | Flaw Remediation | The core control gap this case study addresses: timely patching against the vendor-fixed version within the KEV remediation window. |
| System and Information Integrity | SI-4 | System Monitoring | Detection of path traversal request patterns and anomalous authentication events depends on SI-4 coverage extending to the WSO2 application layer, not just network-perimeter monitoring. |
| Risk Assessment | RA-5 | Vulnerability Monitoring and Scanning | Vulnerability scanning coverage should include self-hosted middleware like WSO2, which is frequently missed by scanners tuned primarily for native cloud services. |
| Configuration Management | CM-6 | Configuration Settings | A hardened baseline configuration for WSO2 deployments (restricted filesystem permissions, minimized exposed interfaces) reduces the practical impact of this and similar flaws. |

## 3.3 ISO 27001:2022 Mapping

| Annex A Clause | Control | Finding |
|---|---|---|
| A.8.3 | Information Access Restriction | Path traversal is, by definition, a failure of information access restriction at the application layer. Access to configuration and credential files should be restricted regardless of application-layer input validation. |
| A.8.5 | Secure Authentication | The authentication mechanisms WSO2 Identity Server provides to other applications are only as trustworthy as the integrity of the signing keys and configuration this flaw can expose. |
| A.8.8 | Management of Technical Vulnerabilities | Direct control gap: this vulnerability was disclosed and exploited before organizations applied the vendor fix within the KEV window. |
| A.8.16 | Monitoring Activities | Detection of exploitation attempts against WSO2 interfaces depends on monitoring activities extending to this application layer specifically. |
| A.8.24 | Use of Cryptography | Token-signing and encryption keys exposed through this flaw are a direct failure mode for any cryptographic key management control that assumes keys at rest are inaccessible outside the application's intended scope. |

## 3.4 CIS Controls v8 Mapping

| CIS Control | Safeguard | Finding / Remediation |
|---|---|---|
| CIS Control 3 — Data Protection | 3.11 Encrypt Sensitive Data at Rest | Configuration files and key stores exposed by this flaw should be encrypted at rest wherever the underlying product supports it, limiting the value of a successful traversal read. |
| CIS Control 6 — Access Control Management | 6.8 Define and Maintain Role-Based Access Control | The WSO2 runtime identity's permissions should be defined and constrained under role-based access control rather than run with broad default filesystem access. |
| CIS Control 7 — Continuous Vulnerability Management | 7.3 / 7.4 Automated Operating System and Application Patch Management | Automated patch management coverage should explicitly include self-hosted middleware such as WSO2, not just OS-level patching. |
| CIS Control 8 — Audit Log Management | 8.5 Collect Detailed Audit Logs | Application-level audit logging on WSO2 instances should be collected and correlated centrally to support detection of path traversal attempts. |

## 3.5 Cloud Security Framework Mapping

| Framework | Reference | Finding |
|---|---|---|
| AWS Well-Architected — Security Pillar | SEC02 (Identity Management), SEC03 (Permissions Management) | Where WSO2 is deployed on AWS compute, the pillar's identity and permissions-management practices apply directly to scoping the instance's IAM role and the credentials it holds. |
| CIS Benchmarks (for the hosting cloud provider) | General hardening baseline | CIS cloud-provider benchmarks for the host OS and compute configuration reduce the blast radius of an application-layer compromise but do not substitute for patching the WSO2 application itself. |
| CSA Cloud Controls Matrix | IAM domain (IAM-02, IAM-04) | The Cloud Controls Matrix's identity and access management domain covers exactly the credential and key exposure risk this flaw creates. Organizations mapping to CCM should treat this as a direct IAM-domain finding. |
| FedRAMP (where applicable) | Continuous monitoring / vulnerability remediation timelines | Federal and FedRAMP-authorized environments running WSO2 in their authorization boundary must track this KEV entry against their own continuous monitoring and remediation timeline requirements, independent of the 3-day deadline that applies to federal civilian agencies directly. |

---

*Case Study CS-CLOUD-2026-09-001 — Blaise Kingko GRC Intelligence Program*
*Framework References: NIST CSF 2.0 | NIST SP 800-53 Rev 5 | ISO 27001:2022 | CIS Controls v8 | AWS Well-Architected*

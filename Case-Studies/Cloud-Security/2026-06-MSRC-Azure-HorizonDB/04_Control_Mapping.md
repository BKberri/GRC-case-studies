# Control Mapping Matrix
## Case: CVE-2026-48567 — Azure HorizonDB Elevation of Privilege Vulnerability

| Framework | Reference | Control Title | Application to This Case |
|---|---|---|---|
| NIST CSF 2.0 | PR.AA-03 | Users, services, and hardware are authenticated | Directly addresses the authentication-bypass weakness class (CWE-290) |
| NIST CSF 2.0 | DE.CM-03 | Personnel activity and technology usage are monitored | Drives retrospective log review for anomalous spoofed authentication |
| NIST CSF 2.0 | GV.SC-06 | Planning and due diligence are performed to reduce risks before entering supplier/vendor relationships and during the relationship | Frames the cloud-vendor risk-tracking dimension of this case |
| NIST 800-53 Rev 5 | IA-2 (Identification and Authentication) | Uniquely identify and authenticate users/processes | Core control mapped to the CWE-290 authentication-spoofing weakness |
| NIST 800-53 Rev 5 | AC-3 (Access Enforcement) | Enforce approved authorizations | Limits blast radius if authentication bypass is achieved |
| NIST 800-53 Rev 5 | SC-7 (Boundary Protection) | Monitor and control communications at external/internal boundaries | Network-layer mitigation pending platform patch confirmation |
| NIST 800-53 Rev 5 | CA-7 (Continuous Monitoring) | Ongoing assessment of security controls | Supports verification that Microsoft's fix has landed and holds |
| ISO 27001:2022 Annex A | A.5.15 | Access Control | Governs the broader access-management posture this flaw threatens |
| ISO 27001:2022 Annex A | A.8.5 | Secure Authentication | Direct mapping to the authentication-bypass weakness |
| ISO 27001:2022 Annex A | A.5.23 | Information Security for Use of Cloud Services | Frames vendor (Microsoft) accountability and verification requirements |
| CIS Controls v8 | Control 6 | Access Control Management | Drives Entra ID enforcement and least-privilege review |
| CIS Controls v8 | Control 13 | Network Monitoring and Defense | Supports anomaly detection in HorizonDB access patterns |
| CIS Controls v8 | Control 3 | Data Protection | Frames data-exposure risk if bypass succeeds |

### Mapping Notes
- This case is a strong candidate for the **third-party / cloud-supply-chain risk register** (GV.SC-06) in addition to the standard technical risk register — it demonstrates how a vendor-side control-plane flaw becomes an organizational risk requiring independent verification, not blind trust in vendor remediation claims.
- Recommend using this case as evidence in the next vendor risk assessment cycle to demonstrate active monitoring of cloud sub-processor security advisories (a common SOC 2 / ISO 27001 control-test inquiry point).

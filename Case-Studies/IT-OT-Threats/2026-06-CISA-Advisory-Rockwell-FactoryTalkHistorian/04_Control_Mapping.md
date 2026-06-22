# Control Mapping — Rockwell FactoryTalk Historian SE Multiple Vulnerabilities

| Framework | Control/Clause | Application to This Case |
|---|---|---|
| **NIST CSF 2.0** | PR.PS-04 — Software maintained/updated | Apply Rockwell vendor patches for all three CVEs |
| **NIST CSF 2.0** | PR.AA-01 — Identities/credentials managed | Rotate hardcoded/default credentials (CVE-2025-44019) |
| **NIST CSF 2.0** | DE.CM-09 — Computing hardware/software monitored | Monitor historian server for anomalous deserialization/RCE indicators |
| **NIST 800-53 Rev 5** | SI-2 — Flaw Remediation | Patch tracked to closure across all three CVEs |
| **NIST 800-53 Rev 5** | IA-5 — Authenticator Management | Address hardcoded credential exposure |
| **NIST 800-53 Rev 5** | AC-3 — Access Enforcement | Remediate improper access control (CVE-2025-36539) |
| **IEC 62443** | SR 1.1 — Human user identification/authentication | Credential management remediation |
| **IEC 62443** | SR 3.1 — Communication integrity | Network segmentation between IT and OT zones |
| **IEC 62443** | SR 7.6 — Network/security configuration settings | Harden historian server configuration |
| **ISO/IEC 27001:2022** | A.8.8 — Management of Technical Vulnerabilities | Vulnerability lifecycle tracked from advisory to patch confirmation |
| **ISO/IEC 27001:2022** | A.8.5 — Secure Authentication | Eliminate hardcoded credential risk |

## Gap Assessment
Verify network segmentation (IT/OT zone boundary firewalling) is actually enforced around FactoryTalk Historian deployments — this is the primary compensating control reducing exploitability pending patch deployment, and should not be assumed without verification.

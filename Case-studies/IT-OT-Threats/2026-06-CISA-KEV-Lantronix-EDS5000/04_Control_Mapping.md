# Control Mapping — CVE-2025-67038 (Lantronix EDS5000)

| Framework | Control/Clause | Application to This Case |
|---|---|---|
| **NIST CSF 2.0** | PR.PS-04 — Software is maintained, replaced, removed | Upgrade to firmware 2.2.0.0R1 |
| **NIST CSF 2.0** | PR.IR-01 — Network integrity protected | Remove device from direct internet exposure; isolate to OOB management network |
| **NIST CSF 2.0** | DE.CM-09 — Computing hardware/software monitored | Monitor device logs for anomalous login/command patterns |
| **NIST 800-53 Rev 5** | SI-2 — Flaw Remediation | Patch tracked to closure across full device fleet |
| **NIST 800-53 Rev 5** | SI-10 — Information Input Validation | Root cause addressed by vendor patch (input sanitization on username field) |
| **NIST 800-53 Rev 5** | SC-7 — Boundary Protection | Network segmentation between device management interface and general IP network |
| **ISO/IEC 27001:2022** | A.8.8 — Management of Technical Vulnerabilities | Vulnerability lifecycle tracked from KEV listing to patch confirmation |
| **ISO/IEC 27001:2022** | A.8.9 — Configuration Management | Device inventory and firmware baseline established/verified |
| **CIS Controls v8** | Control 7 — Continuous Vulnerability Management | Patch deployment verification across device fleet |
| **CIS Controls v8** | Control 4 — Secure Configuration of Enterprise Assets | Remove unnecessary internet exposure on management interfaces |
| **IEC 62443** | Zone/Conduit Model | Re-validate zone boundary integrity for any IT/OT conduit traversing this device class |

## Gap Assessment
Organizations without a complete inventory of serial-to-IP gateway devices (often deployed by OT/facilities teams outside standard IT asset management) are at elevated risk of missing this patch. Recommend extending enterprise asset inventory (CIS Control 1) to explicitly capture OT-boundary gateway devices.

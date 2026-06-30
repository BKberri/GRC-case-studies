# Control Mapping — CVE-2026-12569 (PTC Windchill/FlexPLM)

| Framework | Control/Clause | Application to This Case |
|---|---|---|
| **NIST CSF 2.0** | PR.PS-04 — Software is maintained, replaced, removed | Apply PTC patch for CVE-2026-12569 |
| **NIST CSF 2.0** | PR.DS-01 — Data-at-rest protected | Validate encryption/access controls on stored design data |
| **NIST CSF 2.0** | DE.CM-01 — Networks monitored | Monitor for anomalous access to PLM data repositories |
| **NIST 800-53 Rev 5** | SI-2 — Flaw Remediation | Patch tracked to closure |
| **NIST 800-53 Rev 5** | SC-7 — Boundary Protection | Remove direct internet exposure pending patch |
| **NIST 800-53 Rev 5** | AC-3 — Access Enforcement | Review and restrict supplier/partner access scopes |
| **ISO/IEC 27001:2022** | A.8.8 — Management of Technical Vulnerabilities | Vulnerability tracked from KEV listing to closure |
| **ISO/IEC 27001:2022** | A.8.12 — Data Leakage Prevention | Assess DLP coverage for PLM data exfiltration paths |
| **CMMC 2.0 / DFARS 252.204-7012** | Incident Reporting | Confirm reporting obligations if CUI exposure is found |
| **CIS Controls v8** | Control 3 — Data Protection | Inventory and classify data stored in PLM platform |

## Gap Assessment
Organizations should confirm whether their Windchill/FlexPLM deployment is internet-facing by design or by misconfiguration — PLM platforms are frequently intended for internal/VPN-only access, and direct internet exposure may itself represent an architectural control gap independent of this specific CVE.

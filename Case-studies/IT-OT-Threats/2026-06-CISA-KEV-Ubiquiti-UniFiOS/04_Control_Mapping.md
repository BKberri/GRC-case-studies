# Control Mapping — CVE-2026-34908 / -34909 / -34910 (Ubiquiti UniFi OS)

| Framework | Control/Clause | Application to This Case |
|---|---|---|
| **NIST CSF 2.0** | PR.AA-05 — Access permissions managed | Restrict management interface access; enforce least-privilege admin accounts |
| **NIST CSF 2.0** | PR.PS-04 — Software is maintained, replaced, removed | Upgrade to UniFi OS Server v5.0.8+ |
| **NIST CSF 2.0** | DE.CM-01 — Networks monitored | Monitor for anomalous outbound traffic indicative of botnet conscription |
| **NIST 800-53 Rev 5** | AC-3 — Access Enforcement | Address root cause of access-control bypass via patch |
| **NIST 800-53 Rev 5** | SI-2 — Flaw Remediation | Patch tracked to closure across full device fleet |
| **NIST 800-53 Rev 5** | SC-7 — Boundary Protection | Remove direct internet exposure on management interfaces |
| **ISO/IEC 27001:2022** | A.8.8 — Management of Technical Vulnerabilities | Vulnerability lifecycle tracked from KEV listing to patch confirmation |
| **ISO/IEC 27001:2022** | A.8.16 — Monitoring Activities | Network and device log monitoring for compromise indicators |
| **CIS Controls v8** | Control 7 — Continuous Vulnerability Management | Patch deployment verification |
| **CIS Controls v8** | Control 13 — Network Monitoring and Defense | Detect botnet C2 traffic / anomalous device behavior |

## Gap Assessment
The roughly one-month gap between vendor patch availability (May 21) and KEV listing/active exploitation (June 23) indicates a patch-deployment lag, not a detection failure. Recommend establishing a defined SLA for applying vendor security patches to network infrastructure devices, independent of KEV listing status.

# Control Mapping — CVE-2026-20384 (Cisco Unified Communications Manager)

| Framework | Control/Clause | Application to This Case |
|---|---|---|
| **NIST CSF 2.0** | PR.AA-01 — Identities and credentials managed | Remove/rotate static credential; eliminate hardcoded authenticators |
| **NIST CSF 2.0** | PR.PS-04 — Software is maintained, replaced, removed | Apply Cisco's security patch |
| **NIST CSF 2.0** | DE.CM-01 — Networks monitored | Monitor authentication logs for use of affected credential |
| **NIST 800-53 Rev 5** | IA-5 — Authenticator Management | Audit for any remaining default/static credentials across UC platform |
| **NIST 800-53 Rev 5** | AC-6 — Least Privilege | Review privilege level associated with the static account |
| **NIST 800-53 Rev 5** | SI-2 — Flaw Remediation | Patch tracked to closure |
| **ISO/IEC 27001:2022** | A.8.5 — Secure Authentication | Eliminate static/default credential exposure |
| **ISO/IEC 27001:2022** | A.8.8 — Management of Technical Vulnerabilities | Vulnerability lifecycle tracked from KEV listing to closure |
| **CIS Controls v8** | Control 5 — Account Management | Inventory and remove default/static accounts platform-wide |

## Gap Assessment
Recommend a broader audit of all Cisco UC platform components (Unity Connection, Expressway, IM&P) for similar undocumented/static credential patterns, given that vendor-introduced static credentials are frequently found across product families sharing common codebases.

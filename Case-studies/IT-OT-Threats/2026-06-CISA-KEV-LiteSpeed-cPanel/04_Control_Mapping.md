# Control Mapping — CVE-2026-54420 (LiteSpeed cPanel Plugin)

| Framework | Control/Clause | Application to This Case |
|---|---|---|
| **NIST CSF 2.0** | PR.PS-04 — Software is maintained, replaced, removed | Upgrade to patched LiteSpeed WHM Plugin v5.3.2.1+ |
| **NIST CSF 2.0** | DE.CM-09 — Computing hardware/software monitored | Monitor for anomalous symlink creation and FTP/web-shell activity |
| **NIST CSF 2.0** | PR.AA-05 — Access permissions/authorizations managed | Review FTP and shell access scope on shared hosting accounts |
| **NIST 800-53 Rev 5** | SI-2 — Flaw Remediation | Patch tracked to closure; overdue status documented |
| **NIST 800-53 Rev 5** | CM-6 — Configuration Settings | Validate CageFS/CloudLinux configuration post-patch |
| **NIST 800-53 Rev 5** | AC-6 — Least Privilege | Restrict FTP/web-shell access to minimum necessary scope |
| **ISO/IEC 27001:2022** | A.8.8 — Management of Technical Vulnerabilities | Vulnerability lifecycle tracked from KEV listing to patch confirmation |
| **ISO/IEC 27001:2022** | A.8.9 — Configuration Management | Tenant isolation configuration reviewed post-patch |
| **CIS Controls v8** | Control 7.4 — Manage OS Vulnerabilities | Patch deployment verification across all affected hosts |
| **CIS Controls v8** | Control 4 — Secure Configuration of Enterprise Assets | Harden shared hosting platform baseline |

## Gap Assessment
The standard compensating control for this risk class (CloudLinux/CageFS tenant isolation) is the specific mechanism defeated by this vulnerability. There is no substitute compensating control beyond patching — this should be flagged in any control-effectiveness review as a case where the primary architectural control failed.

# Control Mapping — Joomla! Extension Ecosystem Mass File-Upload RCE

| Framework | Control/Clause | Application to This Case |
|---|---|---|
| **NIST CSF 2.0** | PR.PS-04 — Software/firmware kept up to date | Patch each affected extension to its fixed version |
| **NIST CSF 2.0** | DE.CM-09 — Computing hardware/software monitored | Monitor for unauthorized file uploads / new files in web roots |
| **NIST CSF 2.0** | PR.IR-01 — Network integrity protected | WAF rules on extension upload endpoints as compensating control |
| **NIST 800-53 Rev 5** | SI-2 — Flaw Remediation | Patch tracking across all four extensions |
| **NIST 800-53 Rev 5** | SI-3 — Malicious Code Protection | Web-shell detection/removal |
| **NIST 800-53 Rev 5** | SI-10 — Information Input Validation | Root-cause control gap common to all four CVEs |
| **NIST 800-53 Rev 5** | SC-7 — Boundary Protection | Restrict/monitor upload-endpoint access pending patch |
| **ISO/IEC 27001:2022** | A.8.8 — Management of technical vulnerabilities | Extension-level vulnerability management, not just core-CMS patching |
| **ISO/IEC 27001:2022** | A.8.28 — Secure coding | Vendor-side root cause; relevant if any of these extensions is customized in-house |
| **CIS Controls v8** | Control 7 (7.4) — Manage Application Vulnerabilities | Patch deployment tracking across all affected extensions |
| **CIS Controls v8** | Control 16 — Application Software Security | File-upload validation review as a standing control, not a one-time fix |

## Gap Assessment
Most organizations' vulnerability management programs track core CMS platform versions but have less mature visibility into the patch status of individual third-party extensions/plugins. This four-CVE-in-one-week pattern is a strong argument for extending formal vulnerability management scope to cover installed extensions with the same rigor applied to the core platform — an extension inventory is a prerequisite control that several of the organizations affected by these four CVEs likely lacked.

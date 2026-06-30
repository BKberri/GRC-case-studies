# Control Mapping Matrix
## Case: CVE-2026-45247 — Mirasvit Full Page Cache Warmer Unauthenticated RCE (Magento/Adobe Commerce)

| Framework | Reference | Control Title | Application to This Case |
|---|---|---|---|
| NIST CSF 2.0 | PR.PS-02 | Software is maintained, replaced, and removed commensurate with risk | Drives emergency extension patching |
| NIST CSF 2.0 | DE.CM-01 | Networks and network services are monitored to find anomalous events | Detects exploitation attempts/web-shell traffic |
| NIST CSF 2.0 | RS.AN-03 | Analysis is performed to establish what has taken place during an incident | Forensic web-shell sweep and IOC analysis |
| NIST 800-53 Rev 5 | SI-2 (Flaw Remediation) | Identify, report, correct system flaws | Core remediation control for the CVE |
| NIST 800-53 Rev 5 | SI-3 (Malicious Code Protection) | Implement malicious code protection | Web-shell detection and removal |
| NIST 800-53 Rev 5 | SI-10 (Information Input Validation) | Validate information inputs | Root-cause control for the deserialization weakness class |
| NIST 800-53 Rev 5 | IR-4 (Incident Handling) | Implement incident-handling capability | Governs response if compromise indicators are found |
| ISO 27001:2022 Annex A | A.8.8 | Management of Technical Vulnerabilities | Governs vulnerability-to-patch lifecycle |
| ISO 27001:2022 Annex A | A.8.28 | Secure Coding | Addresses root cause (insecure deserialization) |
| ISO 27001:2022 Annex A | A.8.16 | Monitoring Activities | Supports detection of exploitation attempts |
| CIS Controls v8 | Control 16 / Safeguard 16.13 | Application Software Security / Conduct Application Penetration Testing | Identifies similar deserialization weaknesses proactively |
| CIS Controls v8 | Control 7 | Continuous Vulnerability Management | Drives extension-version inventory and patch cadence |
| CIS Controls v8 | Control 17 | Incident Response Management | Governs forensic response to active exploitation |
| PCI-DSS v4.0 | Req. 6.3.3, 11.3 | Patch critical vulnerabilities within defined timeframes; perform vulnerability scanning | PCI-specific obligation given payment-card scope |

### Mapping Notes
- This case directly intersects **PCI-DSS v4.0** in addition to the standard IT/OT framework stack — a reminder that e-commerce findings carry payment-industry compliance obligations beyond NIST/ISO/CIS mapping. Recommend cross-referencing with the Financial-Services framework track for any QSA evidence requests.
- Given confirmed active exploitation, this finding should be flagged for the next incident-response tabletop exercise as a realistic injected scenario (web-shell discovery → PCI forensic engagement → card-brand notification chain).

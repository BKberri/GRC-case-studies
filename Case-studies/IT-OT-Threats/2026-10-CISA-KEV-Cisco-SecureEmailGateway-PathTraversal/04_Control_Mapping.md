# Control Mapping, CVE-2026-76519 (Cisco Secure Email Gateway Path Traversal)

**Case ID:** 2026-10-CISA-KEV-Cisco-SecureEmailGateway-PathTraversal

## NIST CSF 2.0

| Function | Subcategory | Application |
|---|---|---|
| PROTECT | PR.PS-06, Secure software is included in the development and operation of systems | Root cause, path-traversal flaw in the appliance's own attachment-scanning feature |
| DETECT | DE.CM-01, Networks and network services are monitored | `grep "System Security" system_logs` check across all appliances for prior-compromise indicators |
| RESPOND | RS.MI-02, Incidents are mitigated | Apply Content Scanner Tools 25.3.0.5525+ immediately; escalate to Cisco TAC for any appliance with forensic indicators |

## NIST SP 800-53 Rev 5

| Control | Title | Application |
|---|---|---|
| SI-10 | Information Input Validation | Root cause, appliance fails to sanitize attachment-derived file paths |
| SI-2 | Flaw Remediation | Apply Content Scanner Tools and AsyncOS fixed builds per affected branch |
| SC-7 | Boundary Protection | Gateway is the enforced inbound-mail boundary; compromise defeats the control's purpose |
| IR-4 | Incident Handling | Log review for pre-patch exploitation given confirmed active, pre-disclosure attacks |

## ISO/IEC 27001:2022 Annex A

| Control | Title | Application |
|---|---|---|
| A.8.8 | Management of Technical Vulnerabilities | Vulnerability identified via CISA KEV; tracked to remediation |
| A.8.26 | Application Security Requirements | Input-validation failure in the appliance's attachment-handling logic |
| A.8.16 | Monitoring Activities | Appliance log review for prior-compromise indicators |

## CIS Controls v8

| Control | Safeguard | Application |
|---|---|---|
| Control 16 | 16.1, Secure Application Development Process | Addresses the class of defect (path traversal in attachment processing) |
| Control 7 | 7.4, Vulnerability Remediation Process | Patch tracking and immediate deployment, no workaround available |
| Control 8 | 8.5, Collect Detailed Audit Logs | Supports the forensic log review recommended for exposed appliances |

## Compensating Control Note

Because no workaround exists and disabling the scanning feature removes a separate security control, this case's compensating-control posture is unusually thin; SI-2/A.8.8 patch application is the primary and effectively only enforceable control until the fixed builds are deployed.

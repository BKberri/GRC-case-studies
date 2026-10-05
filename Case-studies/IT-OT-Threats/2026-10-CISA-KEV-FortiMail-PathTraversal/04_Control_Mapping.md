# Control Mapping, CVE-2026-104286 (FortiMail Path Traversal)

**Case ID:** 2026-10-CISA-KEV-FortiMail-PathTraversal

## NIST CSF 2.0

| Function | Subcategory | Application |
|---|---|---|
| PROTECT | PR.PS-06, Secure software is included in the development and operation of systems | Vendor delayed patch release exposes a gap this control is meant to prevent via secure SDLC/input validation |
| DETECT | DE.CM-01, Networks and network services are monitored | Monitor for anomalous outbound connections or unexpected file-write activity on the gateway |
| RESPOND | RS.MI-02, Incidents are mitigated | Apply interim workaround (disable IBE, isolate management interface) pending vendor patch |

## NIST SP 800-53 Rev 5

| Control | Title | Application |
|---|---|---|
| SI-10 | Information Input Validation | Root cause, gateway fails to validate/sanitize path input, permitting traversal |
| SI-2 | Flaw Remediation | Track vendor patch release (8.0.2/7.6.7/7.4.9) and apply on availability |
| SC-7 | Boundary Protection | Restrict management-interface exposure to an out-of-band network as interim compensating control |
| IR-4 | Incident Handling | Treat any pre-workaround exposure window as a potential incident requiring forensic review |

## ISO/IEC 27001:2022 Annex A

| Control | Title | Application |
|---|---|---|
| A.8.8 | Management of Technical Vulnerabilities | Vulnerability identified via CISA KEV; tracked to remediation |
| A.8.26 | Application Security Requirements | Input-validation failure in gateway's HTTP handling |
| A.8.20 | Networks Security | Management-interface network segmentation as compensating control |

## CIS Controls v8

| Control | Safeguard | Application |
|---|---|---|
| Control 16 | 16.1, Secure Application Development Process | Addresses the class of defect (unauthenticated path traversal) |
| Control 12 | 12.2, Secure Network Architecture | Management-interface isolation |
| Control 7 | 7.4, Vulnerability Remediation Process | Patch tracking once Fortinet ships fixed builds |

## Compensating Control Note

Because no vendor patch exists at the time of this assessment, the above control mapping intentionally emphasizes SC-7/A.8.20/CIS 12.2 (network isolation) as the primary enforceable control until SI-2/A.8.8 (patch-based remediation) becomes available.

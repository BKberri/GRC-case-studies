# Control Mapping, CVE-2026-76504 (Cisco SD-WAN Manager Auth Bypass)

**Case ID:** 2026-10-CISA-KEV-Cisco-SDWAN-HexEncodingBypass

## NIST CSF 2.0

| Function | Subcategory | Application |
|---|---|---|
| PROTECT | PR.AA-05, Access permissions and authorizations are managed | Root cause, authentication filter fails to normalize hex-encoded input before enforcement |
| DETECT | DE.CM-01, Networks and network services are monitored | Monitor service-proxy and vManage server logs for encoded `j_security_check` request patterns |
| RESPOND | RS.MI-02, Incidents are mitigated | Mandatory upgrade (no workaround); TAC-assisted compromise assessment |

## NIST SP 800-53 Rev 5

| Control | Title | Application |
|---|---|---|
| IA-2 | Identification and Authentication | Authentication bypass defeats the control this requirement is meant to enforce |
| SI-10 | Information Input Validation | Hex-encoded URI input is not normalized before authentication-filter evaluation |
| AC-3 | Access Enforcement | Bypass grants unauthorized admin-level access enforcement failure |
| IR-4 | Incident Handling | Required given confirmed pre-disclosure active exploitation |

## ISO/IEC 27001:2022 Annex A

| Control | Title | Application |
|---|---|---|
| A.8.5 | Secure Authentication | Directly implicated, authentication mechanism bypassed via encoding trick |
| A.8.26 | Application Security Requirements | Input-handling defect in the web authentication layer |
| A.8.9 | Configuration Management | Baseline configuration audit recommended post-upgrade |

## CIS Controls v8

| Control | Safeguard | Application |
|---|---|---|
| Control 6 | 6.1, Establish an Access Granting Process | Authentication bypass undermines access-granting assurance |
| Control 12 | 12.2, Establish and Maintain a Secure Network Architecture | Management-plane segmentation as defense-in-depth |
| Control 7 | 7.4, Vulnerability Remediation Process | Upgrade tracking to fixed releases |

## Compensating Control Note

No workaround exists for this vulnerability, the control mapping above is oriented entirely around (1) completing the mandatory upgrade and (2) the forensic/detection controls (IR-4, DE.CM-01) needed to determine whether exploitation occurred during the exposure window, since patching alone does not retroactively remediate a prior compromise.

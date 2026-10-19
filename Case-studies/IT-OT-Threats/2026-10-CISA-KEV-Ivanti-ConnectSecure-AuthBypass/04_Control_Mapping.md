# Control Mapping, CVE-2026-104935 (Ivanti Connect Secure Authentication Bypass)

**Case ID:** 2026-10-CISA-KEV-Ivanti-ConnectSecure-AuthBypass

## NIST CSF 2.0

| Function | Subcategory | Application |
|---|---|---|
| PROTECT | PR.AA-02, Identities and credentials are issued, managed, verified, revoked, and audited | Root-cause gap, the gateway's authentication/trust-verification path can be spoofed |
| DETECT | DE.CM-01, Networks and network services are monitored | Monitor for anomalous VPN authentication patterns and command execution on the appliance |
| RESPOND | RS.MI-02, Incidents are mitigated | Emergency patch deployment and compromise assessment against Volexity's published indicators |

## NIST SP 800-53 Rev 5

| Control | Title | Application |
|---|---|---|
| IA-2 | Identification and Authentication (Organizational Users) | Root cause, authentication bypass by spoofing |
| SI-2 | Flaw Remediation | Apply vendor patch (25.1.1.2 / 25.1.3.0-25.1.3.1 / 22.8R2.5) outside normal cycle |
| SC-7 | Boundary Protection | Gateway is the enforced network boundary; compromise here defeats the control's purpose |
| IR-4 | Incident Handling | Treat any pre-2026-10-13 exposure as a potential incident requiring forensic review |

## ISO/IEC 27001:2022 Annex A

| Control | Title | Application |
|---|---|---|
| A.8.5 | Secure Authentication | Directly implicated, authentication logic defeated by spoofing |
| A.8.8 | Management of Technical Vulnerabilities | Vulnerability identified via CISA KEV; tracked to remediation |
| A.5.24 | Information Security Incident Management Planning | Applies to the compromise-assessment workstream given confirmed pre-disclosure exploitation |

## CIS Controls v8

| Control | Safeguard | Application |
|---|---|---|
| Control 7 | 7.4, Vulnerability Remediation Process | Emergency patch tracking and deployment |
| Control 12 | 12.2, Secure Network Architecture | Remote-access gateway segmentation and monitoring |
| Control 13 | 13.1, Centralize Security Event Alerting | Detection of anomalous gateway authentication/command activity |

## Compensating Control Note

Because the observed attack chain also used a second, still-unpatched privilege-escalation flaw, control mapping for this case extends beyond SI-2/A.8.8 patch application to include IR-4/A.5.24 compromise-assessment activity; a patch confirms the authentication-bypass vector is closed but does not, by itself, confirm the appliance is free of prior attacker access.

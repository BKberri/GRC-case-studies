# Control Mapping, CVE-2026-102764 (BeyondTrust Remote Support Authentication Bypass)

**Case ID:** 2026-10-CISA-KEV-BeyondTrust-RemoteSupport-AuthBypass

## NIST CSF 2.0

| Function | Subcategory | Application |
|---|---|---|
| PROTECT | PR.AA-02, Identities and credentials are issued, managed, verified, revoked, and audited | Root cause, authentication bypass on a privileged remote-access tool |
| DETECT | DE.CM-01, Networks and network services are monitored | Gap exploited, roughly seven weeks of undetected activity, including log wiping |
| RESPOND | RS.MI-02, Incidents are mitigated | Immediate patching plus forensic review given confirmed nation-state compromise |
| RECOVER | RC.CO-01, Recovery communications | Client/stakeholder notification planning given managed-service/MSP blast-radius considerations |

## NIST SP 800-53 Rev 5

| Control | Title | Application |
|---|---|---|
| IA-2 | Identification and Authentication (Organizational Users) | Root cause, authentication bypass |
| AC-6 | Least Privilege | Observed SUID-based root escalation underscores the need for least-privilege enforcement on support tooling |
| SI-2 | Flaw Remediation | Apply vendor patch to all self-hosted instances immediately |
| IR-4 | Incident Handling | Nation-state attribution and confirmed log wiping require formal incident-response engagement |
| AU-6 | Audit Record Review, Analysis, and Reporting | Compromised due to log wiping; audit-log integrity protections (e.g., off-box log forwarding) are a key gap this incident exposes |

## ISO/IEC 27001:2022 Annex A

| Control | Title | Application |
|---|---|---|
| A.8.5 | Secure Authentication | Directly implicated, authentication bypass |
| A.8.8 | Management of Technical Vulnerabilities | Vulnerability identified via CISA KEV; tracked to remediation |
| A.5.24 | Information Security Incident Management Planning | Applies given confirmed nation-state compromise and necessary forensic response |
| A.8.15 | Logging | Attacker log-wiping underscores the need for tamper-resistant, off-box log retention |

## CIS Controls v8

| Control | Safeguard | Application |
|---|---|---|
| Control 5 | 5.1, Establish and Maintain an Inventory of Accounts | Credential-compromise review for any administrator account used on the appliance |
| Control 6 | 6.8, Define and Maintain Role-Based Access Control | Least-privilege hardening for remote-support tooling going forward |
| Control 8 | 8.9, Centralize Audit Logs | Directly responsive to the attacker's demonstrated log-wiping technique |

## Compensating Control Note

Because the attacker demonstrably wiped on-appliance logs, this case's control mapping places unusual weight on AU-6/A.8.15/CIS 8.9 (centralized, off-box audit logging) as a forward-looking control; had logs been forwarded to a separate, tamper-resistant system, the roughly seven-week detection gap may have been substantially shorter.

# Control Mapping
## SharePoint Server Deserialization RCE with Machine Key Theft (CVE-2026-50522)

## Applicable Frameworks
Standard IT/Cloud track: NIST CSF 2.0, NIST 800-53 Rev 5, ISO 27001, CIS Controls v8 — this is an on-premises enterprise application platform finding with credential/authenticator-management implications that go beyond standard patch management.

## Control Mapping Table
| Framework | Control ID | Control Name | Applicability | Gap / Status |
|---|---|---|---|---|
| NIST CSF 2.0 | PR.PS-04 | Software integrity mechanisms verified | Patch application to SharePoint Server | Addressed (once applied) |
| NIST CSF 2.0 | RS.AN-03 | Analysis performed to establish incident scope | Determining whether machine keys were stolen prior to patching | Gap (requires forensic review) |
| NIST 800-53 Rev 5 | SI-2 | Flaw Remediation | Patch closes the initial RCE vector | Addressed (once applied) — but insufficient alone |
| NIST 800-53 Rev 5 | SI-3 | Malicious Code Protection | Detection of web shells or malicious artifacts planted during exploitation | Gap (requires active sweep) |
| NIST 800-53 Rev 5 | SI-10 | Information Input Validation | Root-cause deserialization-handling gap (vendor-side) | N/A (vendor patch addresses) |
| NIST 800-53 Rev 5 | IA-5 | Authenticator Management | Machine key rotation — the control this case specifically highlights as commonly missed | Gap (unless explicitly performed) |
| ISO 27001 | A.8.8 | Management of technical vulnerabilities | Vulnerability/patch management for on-premises enterprise applications | Partial |
| ISO 27001 | A.8.28 | Secure coding | Root-cause practice gap (vendor-side) | N/A |
| CIS Controls v8 | Control 7 (7.4) | Continuous Vulnerability Management | Rapid patch cycle for internet-facing enterprise applications | Partial |
| CIS Controls v8 | Control 16 | Application Software Security | WAF/RDS-equivalent protections on SharePoint sign-in endpoints | Gap |

## Control Narrative
This case demonstrates a control mapping gap that is easy to miss: SI-2 (Flaw Remediation) is fully satisfied by applying Microsoft's patch, but that alone does not satisfy IA-5 (Authenticator Management), which requires rotating any authenticator material (here, IIS machine keys) that may have been compromised during the exploitation window. Organizations that treat this finding as closed once SI-2 is satisfied are leaving IA-5 unaddressed — precisely the gap that lets forged authentication tokens survive patching. The correct sequencing, per control theory and per watchTowr's specific technical guidance, is: SI-3 (sweep for and remove malicious artifacts / machine-key-harvesting tools) before IA-5 (rotate keys) — rotating first while a harvesting tool remains active simply hands the attacker the new keys too. A mature control environment for enterprise on-premises applications treats authenticator rotation as a standing post-incident step whenever a vulnerability's exploitation pattern includes credential or key material theft, not as an optional follow-up to patching.

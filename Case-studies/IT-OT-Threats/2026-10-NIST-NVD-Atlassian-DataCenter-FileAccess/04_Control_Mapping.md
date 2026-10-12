# Control Mapping, CVE-2026-21589 (Atlassian Data Center File Access)

**Case ID:** 2026-10-NIST-NVD-Atlassian-DataCenter-FileAccess

## NIST CSF 2.0

| Function | Subcategory | Application |
|---|---|---|
| PROTECT | PR.PS-02, Software is maintained, replaced, and patched | Apply Atlassian's 2026-10-05 patch across all eight affected products |
| PROTECT | PR.AA-05, Access permissions and authorizations are managed | Restrict Crowd network reachability with an IP allow-list as a compensating control |
| DETECT | DE.CM-01, Networks and network services are monitored | Monitor for the published scanning IOCs and Nuclei-template scanning patterns |

## NIST SP 800-53 Rev 5

| Control | Title | Application |
|---|---|---|
| SI-2 | Flaw Remediation | Apply vendor patch immediately across all affected instances |
| AC-3 | Access Enforcement | Root cause, the shared web-resource library fails to enforce intended path restrictions |
| IA-5 | Authenticator Management | Plaintext storage of Crowd credentials in `crowd.properties` is the escalation enabler; rotate exposed credentials |
| SC-7 | Boundary Protection | IP allow-list for Crowd reachability pending full patch confirmation |

## ISO/IEC 27001:2022 Annex A

| Control | Title | Application |
|---|---|---|
| A.8.8 | Management of Technical Vulnerabilities | Vulnerability identified via vendor disclosure; tracked to remediation |
| A.8.24 | Use of Cryptography | Cleartext credential storage in `crowd.properties` is a control gap independent of this specific CVE |
| A.8.3 | Information Access Restriction | Crowd API access restriction as compensating control |

## CIS Controls v8

| Control | Safeguard | Application |
|---|---|---|
| Control 7 | 7.4, Vulnerability Remediation Process | Patch deployment across all eight products |
| Control 3 | 3.11, Encrypt Sensitive Data at Rest | Addresses the underlying cleartext-credential storage issue |
| Control 6 | 6.8, Define and Maintain Role-Based Access Control | Review Crowd-granted administrative roles following any suspected exposure |

## Compensating Control Note

Because a vendor patch was available at disclosure, the mapping here emphasizes SI-2/CIS 7.4 (patch deployment speed) as the primary control, with IA-5/A.8.24 (credential hygiene) as the secondary control addressing the specific Crowd-integration escalation path.

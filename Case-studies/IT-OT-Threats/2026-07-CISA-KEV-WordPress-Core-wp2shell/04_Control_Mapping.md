# Control Mapping
## WordPress Core "wp2shell" Unauthenticated RCE Chain (CVE-2026-63030 + CVE-2026-60137)

## Applicable Frameworks
Standard IT/Cloud track applies: NIST CSF 2.0, NIST 800-53 Rev 5, ISO 27001, and CIS Controls v8, given this is a public-facing web application vulnerability with no OT or AI-specific dimension.

## Control Mapping Table
| Framework | Control ID | Control Name | Applicability | Gap / Status |
|---|---|---|---|---|
| NIST CSF 2.0 | PR.PS-04 | Software integrity mechanisms verified | WordPress Core's own auto-update mechanism is the primary control; disabled in change-controlled environments | Partial |
| NIST CSF 2.0 | DE.CM-09 | Computing hardware/software monitored | Detects webshell installation, rogue admin creation, and anomalous REST API queries post-compromise | Gap (absent WAF/monitoring) |
| NIST 800-53 Rev 5 | SI-2 | Flaw Remediation | Patch to 7.0.2/6.9.5/6.8.6 | Addressed (once applied) |
| NIST 800-53 Rev 5 | SI-10 | Information Input Validation | Root-cause control for the SQL injection (CVE-2026-60137) | Gap (pre-patch) |
| NIST 800-53 Rev 5 | AC-3 | Access Enforcement | REST API route confusion bypassed intended access boundaries | Gap (pre-patch) |
| ISO 27001 | A.8.8 | Management of technical vulnerabilities | Vulnerability/patch management process for public-facing CMS | Partial |
| ISO 27001 | A.8.28 | Secure coding | Root-cause practice gap reflected in the underlying CVEs | N/A (vendor-side) |
| CIS Controls v8 | Control 7 | Continuous Vulnerability Management | WordPress-specific asset inventory and patch cadence | Gap |
| CIS Controls v8 | Control 16 | Application Software Security | WAF rule coverage for REST API abuse patterns | Gap |

## Control Narrative
The preventive control that would have fully closed this exposure is the vendor patch itself (SI-2) — WordPress pushed automatic updates to supported installations, which is why the ~81.6% observed patch rate reflects organizations that either allow auto-updates or responded quickly manually. For the remaining ~18%, the compensating preventive control is a WAF rule blocking abuse of the vulnerable REST API batch route, and the compensating detective control is monitoring for the specific IOCs published by Wordfence, Wiz, and SANS ISC (webshells under `/wp-content/cache/`, malicious plugin installations, anomalous `admin-ajax.php` requests targeting `wp-config.php`). A mature control environment for public-facing CMS platforms treats "just the website" with the same SI-2 patch-cadence discipline as core business systems, maintains WAF coverage as a standing compensating control independent of patch status, and runs periodic file-integrity monitoring against the web root to catch webshells that survive a later patch.

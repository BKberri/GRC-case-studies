# Plan of Action & Milestones (POA&M)
## WordPress Core "wp2shell" Unauthenticated RCE Chain (CVE-2026-63030 + CVE-2026-60137)
**Date Opened:** 2026-07-27 | **Source:** CISA KEV | **Risk Rating:** Critical | **Target Closure:** 2026-08-10

## POA&M Table
| Item ID | Weakness / Finding | Affected System | Control Reference | Responsible Role | Planned Action | Milestone 1 | Milestone 2 | Milestone 3 | Target Date | Status |
|---|---|---|---|---|---|---|---|---|---|---|
| POA-202607-004 | Unauthenticated SQLi chained to RCE via REST API batch route | All WordPress Core installations 6.8.0–6.8.5 / 6.9.0–6.9.4 / 7.0.0–7.0.1 | SI-2, SI-10, AC-3 | Web/IT Operations | Upgrade all sites to 7.0.2 / 6.9.5 / 6.8.6; confirm auto-update is enabled going forward | 2026-07-28: Inventory all organization-run WordPress sites | 2026-07-30: Confirm patched version on all sites | 2026-08-01: Enable/verify auto-update setting | 2026-08-01 | Open — Emergency |
| POA-202607-005 | Potential existing compromise (webshells, rogue admin accounts, malicious plugins) predating patch | All WordPress Core installations exposed since 2026-07-17 | CIS Control 16 | Security Operations | Sweep web roots and `/wp-content/cache/` for unauthorized files; audit administrator account list; audit installed plugins | 2026-07-29: Complete file-integrity sweep | 2026-07-31: Complete admin account audit | 2026-08-04: Remediate any findings | 2026-08-04 | Open — Emergency |
| POA-202607-006 | Database credentials/authentication keys potentially exposed via `wp-config.php` LFI attempts | WordPress database backends | CIS Control 7 | Web/IT Operations | Rotate database credentials and WordPress authentication/security keys (salts) on any site with sweep findings or unconfirmed clean status | 2026-08-01: Identify sites requiring rotation | 2026-08-05: Complete credential rotation | 2026-08-08: Verify rotation effective | 2026-08-08 | Open |
| POA-202607-007 | No WAF coverage on public-facing CMS as compensating control | Public-facing WordPress infrastructure | CIS Control 16 | Web/IT Operations | Deploy WAF rule set covering REST API abuse patterns for WordPress as a standing compensating control | 2026-08-04: Evaluate WAF rule options | 2026-08-11: Deploy rules | 2026-08-15: Validate rule effectiveness | 2026-08-15 | Open — Standard Cycle |

## Remediation Narrative
Apply WordPress Core version 7.0.2 (or 6.9.5 / 6.8.6 depending on branch) to every affected site immediately; where automatic updates are disabled, apply manually and re-enable auto-updates for core going forward. Because Wordfence and SANS ISC telemetry confirm exploitation began 2026-07-17 — before public disclosure — patching must be paired with a compromise sweep: check `/wp-content/cache/` and other writable web-root directories for unauthorized PHP files, review the installed-plugins list for anything not deliberately installed by the organization (the observed attack pattern installs a malicious plugin exposing a remote-command-execution REST endpoint), and audit the WordPress administrator account list for unfamiliar entries. Any site where sweep findings are positive requires full database credential rotation and regeneration of WordPress authentication/security keys (the `wp-config.php` salts), since these were direct targets of the local-file-inclusion attempts observed in this campaign.

## Compensating Controls
Deploy or update WAF rules blocking anomalous requests to the WordPress REST API batch endpoint and to `admin-ajax.php` targeting `wp-config.php`, pending confirmation that all sites are patched and swept.

## Verification & Closure Criteria
Closure requires: (1) confirmed patched version across all identified WordPress sites, (2) a completed file-integrity and plugin/admin-account audit with no unresolved findings, (3) credential/key rotation completed on any site with positive sweep findings, and (4) WAF rule deployment confirmed active for ongoing compensating protection.

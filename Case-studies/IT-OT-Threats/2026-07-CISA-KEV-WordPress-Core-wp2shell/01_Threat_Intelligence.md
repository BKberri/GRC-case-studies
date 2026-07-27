# Threat Intelligence Report — WordPress Core "wp2shell" Unauthenticated RCE Chain

## CVE Details

| Field | Value |
|---|---|
| **CVE IDs** | CVE-2026-63030 (REST API route confusion), CVE-2026-60137 (SQL injection, `author__not_in` in WP_Query) |
| **Vulnerability Name** | "wp2shell" — WordPress Core unauthenticated RCE exploit chain |
| **Affected Vendor/Product** | WordPress Core 6.8.0–6.8.5, 6.9.0–6.9.4, 7.0.0–7.0.1 |
| **CVSS Score** | 9.8 Critical (CNA/Wordfence/WPScan); secondary CISA-ADP assessment 7.5 |
| **Vulnerable Component** | REST API batch-processing endpoint (route confusion) chained with SQL injection in `WP_Query`'s `author__not_in` parameter |
| **Date Added to KEV** | 2026-07-21 |
| **CISA Remediation Due Date** | 2026-07-24 (3-day emergency mandate under BOD 26-04) |
| **Exploitation Type** | Unauthenticated SQL injection chained to full remote code execution |

## Executive Overview
The WordPress REST API's batch endpoint incorrectly resolves internal routes (CVE-2026-63030), and when chained with a pre-existing SQL injection flaw in how `WP_Query` handles the `author__not_in` parameter (CVE-2026-60137), an attacker with no account and no authentication can inject SQL and ultimately execute arbitrary code on the server. Security researchers have labeled this the first critical, unauthenticated WordPress Core RCE in nearly a decade — a materially different risk category than the plugin/extension-level flaws this program has tracked in prior weeks, because it requires no third-party plugin to be installed at all.

## Technical Details
- **CVE IDs / Advisory:** CVE-2026-63030, CVE-2026-60137 (combined exploit chain nicknamed "wp2shell" by researchers at SearchLight Cyber, who first disclosed it)
- **CVSS Score and vector:** 9.8 Critical per CNA, Wordfence, and WPScan scoring; NVD's CISA-ADP secondary assessment scores it 7.5 — flagged here as a scoring divergence worth tracking, not a reason to deprioritize, given confirmed active exploitation at the higher-severity end of the spectrum
- **Affected vendor/product/version:** WordPress Core 6.8.0 through 6.8.5, 6.9.0 through 6.9.4, and 7.0.0 through 7.0.1; patched in 7.0.2, 6.9.5, and 6.8.6 (WordPress auto-pushed the fix to supported installations)
- **Vulnerability type:** REST API route confusion (CVE-2026-63030) chained with unauthenticated SQL injection (CVE-2026-60137), together enabling full RCE
- **Exploitation status:** Actively exploited. Wordfence's timeline: first exploitation-related probing observed 2026-07-17 at 23:29 UTC, with a clear SQL injection attempt 13 minutes later — predating both the public technical disclosure and the KEV listing
- **Threat actor attribution:** Not attributed to a single named group; Wiz and SANS ISC researchers independently observed mass-scanning consistent with opportunistic, automated exploitation rather than a targeted campaign
- **MITRE ATT&CK:** T1190 (Exploit Public-Facing Application), T1505.003 (Server Software Component: Web Shell), T1136 (Create Account — rogue WordPress admin accounts observed in some attacks)
- **IOCs:** Webshells created under `/wp-content/cache/` with randomized filenames used as access passwords (per SANS ISC researcher Johannes Ullrich); malicious plugins installed to expose a REST API endpoint for remote command execution; queries against the WordPress REST API to enumerate administrator usernames/emails; local file inclusion attempts against `wp-config.php` via `admin-ajax.php` to retrieve database credentials and authentication keys; webshell functions checked include `system()`, `passthru()`, `exec()`, `shell_exec()`, `popen()`, and the backtick operator
- **CISA remediation due date:** 2026-07-24 (KEV added 2026-07-21; 3-business-day BOD 26-04 emergency mandate)

## Affected Technology Context
WordPress powers a substantial share of the public web, including many enterprise marketing sites, customer portals, and content properties that security teams may not treat with the same rigor as core business applications — "it's just the website" is a common but dangerous framing. Because this flaw lives in WordPress Core rather than a plugin, every unpatched WordPress installation is exposed regardless of which plugins are installed, dramatically widening the affected population compared to the plugin-specific findings this program logged in the prior reporting period (RR-030 through RR-033, the four-extension Joomla file-upload cluster). Observed attacker behavior — rogue admin account creation, webshell installation, database credential harvesting via `wp-config.php` — indicates attackers are establishing durable persistence, not merely probing. An independent public dashboard tracking patch adoption across a sample of ~124,580 sites reported an 81.6% patch rate days after disclosure, meaning a meaningful fraction of internet-facing WordPress installations likely remain exploitable.

## Intelligence Source Links
- CISA KEV addition: https://www.cisa.gov/news-events/alerts/2026/07/21/cisa-adds-four-known-exploited-vulnerabilities-catalog
- NVD (CVE-2026-63030): https://nvd.nist.gov/vuln/detail/CVE-2026-63030
- Wordfence "aftermath" analysis: https://www.wordfence.com/blog/2026/07/wp2shell-aftermath-the-first-critical-unauthenticated-wordpress-core-rce-in-nearly-a-decade/
- Wiz technical analysis: https://www.wiz.io/blog/wp2shell-cve-2026-63030-cve-2026-60137
- SANS ISC diary (Johannes Ullrich): https://isc.sans.edu/diary/WordPress+Exploitation+Underway+CVE202663030/33168/
- BleepingComputer: https://www.bleepingcomputer.com/news/security/critical-wp2shell-wordpress-flaws-exploited-to-install-webshells/

## Risk Rating
**Critical** — CVSS 9.8 (primary scoring), unauthenticated SQL injection chained to full RCE in WordPress Core itself (not a plugin), confirmed active exploitation with persistent webshell and rogue-admin-account deployment, and 3-day federal remediation mandate.

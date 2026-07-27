# Risk Assessment
## WordPress Core "wp2shell" Unauthenticated RCE Chain (CVE-2026-63030 + CVE-2026-60137)

## Risk Scoring
| Method | Score | Rating |
|---|---|---|
| Likelihood × Impact Matrix | 5 × 5 = 25 | Critical |
| CVSS Base Score (primary) | 9.8 | Critical |
| CVSS Base Score (CISA-ADP secondary) | 7.5 | High |

**Likelihood = 5 (Actively exploited):** Confirmed exploitation predating public disclosure (first probing 2026-07-17, ahead of the researcher write-up), with mass-scanning, webshell installation, and rogue admin account creation observed across the internet-facing WordPress population.
**Impact = 5 (Full system compromise / data breach):** Unauthenticated path to full RCE, database credential theft, and durable persistence via webshells and rogue accounts.

## Risk Narrative
The realistic threat scenario is broad, automated, and already underway rather than hypothetical: mass scanners probe internet-facing WordPress sites for the vulnerable REST API route, chain the SQL injection to achieve code execution, and immediately move to persistence — installing a disguised plugin that exposes a remote-command-execution endpoint, dropping PHP webshells in cache directories, and in some cases creating rogue administrator accounts. The most probable path to material business impact is a public-facing marketing or customer-portal WordPress site that the organization does not treat as a Tier-1 asset for patch management, gets compromised within days of disclosure, and is used either as a foothold for further internal network access (if co-located with other infrastructure) or simply defaced/used to host malicious content that damages brand trust and potentially triggers search-engine blacklisting.

## Framework Control Gaps
- **NIST 800-53 SI-2 (Flaw Remediation):** Auto-update was WordPress's own mitigation for supported sites; organizations that disable automatic core updates (common in enterprise environments with change-control processes) lost this safety net and needed a manual, expedited patch cycle.
- **NIST 800-53 SI-3 / SI-10 (Malicious Code Protection / Information Input Validation):** The root cause is unauthenticated SQL injection — a textbook input-validation failure that predates this specific incident by years as a known control category.
- **CIS Control 7 (Continuous Vulnerability Management):** Organizations without a WordPress-specific asset inventory and patch cadence could not have responded within the 3-day exploitation window observed here.
- **CIS Control 16 (Application Software Security):** Absence of a web application firewall rule covering the vulnerable REST API route removed a compensating control that could have blunted exploitation pending patch.

## Residual Risk Statement
After patching to 7.0.2 / 6.9.5 / 6.8.6, residual risk depends entirely on whether the instance was compromised during the exposure window (2026-07-17 onward). Patching alone does not remove a webshell already planted in `/wp-content/cache/`, a malicious plugin already installed, or a rogue administrator account already created — all of which survive an update. Residual risk is High until a full compromise assessment (webshell/plugin sweep, admin account audit, database credential rotation) is completed; it drops to Low only after that assessment confirms no persistence artifacts remain.

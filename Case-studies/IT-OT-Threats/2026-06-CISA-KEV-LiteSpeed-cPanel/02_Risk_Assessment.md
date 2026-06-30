# Risk Assessment — CVE-2026-54420 (LiteSpeed cPanel Plugin)

## Risk Statement
An actively exploited symlink-handling flaw in the LiteSpeed cPanel plugin allows an attacker with only FTP or web-shell access on a single shared hosting account to escalate to root, defeating CloudLinux/CageFS tenant isolation. The federal remediation due date (2026-06-18) has already passed without confirmation of organization-wide patching.

## Likelihood: 5/5 (Actively exploited in the wild)
- CISA confirmed active exploitation prior to KEV listing.
- Low barrier to entry: any existing low-privilege account compromise (e.g., via a separate web application vulnerability or weak credentials) provides the foothold needed to trigger this flaw.
- Exploitation is documented as "weaponized for tenant breakout" — indicating mature, repeatable exploit tooling is already circulating.

## Impact: 5/5 (Full system compromise / data breach)
- Root access on a shared hosting server compromises every tenant on that host, not just the initially-compromised account.
- On multi-tenant infrastructure, this represents a one-to-many blast radius uncommon for a single CVE.

## Risk Score: 25 (5 × 5) — **Critical**

## Inherent Risk: Critical
## Residual Risk: Critical (no effective compensating control short of patching)
CloudLinux/CageFS — the standard compensating control for shared-hosting tenant isolation — is specifically defeated by this vulnerability, leaving organizations with no meaningful interim mitigation other than aggressive monitoring for symlink-creation anomalies and FTP/web-shell access abuse.

## Business Risk Translation
If left unpatched, a single compromised customer account on shared hosting infrastructure can become a complete breach of every other customer hosted on the same server — turning an isolated incident into a multi-tenant data breach with proportionally larger legal, contractual, and reputational exposure.

## Compliance Note
Given the overdue federal due date, any FedRAMP, CMMC, or federal-contract-adjacent hosting environment subject to BOD 26-04 should treat this as a reportable compliance gap until closure evidence is documented.

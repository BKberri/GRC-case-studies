# POA&M / Remediation Plan — Joomla! Extension Ecosystem Mass File-Upload RCE

| # | Action | Owner | Target Date | Status |
|---|---|---|---|---|
| 1 | Inventory all Joomla installations and installed extensions/plugins | Web/IT Operations | 2026-07-09 | Open |
| 2 | Patch SP Page Builder to 6.6.2+ and Joomlack Page Builder to vendor-patched version wherever installed | Web/IT Operations | 2026-07-10 | Open |
| 3 | Patch iCagenda to 4.0.8+ and Balbooa Forms to vendor-patched version wherever installed | Web/IT Operations | 2026-07-13 | Open |
| 4 | Scan all Joomla web roots for unauthorized PHP/web-shell files (all sites, not just those with the four named extensions) | Security Operations | 2026-07-14 | Open |
| 5 | Deploy WAF rules on extension upload endpoints as interim/standing compensating control | Security Operations | 2026-07-10 | Open |
| 6 | Build/refresh a full Joomla extension inventory as a standing vulnerability-management input | Web/IT Operations | 2026-08-10 | Open |
| 7 | Document closure evidence and update risk register (4 rows) | GRC | 2026-07-18 | Open |

## Specific Remediation
Patch each affected extension to its vendor-fixed version per the schedule above. Independent of which of the four extensions is installed, run a web-root scan for unauthorized files across all Joomla sites — the convergent zero-day pattern across four unrelated vendors this week indicates the same vulnerability class may exist in extensions not yet publicly disclosed, so patch compliance on these four CVEs alone does not fully retire risk.

## Cross-Reference
See also `IT-OT-Threats/2026-06-CISA-KEV-Joomla-JCE` — a prior, distinct finding in the same CMS ecosystem and vulnerability class (unauthenticated file-upload RCE), included here for pattern awareness, not as a superseded or related revision.

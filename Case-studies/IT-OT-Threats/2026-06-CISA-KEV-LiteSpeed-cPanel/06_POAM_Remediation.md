# POA&M / Remediation Plan — CVE-2026-54420 (LiteSpeed cPanel Plugin)

| # | Action | Owner | Target Date | Status |
|---|---|---|---|---|
| 1 | Inventory all servers running LiteSpeed Web Server + cPanel/WHM plugin | Hosting Operations | 2026-06-23 | Open — Overdue baseline |
| 2 | Upgrade to LiteSpeed WHM Plugin v5.3.2.1 (cPanel plugin v2.4.8) or later on all identified servers | Hosting Operations | 2026-06-23 | Open — Emergency (federal due date 2026-06-18 already passed) |
| 3 | Review server logs for symlink-creation anomalies and unexpected root-level process activity predating the patch | Security Operations / IR | 2026-06-24 | Open |
| 4 | Validate CloudLinux/CageFS isolation integrity post-patch via configuration audit | Hosting Operations | 2026-06-25 | Open |
| 5 | Determine tenant notification requirements if IOCs are found | GRC / Legal | Upon IOC findings | Pending |
| 6 | Document closure evidence (patch version per host, log review findings) | GRC | 2026-06-26 | Open |

## Specific Remediation
Upgrade to LiteSpeed WHM Plugin v5.3.2.1 / cPanel plugin v2.4.8 or later on every affected host. No registry, ACL, or configuration-only workaround exists — the only remediation is the vendor patch.

## Overdue Status Note
The CISA-mandated due date (2026-06-18) has passed as of this report (2026-06-22). This POA&M should be flagged in the next compliance status review as a missed BOD 26-04 deadline pending confirmation of patch completion.

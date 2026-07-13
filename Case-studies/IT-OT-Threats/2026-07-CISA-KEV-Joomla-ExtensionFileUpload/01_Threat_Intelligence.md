# Threat Intelligence Report — Joomla! Extension Ecosystem Mass File-Upload RCE

## CVE Details

| CVE ID | Extension / Vendor | CVSS | KEV Added | Federal Due Date |
|---|---|---|---|---|
| CVE-2026-48908 | SP Page Builder (JoomShaper) — affects all versions ≤ 6.6.1, fixed in 6.6.2 | 10.0 | 2026-07-07 | 2026-07-10 |
| CVE-2026-56290 | Page Builder (Joomlack) | 10.0 | 2026-07-07 | 2026-07-10 |
| CVE-2026-48939 | iCagenda — affects versions ≤ 4.0.7, fixed in 4.0.8 | 10.0 | 2026-07-10 | 2026-07-13 |
| CVE-2026-56291 | Balbooa Forms | 10.0 | 2026-07-10 | 2026-07-13 |

**Vulnerability Class (all four):** Unauthenticated unrestricted/arbitrary file upload (CWE-284 Improper Access Control / CWE-434 Unrestricted Upload of File with Dangerous Type) enabling remote code execution.

## Exploitation Summary
All four vulnerabilities share the same fundamental pattern: each extension exposes an endpoint (icon-upload functionality, file-attachment functionality, or equivalent) that accepts file uploads without authentication and without adequate file-type validation, allowing an attacker to upload a PHP web shell directly into the Joomla web root and execute it — full remote code execution with no credentials required. CVE-2026-48908 (SP Page Builder) was disclosed via the `uploadCustomIcon` functionality; CVE-2026-48939 (iCagenda) via its file-attachment feature. All four are confirmed under active zero-day exploitation, and all four were added to CISA's KEV catalog within a single week (2026-07-07 and 2026-07-10), each under a 3-day emergency remediation mandate.

## Pattern Significance
Four independently developed, unrelated Joomla extensions producing the identical vulnerability class within the same disclosure week is a notable ecosystem-level signal: it suggests either coordinated security research sweeping the Joomla extension marketplace for this vulnerability pattern, or independent threat actors converging on the same class of low-hanging-fruit flaw across third-party CMS extensions. Organizations running Joomla with any third-party extensions — not just these four — should treat this as a prompt for a full extension inventory and file-upload-endpoint review, not just a four-CVE patch exercise.

## Framework Mapping (applies to all four CVEs)
- **NIST CSF 2.0:** PR.PS-04 (Software/firmware kept up to date), DE.CM-09 (Computing hardware/software monitored), PR.IR-01 (Network integrity protected)
- **NIST 800-53 Rev 5:** SI-2 (Flaw Remediation), SI-3 (Malicious Code Protection), SI-10 (Information Input Validation), SC-7 (Boundary Protection)
- **ISO/IEC 27001:2022:** A.8.8 (Management of technical vulnerabilities), A.8.28 (Secure coding)
- **CIS Controls v8:** Control 7 (Continuous Vulnerability Management), Control 16 (Application Software Security)

## Recommended Immediate Action
Identify every Joomla installation in the environment and enumerate all installed third-party extensions. Upgrade SP Page Builder to 6.6.2+, iCagenda to 4.0.8+, and apply vendor patches for Joomlack Page Builder and Balbooa Forms as soon as available. Scan all Joomla web roots for unauthorized PHP files uploaded via extension upload endpoints, regardless of which (if any) of these four extensions is installed — the pattern indicates this vulnerability class may recur in extensions not yet publicly disclosed.

## Risk Rating
**Critical** — all four CVEs rated CVSS 10.0, unauthenticated RCE, confirmed active zero-day exploitation, 3-day federal remediation mandates.

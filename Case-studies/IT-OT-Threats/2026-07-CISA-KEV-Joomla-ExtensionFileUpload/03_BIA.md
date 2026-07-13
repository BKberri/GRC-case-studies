# Business Impact Analysis — Joomla! Extension Ecosystem Mass File-Upload RCE

## Affected Business Function
Any Joomla!-based public-facing website or portal running SP Page Builder, Joomlack Page Builder, iCagenda, or Balbooa Forms — commonly marketing sites, event/registration portals, and public form-intake systems.

## Impact Categories

| Impact Type | Assessment |
|---|---|
| **Confidentiality** | High — RCE on the host exposes any data reachable by the web application, including form-submission data (Balbooa), event/registrant data (iCagenda), and any connected backend systems |
| **Integrity** | Critical — attacker-controlled code execution allows arbitrary defacement, content manipulation, or use of the site as a staging point for further attacks |
| **Availability** | High — compromised public-facing sites are common targets for defacement or further weaponization (e.g., malware distribution, phishing hosting) |
| **Regulatory/Compliance** | Medium-High — where PII is collected via affected forms/registration systems, compromise may trigger breach-notification review |
| **Reputational** | High — public-facing website compromise (defacement, malware hosting) is directly visible to customers/the public, unlike an internal-system compromise |
| **Financial** | Medium — incident response and remediation costs across potentially multiple affected sites/extensions |

## Recovery Time Objective (RTO) / Recovery Point Objective (RPO)
- **RTO:** Patch each affected extension per its federal due date (2026-07-10 for SP Page Builder/Joomlack; 2026-07-13 for iCagenda/Balbooa Forms).
- **RPO:** Web-shell/unauthorized-file sweep should cover each extension's disclosure/exploitation window; given zero-day exploitation was confirmed for multiple of these, treat any affected site as potentially compromised prior to patch availability and review accordingly.

## Dependency Mapping
Any system integrated with an affected Joomla site (shared hosting environment, connected databases, single sign-on) inherits exposure from host compromise. Shared/multi-tenant Joomla hosting environments should be treated as higher priority given the potential for cross-site impact from a single compromised extension.

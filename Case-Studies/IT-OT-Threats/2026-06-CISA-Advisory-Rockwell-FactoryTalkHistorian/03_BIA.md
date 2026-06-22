# Business Impact Analysis — Rockwell FactoryTalk Historian SE Multiple Vulnerabilities

## Affected Business Function
OT/ICS process data collection, historization, and analytics infrastructure (FactoryTalk Historian SE), typically deployed at the IT/OT network boundary.

## Impact Categories

| Impact Type | Assessment |
|---|---|
| **Confidentiality** | High — historian databases contain process data that may reveal proprietary manufacturing parameters or operational details |
| **Integrity** | Critical — RCE could allow manipulation of historical process data relied upon for safety, quality, and compliance reporting |
| **Availability** | High — compromise or disruption of the historian affects downstream reporting, analytics, and potentially OT operational visibility |
| **Regulatory/Compliance** | Medium-High — depending on sector (e.g., manufacturing, utilities, critical infrastructure), compromised process data integrity may affect safety or regulatory attestations |
| **Reputational** | Medium — OT/ICS incidents involving named industrial control vendors draw significant media and regulatory attention |

## Recovery Time Objective (RTO) / Recovery Point Objective (RPO)
- **RTO:** Patch deployment targeted within the standard OT change-control patch cycle; given the severity of CVE-2025-13036, recommend expediting outside normal cycle where feasible (target: 2 weeks).
- **RPO:** Verify historian database backups are current and isolated from the production historian server in case of integrity compromise requiring rollback.

## Dependency Mapping
Any business reporting, regulatory attestation, or safety analytics process that depends on FactoryTalk Historian data inherits the integrity risk posed by these vulnerabilities until patched.

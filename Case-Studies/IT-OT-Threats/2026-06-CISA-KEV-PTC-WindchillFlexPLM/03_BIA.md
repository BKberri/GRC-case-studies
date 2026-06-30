# Business Impact Analysis — CVE-2026-12569 (PTC Windchill/FlexPLM)

## Affected Business Function
Product lifecycle management — engineering design data, bills of materials, supplier/partner data exchange, and product specification management for any organization running internet-facing Windchill or FlexPLM instances.

## Impact Categories

| Impact Type | Assessment |
|---|---|
| **Confidentiality** | Critical — direct exposure of proprietary engineering designs, CAD files, and supplier/partner data |
| **Integrity** | High — attacker with RCE can modify product specifications, bills of materials, or design records |
| **Availability** | High — ransomware deployment or destructive attack could take the PLM platform offline, halting product development workflows |
| **Regulatory/Compliance** | High — exposure of CUI or export-controlled technical data may trigger DFARS/CMMC/ITAR/EAR reporting obligations |
| **Reputational** | High — IP theft involving customer or partner design data carries significant reputational and contractual risk |

## Recovery Time Objective (RTO) / Recovery Point Objective (RPO)
- **RTO:** Patch deployment within the federal 3-day window (2026-06-28); incident response activation if compromise indicators are found.
- **RPO:** Restore from last verified-clean backup if integrity compromise (unauthorized BOM/design changes) is confirmed.

## Dependency Mapping
Organizations sharing Windchill/FlexPLM access with external suppliers or partners should assess whether compromise could propagate through shared workspaces, and should coordinate with affected third parties on incident notification if exposure is confirmed.

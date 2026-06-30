# Business Impact Analysis — CVE-2026-20262 (Cisco Catalyst SD-WAN Manager)

## Affected Business Function
Enterprise WAN connectivity and network policy management across all sites connected via Cisco Catalyst SD-WAN fabric (branch offices, data centers, cloud on-ramps).

## Impact Categories

| Impact Type | Assessment |
|---|---|
| **Confidentiality** | High — root access exposes all stored configuration, credentials, and routing/security policy data on the appliance |
| **Integrity** | Critical — attacker with root can modify routing policy, disable segmentation, or insert persistent backdoors into the WAN control plane |
| **Availability** | High — attacker can disrupt WAN connectivity for all connected sites simultaneously by modifying or deleting SD-WAN policy |
| **Regulatory/Compliance** | Medium — depending on data traversing the WAN fabric, a confirmed compromise could trigger breach notification obligations (state breach laws, sector-specific regulations) if regulated data was exposed or traffic was intercepted |
| **Reputational** | Medium-High — WAN-wide compromise affecting multi-site operations is a visible, hard-to-contain incident |

## Recovery Time Objective (RTO) / Recovery Point Objective (RPO)
- **RTO:** Patch deployment and credential rotation should complete within the CISA-mandated window (by 2026-06-29); if active compromise is detected, treat as an active incident with IR-driven RTO (target: containment within 24 hours of detection).
- **RPO:** Configuration backups of SD-WAN Manager should be current as of the last change window prior to patching to support clean rollback if a malicious configuration change is discovered.

## Dependency Mapping
All branch and data-center connectivity routed through the SD-WAN fabric is dependent on the integrity of this single control plane. Loss of trust in SD-WAN Manager cascades to every business application relying on site-to-site or site-to-cloud connectivity through the fabric.

## Single Point of Failure Note
SD-WAN Manager functions as a centralized control plane; this case reinforces the architectural risk of concentrating WAN policy enforcement in a single, internet-reachable management system without strict network isolation.

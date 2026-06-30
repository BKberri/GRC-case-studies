# Business Impact Analysis — ICSA-26-176-04 (Daktronics Controller Firmware)

## Affected Business Function
Public-facing display/signage infrastructure, including stadium displays, transportation hub information systems, and digital signage networks running affected Daktronics controllers.

## Impact Categories

| Impact Type | Assessment |
|---|---|
| **Confidentiality** | Low — limited sensitive data typically processed by display controllers |
| **Integrity** | High — attacker with root access can alter displayed content (defacement, disinformation risk) |
| **Availability** | Medium-High — denial of service against safety-relevant signage (transportation, emergency information) carries elevated impact |
| **Regulatory/Compliance** | Low-Medium — limited direct regulatory exposure unless signage serves a safety-notification function in a regulated transportation context |
| **Reputational** | High — public-facing defacement is highly visible and carries significant reputational risk |

## Recovery Time Objective (RTO) / Recovery Point Objective (RPO)
- **RTO:** Firmware update should be scheduled within standard change-management windows; expedite for any controller serving a safety-notification function.
- **RPO:** Not applicable in the traditional data-recovery sense; focus on restoring controller to known-good firmware/configuration state if compromise is detected.

## Dependency Mapping
Organizations should map which Daktronics controllers, if any, share network segments with other OT/safety systems, and prioritize segmentation verification for those instances over purely decorative/marketing signage deployments.

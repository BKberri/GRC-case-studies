# Business Impact Analysis — CVE-2026-54420 (LiteSpeed cPanel Plugin)

## Affected Business Function
Shared/multi-tenant web hosting infrastructure running LiteSpeed Web Server with the cPanel/WHM plugin and CloudLinux/CageFS tenant isolation.

## Impact Categories

| Impact Type | Assessment |
|---|---|
| **Confidentiality** | Critical — root access exposes data for every tenant on the affected server, not just the compromised account |
| **Integrity** | Critical — attacker can modify any file, database, or configuration across all hosted tenants |
| **Availability** | High — attacker with root can disrupt service for all tenants on the host simultaneously |
| **Regulatory/Compliance** | High — a multi-tenant breach likely triggers notification obligations to every affected customer/tenant organization, multiplying regulatory exposure (state breach laws, GDPR/CCPA depending on tenant data, sector regulations per tenant) |
| **Reputational** | High — hosting providers or platforms affected by cross-tenant compromise face acute trust damage with their entire customer base, not a single client |

## Recovery Time Objective (RTO) / Recovery Point Objective (RPO)
- **RTO:** Patch deployment should have completed by the federal due date (2026-06-18); given the date has passed, treat remediation as overdue-critical with an internal target of immediate (within 24 hours of this report).
- **RPO:** Full server/tenant backups should be validated as current and clean prior to patching, in case forensic rollback of any tenant is required.

## Dependency Mapping
Every tenant hosted on an affected LiteSpeed/cPanel server inherits this risk regardless of that tenant's own security posture — this is a hosting-platform-level dependency outside individual tenant control.

## Multi-Tenant Notification Consideration
If forensic review identifies indicators of compromise predating the patch, affected hosting providers should assess notification obligations to all tenants on the affected server(s), not solely the tenant whose account was the initial entry point.

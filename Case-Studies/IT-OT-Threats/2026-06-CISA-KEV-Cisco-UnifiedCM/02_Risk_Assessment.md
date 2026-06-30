# Risk Assessment — CVE-2026-20384 (Cisco Unified Communications Manager)

## Risk Statement
A static, undocumented credential in Cisco Unified CM allows an attacker to bypass authentication and obtain root-level access to the enterprise call-control platform, with confirmed active exploitation in the wild.

## Likelihood: 5/5 (Actively exploited in the wild)
- CISA confirmed active exploitation, triggering the expedited 3-day BOD 26-04 mandate.
- Static credentials are a well-known, easily weaponized attack vector once disclosed or reverse-engineered, and require no social engineering or prior access.

## Impact: 5/5 (Critical — root-level access to enterprise voice infrastructure)
- Root access to Unified CM allows interception or recording of voice communications, manipulation of call routing, and lateral movement into the broader UC/voice network.
- Outage or manipulation of Unified CM disrupts enterprise-wide voice communications, including potentially emergency/911 call routing in some deployments.
- Organizations subject to communications-privacy regulation face elevated regulatory exposure if call interception is confirmed.

## Risk Score: 25 (5 × 5) — **Critical**

## Inherent Risk: Critical
## Residual Risk: High until patched; reduced to Medium with patching, credential rotation, and management-plane network restriction.

## Business Risk Translation
Voice communications often carry sensitive business discussions, customer PII (e.g., call centers handling payment or health information), and executive communications. Root-level compromise of the call-control platform should be treated as a potential wiretapping incident pending forensic review, not merely an infrastructure availability issue.

## Compliance Note
Organizations in financial services or healthcare using Unified CM for customer-facing call centers should evaluate whether this exposure triggers breach-notification obligations under GLBA, HIPAA, or state wiretapping statutes if interception is confirmed.

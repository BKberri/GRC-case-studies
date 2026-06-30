# Risk Assessment — ICSA-26-176-04 (Daktronics Controller Firmware)

## Risk Statement
A chain of vulnerabilities in Daktronics display controller firmware allows an attacker to obtain root-level access to the device, with no confirmed active exploitation but a severity and deployment footprint (including transportation-adjacent signage) that warrants proactive remediation.

## Likelihood: 3/5 (No confirmed active exploitation; moderate attacker interest expected)
- No confirmed in-the-wild exploitation at time of publication.
- Display controllers are a less conventional target than IT infrastructure, but public-facing defacement attacks have historical precedent (digital signage hijacking is an established attack pattern).
- Multi-CVE chain requires more attacker effort than a single unauthenticated RCE, moderating likelihood relative to this week's KEV cases.

## Impact: 4/5 (High — public-facing disruption/defacement, potential OT network pivot)
- Display defacement carries reputational and, in transportation/safety-signage contexts, potential public-safety messaging risk.
- Root access could be leveraged as a pivot point if the controller shares network segments with other operational systems.
- Denial of service against safety-relevant signage (e.g., transportation hub displays) carries elevated impact beyond simple reputational harm.

## Risk Score: 12 (3 × 4) — **High**

## Inherent Risk: High
## Residual Risk: Medium with firmware update and network segmentation verification.

## Business Risk Translation
Organizations operating Daktronics controllers in transportation, stadium, or public-information contexts should treat this as a public-safety/reputational risk item in addition to a standard technical vulnerability, given the visibility of any successful defacement or denial-of-service attack.

## Comparison to Program Precedent
Consistent with RR-020 (Rockwell FactoryTalk Historian) — both are multi-CVE chains to root access without confirmed active exploitation, both warranting full assessment due to severity and critical-infrastructure-adjacent deployment.

# Control Mapping
## 2026-08-CISA-KEV-Progress-LoadMaster-CommandInjection

## Applicable Frameworks
NIST CSF 2.0 and NIST 800-53 Rev 5 for enterprise risk management and input-validation control specificity; ISO 27001:2022 Annex A for ISMS-aligned organizations; CIS Controls v8 for network architecture and prioritized remediation guidance.

## Control Mapping Table
| Framework | Control ID | Control Name | Applicability | Gap / Status |
|---|---|---|---|---|
| NIST 800-53 | SI-10 | Information Input Validation | Root cause is a flawed input-sanitization function permitting shell metacharacter injection | Gap (vendor) |
| NIST 800-53 | SI-2 | Flaw Remediation | Over five-week gap between vendor patch and KEV addition with confirmed ongoing exploitation | Gap (process) |
| NIST 800-53 | AC-4 | Information Flow Enforcement | Management API should not be reachable from the open internet without compensating access restriction | Gap |
| NIST CSF 2.0 | PR.PS-01 | Configuration management practices are established | Perimeter appliance patch policy should not depend solely on KEV listing to trigger urgency | Gap |
| ISO 27001 | A.8.28 | Secure Coding | Vendor-side secure-coding gap (unsafe memory handling in sanitization function) | Gap (vendor) |
| ISO 27001 | A.8.20 | Networks Security | Management-plane API exposure should be minimized via network segmentation | Gap |
| CIS Controls | CIS 12.2 | Establish and Maintain a Secure Network Architecture | Internet-facing management/API endpoints on perimeter infrastructure require access restriction as a standing control | Gap |

## Control Narrative
This finding is a textbook input-validation failure (SI-10) compounded by an organizational patch-prioritization gap: the vendor fix was available in June, but exploitation continued for over five weeks before this specific finding entered the KEV catalog and triggered elevated attention through that channel. This is a useful case for illustrating to leadership why patch-management policy should not be exclusively KEV-driven — vendor security advisories and CVSS severity alone should be sufficient to trigger expedited patching for perimeter infrastructure like ADCs, without waiting for CISA's catalog listing as the forcing function.

Network-level compensating controls (AC-4, CIS 12.2) matter significantly for this vulnerability class because the affected endpoint (`/accessv2`) is part of the appliance's management/API surface, which in many deployments does not need to be reachable from the open internet at all — restricting it to an administrative network segment would have prevented exploitation entirely, independent of the underlying code defect, and should be considered a standing control for this device class going forward regardless of patch status.

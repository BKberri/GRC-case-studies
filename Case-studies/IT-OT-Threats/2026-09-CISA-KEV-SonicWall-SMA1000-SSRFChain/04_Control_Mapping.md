# Control Mapping
## 2026-09-CISA-KEV-SonicWall-SMA1000-SSRFChain

## Applicable Frameworks
NIST CSF 2.0 and NIST 800-53 Rev 5 for enterprise risk management and boundary-protection control specificity; ISO 27001:2022 Annex A for ISMS-aligned organizations; CIS Controls v8 for network architecture and prioritized remediation guidance.

## Control Mapping Table
| Framework | Control ID | Control Name | Applicability | Gap / Status |
|---|---|---|---|---|
| NIST 800-53 | SC-7 | Boundary Protection | SSRF allowed the public Work Place interface to reach functionality intended to be isolated | Gap (vendor) |
| NIST 800-53 | AC-4 | Information Flow Enforcement | Administrative console (AMC) reachable via a chain originating from an unauthenticated path | Gap (vendor) |
| NIST 800-53 | SI-10 | Information Input Validation | Root cause of the OS command injection component | Gap (vendor, now fixed) |
| NIST CSF 2.0 | PR.PS-01 | Configuration management practices are established | Perimeter remote-access appliance patch policy should be expedited by exposure profile, independent of KEV timing | Gap |
| ISO 27001 | A.8.20 | Networks Security | Administrative interfaces should be network-segmented from any path reachable by unauthenticated traffic | Gap |
| CIS Controls | CIS 12.2 | Establish and Maintain a Secure Network Architecture | Reinforces segmentation of administrative planes from public-facing interfaces | Gap |

## Control Narrative
This finding is a textbook boundary-protection failure (SC-7, AC-4) in which two independently-scoped interfaces — a public-facing user portal and a separate administrative console — were not as isolated from each other as their separate authentication requirements implied. The SSRF flaw effectively erased that isolation, turning a post-authentication administrative vulnerability into a pre-authentication one. This is a useful illustrative point for architecture reviews generally: authentication requirements on an interface are only as strong as the network-level isolation enforcing that only the intended callers can reach it — an administrative console that is technically reachable via server-side request forgery from a public interface has a weaker real-world security boundary than its authentication model alone would suggest, regardless of how well that authentication is implemented. Given this is the second SonicWall SMA-series perimeter appliance KEV entry and the third publicly-reported SMA1000 security event this program has tracked in 2026, organizations running this product line should consider elevated monitoring or a compensating network-segmentation review as a standing control, not solely reactive patching per disclosure.

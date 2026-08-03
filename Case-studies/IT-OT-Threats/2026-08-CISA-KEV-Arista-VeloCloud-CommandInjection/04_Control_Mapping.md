# Control Mapping
## 2026-08-CISA-KEV-Arista-VeloCloud-CommandInjection

## Applicable Frameworks
NIST CSF 2.0 and NIST 800-53 Rev 5 for enterprise risk management and control specificity; ISO 27001:2022 Annex A for ISMS-aligned organizations; CIS Controls v8 for prioritized, actionable remediation guidance — the standard IT/OT/Cloud framework track for this case category.

## Control Mapping Table
| Framework | Control ID | Control Name | Applicability | Gap / Status |
|---|---|---|---|---|
| NIST CSF 2.0 | PR.PS-04 | Software is maintained, replaced, and removed commensurate with risk | VCO patch to 5.2.3.14 / 6.1.3.4 / 6.4.2.4 / 7.0.0.1+ closes the vulnerable code path | Gap (pre-patch) |
| NIST CSF 2.0 | PR.AA-05 | Access permissions and authorizations are managed | Management-interface exposure should be restricted to trusted networks, not the open internet | Gap |
| NIST CSF 2.0 | DE.CM-01 | Networks and network services are monitored | Anomalous orchestrator command execution should trigger detection | Partial |
| NIST 800-53 | SI-10 | Information Input Validation | Root-cause control for the OS command injection flaw itself (vendor-side) | Gap (vendor code) |
| NIST 800-53 | SC-7 | Boundary Protection | Isolate VCO management interface behind firewall/VPN/allow-list | Gap |
| NIST 800-53 | SI-2 | Flaw Remediation | Apply vendor patch on confirmed timeline | Addressed once patched |
| ISO 27001 | A.8.8 | Management of Technical Vulnerabilities | Vulnerability identification, risk evaluation, and timely patching process | Partial |
| ISO 27001 | A.8.20 | Networks Security | Segmentation and controlled access to network management planes | Gap |
| CIS Controls | CIS 12.2 | Establish and Maintain a Secure Network Architecture | Management interfaces isolated from general-purpose network segments | Gap |
| CIS Controls | CIS 7.4 | Perform Automated Application Patch Management | Timely patch deployment for network orchestration software | Gap (pre-patch) |

## Control Narrative
The controls above split cleanly into preventive and detective categories. Preventive controls — SC-7 boundary protection, CIS 12.2 network architecture segmentation, and PR.AA-05 access management — are the highest-leverage controls here because they would have prevented remote exploitation of this vulnerability even before a patch existed, simply by removing the orchestrator's management interface from direct internet reachability. Corrective controls — SI-2 flaw remediation and CIS 7.4 automated patch management — close the vulnerability itself once Arista's fix is applied. Detective controls — DE.CM-01 network monitoring — provide the safety net for organizations that were exposed during the window between disclosure and patching, by surfacing anomalous command execution or configuration-push activity originating from the orchestrator.

A mature control environment for SD-WAN orchestration platforms treats the orchestrator itself as Tier-0 infrastructure — equivalent in sensitivity to a domain controller or PKI root — with management-plane access restricted to a dedicated administrative network, MFA-gated access, and continuous monitoring of configuration-push events for anomalies. Organizations that have not yet classified their SD-WAN orchestrator at this tier should treat this case as the trigger to do so.

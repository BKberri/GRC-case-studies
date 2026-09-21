# Control Mapping
## 2026-09-CISA-KEV-LinuxKernel-TripleCVE

## Applicable Frameworks
NIST CSF 2.0 and NIST 800-53 Rev 5 for patch management and configuration-currency controls; ISO 27001:2022 for technical vulnerability management; CIS Controls v8 for fleet-wide vulnerability remediation prioritization.

## Control Mapping Table
| Framework | Control ID | Control Name | Applicability | Gap / Status |
|---|---|---|---|---|
| NIST 800-53 | SI-2 | Flaw Remediation | Kernel patch deployment across the Linux fleet must meet the 2026-09-21 CISA deadline | Organizational — verify |
| NIST 800-53 | CM-6 | Configuration Settings | EoL/EoS kernel versions (possible per CISA note) lack a vendor fix path | Organizational — verify |
| NIST CSF 2.0 | PR.PS-02 | Software is maintained, replaced, and removed | Standing kernel-version-currency and EoL tracking practice is the control this finding tests | Organizational — verify |
| ISO 27001:2022 | A.8.8 | Management of Technical Vulnerabilities | Three simultaneous actively-exploited kernel CVEs increase remediation scope and urgency | Organizational — verify |
| CIS Controls v8 | Control 7 | Continuous Vulnerability Management | KEV-listed, actively-exploited vulnerabilities require expedited fleet-wide patch cadence | Organizational — verify |

## Control Narrative
These three CVEs are conventional kernel memory-safety and logic-handling defects, individually unremarkable in isolation but notable in aggregate: three separate, independently-confirmed actively-exploited kernel vulnerabilities disclosed on the same date suggests either a coordinated research disclosure cycle or a broader ongoing exploitation campaign leveraging multiple kernel primitives. Because remediation depends on each organization's Linux distribution and patch cadence rather than a single vendor advisory, this program recommends organizations confirm their kernel patch-management process can reliably reach 100% fleet coverage within the CISA remediation window, and separately flag any EoL/EoS kernel versions discovered during the inventory process — those require an upgrade project, not just a patch.

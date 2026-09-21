# Risk Assessment
## 2026-09-CISA-KEV-LinuxKernel-TripleCVE

## Risk Scoring
| Method | Score | Rating |
|---|---|---|
| Likelihood x Impact Matrix | 5 x 4 = 20 | Critical |
| CVSS Base Score | Up to 9.8 (CNA, disputed) / 8.8 confirmed | High-Critical |
| FAIR Qualitative | High loss exposure bounded by the local-access prerequisite — realistic threat scenario is post-compromise privilege escalation or persistence rather than initial access, but confirmed active exploitation across all three raises urgency | High |

## Risk Narrative
Likelihood is scored at 5 (actively exploited) based on Red Hat's confirmation across all three CVEs. Impact is scored at 4 (significant) rather than 5 because all three require local, low-privilege access as a precondition — this is not an internet-reachable, unauthenticated initial-access vector, but a privilege-escalation/persistence primitive most valuable to an attacker who has already gained a low-privilege foothold through another vector (phishing, an exposed application, a stolen credential). That said, the combination of three independently-confirmed actively-exploited kernel flaws disclosed simultaneously, on a technology stack present across nearly the entire enterprise Linux estate, materially increases the value of any existing foothold an attacker already holds — organizations should assume any current or recent low-privilege compromise could be leveraged to full root access via one of these three paths.

## Framework Control Gaps
- **NIST 800-53 SI-2 (Flaw Remediation):** Kernel patch cadence across the Linux server/container-host fleet should be verified against the 2026-09-21 CISA deadline.
- **NIST 800-53 CM-6 (Configuration Settings):** Organizations running EoL/EoS kernel versions (flagged by CISA as a possibility here) are exposed with no vendor-backported fix path — a standing configuration-currency gap independent of this specific KEV entry.
- **NIST CSF 2.0 PR.PS-02 (Software is maintained, replaced, and removed):** Kernel version currency and EoL tracking across the Linux fleet is the underlying control this finding tests.
- **ISO 27001:2022 A.8.8 (Management of Technical Vulnerabilities):** Standard vulnerability-management control applies; three simultaneous KEV entries on the same subsystem family increase remediation urgency and scope.

## Residual Risk Statement
After applying the distribution-specific kernel update containing all three fixes, residual risk drops to Low-Medium (Medium if the organization cannot confirm no prior low-privilege compromise occurred during the exploitation window). Organizations running EoL/EoS kernel versions without an available backported fix should treat kernel version upgrade as a required compensating action, since no patch-only remediation path exists for unsupported versions.

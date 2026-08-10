# Control Mapping
## 2026-08-NIST-NVD-Jenkins-DeserializationFilterBypass

## Applicable Frameworks
NIST CSF 2.0 and NIST 800-53 Rev 5 for enterprise risk management and access-control specificity; ISO 27001:2022 Annex A for ISMS-aligned organizations; CIS Controls v8 for application software security and secure configuration guidance.

## Control Mapping Table
| Framework | Control ID | Control Name | Applicability | Gap / Status |
|---|---|---|---|---|
| NIST 800-53 | SI-2 | Flaw Remediation | Controller should be prioritized for expedited patching given CI/CD trust-anchor role | Gap |
| NIST 800-53 | AC-6 | Least Privilege | Agent/Connect and Item/Configure/Item/Build permission scope directly gates exploitability of all three findings | Gap |
| NIST 800-53 | SC-39 | Process Isolation | Controller-agent trust boundary should limit what a compromised or malicious agent can do to the controller regardless of code-level fixes | Partial |
| NIST CSF 2.0 | PR.AA-05 | Access permissions are defined and enforced incorporating least privilege | Directly reduces practical exploitability | Gap |
| ISO 27001 | A.8.25 | Secure Development Life Cycle | CI/CD controller hardening is a secure-SDLC control area | Partial |
| CIS Controls | CIS 16.1 | Application Software Security | CI/CD platform hardening validated as an under-addressed control area by this advisory | Gap |
| CIS Controls | CIS 4.1 | Establish and Maintain a Secure Configuration Process | Controller filesystem permissions and agent trust configuration should follow documented secure-configuration baselines | Partial |

## Control Narrative
This advisory is a useful reminder that CI/CD platforms deserve the same controller/trust-boundary scrutiny applied to identity providers and privileged-access-management systems — Jenkins controllers hold the practical "keys to the kingdom" for software delivery, and all three findings in this advisory converge on controller-level code execution through different technical mechanisms (deserialization filter bypass, symlink-based arbitrary file write, path-traversal file write), which suggests the controller/agent trust boundary and controller filesystem permission model are systemically under-hardened relative to their actual privilege level.

Least-privilege scoping (AC-6, CIS 4.1) is the highest-leverage compensating control here because it is deployable immediately as a configuration change, independent of the patch timeline, and it directly reduces the population of potential exploiters for two of the three findings (which require specific permissions rather than full compromise). Organizations should treat this advisory as a prompt to audit who currently holds Agent/Connect, Item/Configure, and Item/Build permissions on their Jenkins controllers, not just to schedule the version upgrade.

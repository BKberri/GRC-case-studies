# Control Mapping
## 2026-09-MSRC-Azure-AI-PlatformBatch

## Applicable Frameworks
NIST AI RMF and ISO 42001 for AI-platform-specific impact-assessment and governance gaps; NIST CSF 2.0 and NIST 800-53 Rev 5 for the underlying authentication/input-validation control failures.

## Control Mapping Table
| Framework | Control ID | Control Name | Applicability | Gap / Status |
|---|---|---|---|---|
| NIST 800-53 | IA-2 | Identification and Authentication | Azure AI Foundry critical function lacked authentication enforcement | Gap (vendor, fixed) |
| NIST 800-53 | SI-10 | Information Input Validation | Copilot command elements not adequately neutralized before execution | Gap (vendor, fixed) |
| NIST CSF 2.0 | PR.AA-05 | Access permissions and authorizations are managed | AI platform privilege boundaries require the same rigor as conventional cloud IAM | Organizational — verify |
| NIST AI RMF | MAP 5.1 | Likelihood and magnitude of impacts documented | Platform-level authentication risk in AI tooling not identified prior to disclosure | Gap (vendor) |
| ISO 42001 | 8.4 | AI system impact assessment | Organizations should independently verify impact-assessment scope covers platform authentication risk | Organizational — verify |

## Control Narrative
Both findings are conventional authentication/input-validation control failures (missing-auth, command injection) that happen to sit inside AI-specific platforms, which is precisely the pattern this program has flagged as a recurring theme across recent weeks: AI feature expansion (Foundry's agent-building capabilities, Copilot's deepening M365 integration) is introducing new privileged functions and command-execution paths faster than the authentication and input-validation discipline applied to conventional enterprise software is being extended to cover them. This is the second consecutive week this program has logged a critical Azure AI-platform trust-boundary finding (following last week's Cosmos DB CosmosEscape case), which this program recommends treating as a standing watch item — organizations with significant investment in Azure AI Foundry or Copilot should request Microsoft's AI-platform security roadmap and ask specifically how authentication parity is being verified across newly shipped AI features.

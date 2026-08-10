# Control Mapping
## 2026-08-AWS-Bulletin-CoreBreak-AgentToolInvocationBypass

## Applicable Frameworks
NIST AI RMF and ISO 42001 as the primary AI-system governance frameworks; MITRE ATLAS for AI-specific threat-technique mapping; NIST CSF 2.0 and NIST 800-53 Rev 5 for enterprise access-enforcement control specificity.

## Control Mapping Table
| Framework | Control ID | Control Name | Applicability | Gap / Status |
|---|---|---|---|---|
| NIST AI RMF | MAP 1.1 | AI system context and boundaries are understood | Root failure is a boundary-confusion between "model decided" and "data shaped like model decided" | Gap |
| NIST AI RMF | MANAGE 4.1 | Risk treatment plans for third-party AI components | Organizations using any of the four affected SDKs need a documented treatment record for this class | Gap |
| NIST AI RMF | GOVERN 1.3 | Processes for AI risk are integrated into organizational risk management | Architectural agent-authorization patterns should be reviewed as part of standing AI governance, not only post-disclosure | Partial |
| ISO 42001 | 6.1.2 | AI risk assessment | In-house agent systems require re-assessment against this specific failure mode | Gap |
| ISO 42001 | 8.4 | AI system impact assessment | Impact assessment for agentic systems should explicitly consider tool-invocation authorization boundaries | Gap |
| NIST 800-53 | AC-3 | Access Enforcement | Applied at the AI-agent-to-tool boundary: tool execution must require verified, specific authorization | Gap (architectural) |
| NIST CSF 2.0 | PR.AA-05 | Access permissions are defined and enforced incorporating least privilege | Agents should hold only the tools/credentials required for their task, limiting blast radius when authorization logic fails | Partial |
| MITRE ATLAS | ML Model Access (tactic) | Unauthorized access to agent tool-execution capability bypassing model mediation | Directly applicable |

## Control Narrative
This case is best used as a governance-and-architecture teaching example rather than a routine patch item: three independent engineering organizations (AWS, Google, Vercel) each built agent-to-tool authorization logic that trusted the *shape* of incoming data rather than verifying its *provenance*, and none of the three caught it during their own security review process — it took an external researcher presenting a cross-platform pattern at a public conference. The unifying remedy each vendor converged on independently — binding tool execution to a specific, verified, single-use authorization tied to an observed model event, rather than trusting a system-prompt-level or model-response-shaped instruction — is a design principle GRC and AI governance teams should require of *any* internally-built or vendor agentic AI system going forward, documented explicitly in AI system design-review checklists per NIST AI RMF MAP 1.1 and ISO 42001 6.1.2.

For CISSP/AI-governance-certification-relevant framing: this is a clean real-world illustration of why "the model is aligned/safe" is an insufficient control when the actual authorization decision can be reached through a path that never involves the model at all. Any control relying solely on model-level behavior (system prompts, content filters, RLHF alignment) provides zero protection against this class of finding, which is why NIST AI RMF's MANAGE function explicitly calls for risk treatment at the system/architecture level, not only the model level.

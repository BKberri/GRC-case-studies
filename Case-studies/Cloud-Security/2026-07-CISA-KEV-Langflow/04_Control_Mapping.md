# Control Mapping — Langflow AI Agent Platform Authorization Bypass

| Framework | Control/Clause | Application to This Case |
|---|---|---|
| **NIST AI RMF** | GOVERN 1.1 — AI risk management processes established | Formalize AI agent platform security as a standing AI risk management item |
| **NIST AI RMF** | MAP 4.1 — Risks/benefits mapped for third-party AI components | Langflow as a third-party AI agent-orchestration component requiring risk mapping |
| **NIST AI RMF** | MANAGE 2.3 / 4.1 — AI system incidents responded to/managed; post-deployment risks monitored | Incident response and ongoing monitoring for hijacked-agent scenarios |
| **ISO/IEC 42001:2023** | Clause 6.1.2 — AI risk assessment | Assess risk of each deployed agent flow based on its tool/credential scope |
| **ISO/IEC 42001:2023** | Clause 8.1 — Operational planning/control | Formal operational control over AI agent authorization and access |
| **NIST CSF 2.0** | PR.AA-05 — Access permissions/authorizations managed | Enforce flow-ownership checks; audit who can execute which flows |
| **NIST CSF 2.0** | DE.CM-09 — Computing hardware/software monitored | Monitor flow-execution logs for cross-user access patterns |
| **NIST 800-53 Rev 5** | AC-3 — Access Enforcement | Root-cause control gap this CVE represents |
| **NIST 800-53 Rev 5** | IA-2 — Identification/Authentication | Confirm authentication alone is insufficient without authorization/ownership checks |
| **NIST 800-53 Rev 5** | SI-2 — Flaw Remediation | Patch to Langflow 1.9.2+ |
| **EU AI Act** | Article 9 / Article 15 — Risk management system; accuracy, robustness, and cybersecurity | Applicable where the affected instance is in scope of a high-risk AI system |

## Gap Assessment
Most organizations' AI governance programs are still built around model-level risk (bias, hallucination, data handling) and have not yet extended standard access-control and vulnerability-management rigor to the orchestration layer that grants AI agents their tool access. This finding should prompt a specific review of whether AI agent platforms are covered by existing IAM and vulnerability management processes with the same discipline applied to traditional application infrastructure.

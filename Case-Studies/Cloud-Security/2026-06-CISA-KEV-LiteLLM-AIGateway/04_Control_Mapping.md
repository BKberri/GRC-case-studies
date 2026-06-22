# Control Mapping — LiteLLM AI Gateway Multiple Vulnerabilities

| Framework | Control/Clause | Application to This Case |
|---|---|---|
| **NIST AI RMF** | GOVERN 1.1 — AI risk management processes established | Treat AI gateway security as a formal AI risk management item |
| **NIST AI RMF** | MANAGE 2.3 — AI system incidents responded to/managed | Incident response process for the gateway compromise |
| **NIST AI RMF** | MAP 4.1 — Risks/benefits mapped for third-party AI components | LiteLLM as a third-party AI infrastructure component requiring risk mapping |
| **ISO/IEC 42001:2023** | Clause 8.1 — Operational planning/control | Formal control over AI system operational risk, including gateway security |
| **ISO/IEC 42001:2023** | Clause 6.1 — Risk treatment | Document risk treatment plan for this finding |
| **NIST CSF 2.0** | PR.AA-01 — Identities/credentials managed | Rotate all API keys/credentials proxied through the gateway |
| **NIST CSF 2.0** | DE.CM-09 — Computing hardware/software monitored | Monitor gateway access logs and model-usage volume for anomalies |
| **NIST 800-53 Rev 5** | SI-2 — Flaw Remediation | Patch LiteLLM to current release |
| **NIST 800-53 Rev 5** | IA-2 — Identification/Authentication | Remediate authentication bypass |
| **NIST 800-53 Rev 5** | SC-7 — Boundary Protection | Restrict gateway egress to mitigate SSRF |
| **EU AI Act** | Article 9 — Risk management system | Where gateway is in scope of a high-risk AI system supply chain |

## Gap Assessment
Many organizations have not yet extended formal vulnerability management and incident response processes to cover AI infrastructure components like LLM gateways with the same rigor applied to traditional IT systems. This finding should prompt a review of whether AI infrastructure is fully captured within the existing vulnerability management and AI governance programs.

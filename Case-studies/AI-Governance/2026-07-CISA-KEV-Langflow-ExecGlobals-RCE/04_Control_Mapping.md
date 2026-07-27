# Control Mapping
## Langflow Unauthenticated Root RCE via `exec_globals` (CVE-2026-0770)

## Applicable Frameworks
This is an AI/LLM agent-infrastructure finding with a direct cloud-credential-theft component, so the mapping draws from both the AI governance track (NIST AI RMF, ISO 42001, EU AI Act) and the standard IT/cloud track (NIST CSF 2.0, NIST 800-53, MITRE ATT&CK) to capture both the platform-governance gap and the technical control failure.

## Control Mapping Table
| Framework | Control ID | Control Name | Applicability | Gap / Status |
|---|---|---|---|---|
| NIST AI RMF | MAP 4.1 | Risks and benefits mapped for third-party/internal AI components | Organization must know which AI tools (Langflow instances) are deployed to react to KEV advisories | Gap |
| NIST AI RMF | GOVERN 1.1 | AI risk management processes established and integrated | Governs whether agentic-AI tooling is subject to the same patch/vuln management SLAs as core infrastructure | Partial |
| NIST AI RMF | MANAGE 2.3 | AI system incidents responded to and managed | Determines speed of credential rotation and forensic response post-compromise | Gap |
| ISO/IEC 42001 | Clause 8.1 | Operational planning and control of AI system risk | Requires documented control over AI-system deployment configuration (endpoint exposure, authentication) | Gap |
| NIST CSF 2.0 | PR.AA-01 / DE.CM-09 | Identities/credentials managed; computing hardware/software monitored | Endpoint required no authentication and was internet-reachable without detection | Gap |
| NIST 800-53 Rev 5 | IA-2, AC-3, SC-7 | Identification/Authentication; Access Enforcement; Boundary Protection | The specific control failures exploited by this CVE | Gap (pre-patch) |
| NIST 800-53 Rev 5 | SI-2 | Flaw Remediation | Determines time-to-patch once vendor fix is available | Addressed (once patched) |
| MITRE ATT&CK | T1190, T1552.005 | Exploit Public-Facing Application; Unsecured Credentials: Cloud Instance Metadata API | TTP mapping for the observed attack chain | N/A — detective reference |

## Control Narrative
This finding illustrates a control gap specific to fast-moving internal AI adoption: teams stand up agentic-AI tooling like Langflow with the same operational urgency as a hackathon project, but without routing it through the same asset-inventory, network-exposure-review, and patch-management processes applied to production infrastructure. NIST AI RMF's MAP and GOVERN functions exist precisely to close this gap — an organization cannot apply IA-2/AC-3/SC-7 technical controls to an asset it does not know exists or does not treat as in-scope. Preventive controls here are boundary protection (SC-7: the validation endpoint should never be reachable without a VPN, private network, or authentication gate) and identification/authentication (IA-2: even internal tooling should not expose unauthenticated code-execution paths). Detective controls are monitoring (DE.CM-09) for anomalous requests to AI-tooling endpoints — a category most SIEM/EDR deployments do not yet instrument by default. A mature control environment treats every internally-adopted AI agent platform as a Tier-1 asset in the vulnerability management program from day one of deployment, not after its first KEV listing.

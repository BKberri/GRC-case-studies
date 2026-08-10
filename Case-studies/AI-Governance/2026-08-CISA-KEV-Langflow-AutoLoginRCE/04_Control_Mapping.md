# Control Mapping
## 2026-08-CISA-KEV-Langflow-AutoLoginRCE

## Applicable Frameworks
NIST AI RMF and ISO 42001 for AI-system-specific governance and risk treatment; NIST CSF 2.0 and NIST 800-53 Rev 5 for enterprise control specificity; ISO 27001:2022 Annex A and CIS Controls v8 for baseline application-security controls.

## Control Mapping Table
| Framework | Control ID | Control Name | Applicability | Gap / Status |
|---|---|---|---|---|
| NIST AI RMF | MAP 5.1 | Third-party AI system risks are identified and characterized | Requires organizations to track repeat-CVE AI platforms as a standing risk category, not a one-off patch item | Gap |
| NIST AI RMF | GOVERN 1.1 | Policies for AI risk management are in place | AI tooling onboarding should require a security review of default authentication posture before production use | Gap |
| ISO 42001 | 8.4 | AI system impact assessment | Impact assessment should account for every credential/connector an AI workflow platform is wired to, not just the platform itself | Partial |
| NIST 800-53 | IA-2 | Identification and Authentication (Organizational Users) | `auto_login` endpoint bypasses authentication entirely for privileged sessions | Gap (vendor default) |
| NIST 800-53 | SI-2 | Flaw Remediation | Third Langflow CVE in 90 days indicates need for a documented, expedited patch SLA specific to this platform | Gap (process) |
| NIST CSF 2.0 | PR.PS-01 | Configuration management practices are established | Default "auto_login" convenience endpoint should have been disabled or network-isolated pre-deployment | Gap |
| ISO 27001 | A.8.5 | Secure Authentication | Requires secure authentication procedures for all system access, including convenience/local-dev endpoints left enabled in production | Gap |
| CIS Controls | CIS 16.1 | Application Software Security | AI/LLM application servers require the same secure-configuration baseline as any other internet-facing web application | Gap |

## Control Narrative
This finding is a compound vulnerability: an authentication-bypass endpoint (intended for local single-user convenience) chained with an intentional-but-dangerous code-execution endpoint (used for validating custom Python components). Neither flaw alone is unusual for a rapidly-iterating open-source AI tooling project, but together they produce unauthenticated RCE — and this is the third such compounding-design issue found in Langflow within 90 days. Organizations running Langflow or comparable AI agent/workflow builders should treat "does this platform expose privileged local-convenience endpoints to the network by default" as a standard pre-deployment security review question (NIST AI RMF GOVERN 1.1), and should require network isolation (binding management/convenience APIs to loopback or an internal-only interface) regardless of vendor patch status, since this class of design pattern has now recurred across three separate CVEs on the same platform.

Detective controls matter here specifically because AI agent platforms are novel enough that many organizations have not yet extended their standard web-application monitoring (WAF rules, anomalous-endpoint-sequence detection) to cover them. A detection rule alerting on any call to an authentication or "auto_login"-named endpoint from a non-loopback source, followed by a code-validation or code-execution endpoint call, would have caught this exploit chain pattern generically — and would likely generalize to future similar findings on this and comparable platforms.

# 2026-08-AWS-Bulletin-CoreBreak-AgentToolInvocationBypass
**Date:** 2026-08-10 | **Source:** AWS Security Bulletin / NIST NVD / Vendor Advisories | **Category:** AI-Governance / Cloud-Security (dual) | **Risk Rating:** Critical

## Summary
Security researchers Hedi Ingber and Aviyam Ivgi (Stealth) presented "CoreBreak" at Black Hat USA 2026 (2026-08-06): a cross-platform vulnerability pattern affecting AI agent infrastructure from AWS, Google, and Vercel, where forged or untrusted data shaped like a model-generated tool call reaches an agent's tool-execution layer without any verification that a legitimate model turn actually authorized it. In several affected paths, the model never runs at all — meaning system prompts, content filters, and model-level guardrails have no opportunity to intervene, because the exploit does not rely on manipulating the model. Affected products: Amazon Bedrock AgentCore's InvokeHarness API (CVE-2026-18830, CVSS v4.0 8.6, already fixed server-side by AWS), Google's Agent Development Kit for Python (CVE-2026-18236, CVSS v4.0 9.3, fixed in ADK 2.5.0), and Vercel AI SDK harness packages for Codex and OpenCode coding agents (CVE-2026-64650 / CVE-2026-64651, CVSS v4.0 6.3 each, fixed in 1.0.29/1.0.28). This is a new, named vulnerability *class* for agentic AI architecture — not an isolated bug — and is the highest-priority AI Governance item in this week's sweep.

## Artifact Index
| File | Description |
|---|---|
| 01_Threat_Intelligence.md | Full technical threat intelligence report |
| 02_Risk_Assessment.md | Risk scoring and control gap analysis |
| 03_BIA.md | Business impact analysis |
| 04_Control_Mapping.md | Framework control mapping |
| 05_Executive_Summary.md | Board/CISO-level summary |
| 06_POAM_Remediation.md | Plan of Action & Milestones |

## Key Facts
- **CVE/Advisory ID:** CVE-2026-18830 (AWS); CVE-2026-18236 (Google); CVE-2026-64650, CVE-2026-64651 (Vercel)
- **CVSS Score:** 8.6 (AWS, v4.0); 9.3 (Google, v4.0); 6.3 each (Vercel, v4.0)
- **Affected Technology:** Amazon Bedrock AgentCore InvokeHarness API; Google Agent Development Kit (ADK) for Python < 2.5.0; Vercel @ai-sdk/harness-codex < 1.0.29 and @ai-sdk/harness-opencode < 1.0.28
- **Frameworks Applied:** NIST AI RMF, ISO 42001, MITRE ATLAS, NIST CSF 2.0, NIST 800-53 Rev 5
- **Exploitation Status:** No confirmed exploitation against live deployments reported as of disclosure; responsibly disclosed to all three vendors with PoC withheld from public release; all three vendors have shipped fixes
- **Disclosure Date:** 2026-08-06 (Black Hat USA 2026)

## Related Cases
First entry in this program specifically addressing an agentic-AI *architectural* vulnerability class spanning multiple cloud/AI vendors simultaneously, rather than a single-vendor CVE. Should be read alongside `AI-Governance/2026-08-CISA-KEV-Langflow-AutoLoginRCE` (also AI agent platform, but a conventional auth-bypass bug rather than an architectural class) when briefing on overall AI agent platform risk posture this quarter.

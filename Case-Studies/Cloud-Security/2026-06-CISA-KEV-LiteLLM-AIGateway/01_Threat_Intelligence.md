# Threat Intelligence Report — LiteLLM AI Gateway Multiple Vulnerabilities

## CVE Details

| Field | Value |
|---|---|
| **CVE IDs** | CVE-2026-42271 (primary/most severe); CVE-2026-47101, CVE-2026-47102, CVE-2026-40217 (related) |
| **Vulnerability Name** | LiteLLM AI Gateway/Proxy — Multiple Vulnerabilities (Authentication Bypass, SSRF, Privilege Escalation, Information Disclosure) |
| **Affected Vendor/Product** | LiteLLM (open-source LLM gateway/proxy used to unify access to multiple AI model providers) |
| **CVSS Score** | CVE-2026-42271: 9.1 (Critical); related CVEs range High-Critical |
| **Disclosure Source** | Obsidian Security research disclosure, 2026-06-11; CISA KEV addition following confirmed active exploitation, week of 2026-06-15 |
| **Exploitation Type** | Authentication bypass allowing unauthorized access to the LLM gateway; downstream risk includes unauthorized model invocation, API key/credential exposure, and potential SSRF against internal network resources reachable via the gateway |

## Exploitation Summary
LiteLLM is a widely adopted open-source gateway/proxy that organizations use to route, authenticate, and meter access to multiple large language model providers (OpenAI, Anthropic, Azure OpenAI, etc.) through a single unified interface. Security researchers at Obsidian Security disclosed a chain of vulnerabilities on 2026-06-11, the most severe of which (CVE-2026-42271) allows authentication bypass against the gateway. CISA subsequently added related CVEs to the KEV catalog after confirming active exploitation in the wild. Because LiteLLM commonly sits between an organization's applications and upstream AI providers — frequently holding or proxying API keys/credentials for those providers — a compromised gateway can expose model-provider credentials, enable unauthorized/unmetered model usage (with direct cost and data-exposure implications), and in some deployment configurations enable SSRF against internal network resources reachable from the gateway host.

## Why This Is Flagged as Highest Priority
Per the GRC Intelligence Monitoring program's standing instruction to treat AI/LLM platform vulnerabilities as highest priority, this finding is included despite the primary disclosure date (2026-06-11) falling just outside the strict 7-day lookback window (2026-06-15 to 2026-06-22). Active-exploitation reporting and CISA's own KEV-related warnings continued through 2026-06-16/06-18, within the monitoring window, and the underlying risk — compromise of AI infrastructure sitting between applications and multiple LLM providers — is squarely within the program's AI governance and security scope. **This is a documented judgment call**, made because the operational risk (live exploitation of AI infrastructure) outweighs strict adherence to the calendar boundary.

## Framework Mapping
- **NIST AI RMF:** GOVERN 1.1 (AI risk management processes), MANAGE 2.3 (AI system incidents responded to and managed), MAP 4.1 (Risks/benefits mapped for third-party AI components)
- **ISO/IEC 42001:2023:** Clause 8.1 (Operational planning/control of AI system risk), Clause 6.1 (Risk treatment)
- **NIST CSF 2.0:** PR.AA-01 (Identity/credential management), DE.CM-09 (Computing hardware/software monitored), PR.DS-02 (Data-in-transit protected)
- **NIST 800-53 Rev 5:** SI-2 (Flaw Remediation), IA-2 (Identification/Authentication), SC-7 (Boundary Protection — SSRF mitigation)
- **EU AI Act:** Article 9 (Risk management system) — relevant where the gateway sits in scope of a high-risk AI system's supply chain

## Recommended Immediate Action
Upgrade LiteLLM to the patched release immediately; rotate all API keys/credentials proxied through the gateway as a precaution; review gateway access logs for unauthorized authentication bypass attempts and unusual model-usage volume/cost spikes; restrict network egress from the gateway host to reduce SSRF blast radius.

## Risk Rating
**Critical** — CVSS 9.1 on the primary CVE, confirmed active exploitation, sits at a high-value chokepoint (AI provider credentials and multi-tenant model access) within the organization's AI infrastructure.

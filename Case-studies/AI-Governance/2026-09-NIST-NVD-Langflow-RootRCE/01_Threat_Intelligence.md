# Threat Intelligence Report
## 2026-09-NIST-NVD-Langflow-RootRCE
**Date:** 2026-09-21 | **Source:** NIST NVD (published 2026-09-14) | **Severity:** Critical | **Category:** AI-Governance / Cloud-Security

## Executive Overview
Langflow is an open-source visual builder for constructing LLM and AI-agent workflows by connecting reusable components — a popular low-code entry point for organizations building custom AI agents. CVE-2026-12944 allows arbitrary Python code execution running as root (UID 0) inside the Langflow container/host, achieved through socket and urllib imports that user-submitted workflow components are permitted to use without adequate sandboxing. Because Langflow instances are frequently deployed inside cloud environments (commonly AWS, given the platform's popularity for cloud-hosted AI agent prototyping), successful exploitation enables credential theft from the cloud instance metadata service via IMDSv1-based SSRF, arbitrary file exfiltration from the host, and lateral movement using any stolen cloud credentials.

## Technical Details
- **CVE ID:** CVE-2026-12944
- **CVSS Score:** 9.6 Critical
- **Affected Vendor/Product/Version:** IBM Langflow OSS, 1.0.0-1.10.0
- **Vulnerability Type:** Server-Side Request Forgery (CWE-918) chained with unsafe code execution — user-submitted workflow components can import `socket` and `urllib`, providing both network access and arbitrary code execution as root within the workflow execution context
- **Exploitation Status:** No CISA KEV listing as of this sweep; NVD-published 2026-09-14
- **Threat Actor Attribution:** None publicly disclosed for this specific CVE
- **MITRE ATLAS Technique IDs:** ML Attack Staging (adversarial workflow component submission), ML Model Access, Exfiltration (credential/file theft)
- **MITRE ATT&CK Technique IDs:** T1552.005 (Cloud Instance Metadata API credential theft), T1078.004 (Valid Accounts: Cloud Accounts)
- **CISA Remediation Due Date:** Not applicable — not KEV-listed as of this sweep

## Affected Technology Context
This is the fifth Langflow-specific security finding this program has logged since June 2026, a frequency notably higher than any other single vendor/product this program tracks. The recurring root cause across all five findings is structurally similar: Langflow's core value proposition — letting users build AI agent workflows by submitting arbitrary reusable components — inherently creates a code-execution surface that is difficult to fully sandbox, and each disclosed CVE has found a new path through that surface (execGlobals, auto-login bypass, and now socket/urllib imports). Organizations running Langflow should treat this as a structural platform risk rather than a series of unrelated bugs, and weight network-level compensating controls (restricting outbound access from Langflow hosts, disabling IMDSv1 in favor of IMDSv2 with hop-limit protections) accordingly.

## Intelligence Source Links
- NVD: https://nvd.nist.gov/vuln/detail/CVE-2026-12944
- IBM Langflow OSS GitHub Security Advisories: https://github.com/langflow-ai/langflow/security/advisories

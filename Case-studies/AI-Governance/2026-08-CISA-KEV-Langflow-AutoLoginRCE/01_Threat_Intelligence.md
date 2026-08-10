# Threat Intelligence Report
## 2026-08-CISA-KEV-Langflow-AutoLoginRCE
**Date:** 2026-08-10 | **Source:** CISA KEV (added 2026-08-04) | **Severity:** Critical | **Category:** AI-Governance / Cloud-Security

## Executive Overview
IBM Langflow (the open-source visual builder for LLM/agent workflows acquired via IBM's purchase of DataStax) ships a REST API endpoint, `/api/v1/auto_login`, intended to simplify local single-user deployments by silently issuing a SUPERUSER session token. The endpoint does not verify that the caller is local, and does not require any credential. An attacker who reaches the endpoint over the network receives a valid SUPERUSER token without authenticating. That token is then accepted by `/api/v1/validate/code`, an endpoint that evaluates submitted Python source using `exec()` to validate custom-component code inside Langflow flows. Chaining the two endpoints gives an unauthenticated remote attacker arbitrary Python code execution in the context of the Langflow server process on any internet-reachable, default-configuration instance.

## Technical Details
- **CVE ID:** CVE-2026-9198
- **CVSS Score:** 9.8 (Critical) — CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H (network vector, low complexity, no privileges or user interaction required)
- **Affected Vendor/Product/Version:** IBM Langflow OSS versions 1.0.0 through 1.10.0; fixed in 1.10.1
- **Vulnerability Type:** Improper Authentication combined with Code Injection (CWE-306 / CWE-94)
- **Exploitation Status:** Actively exploited in the wild; added to CISA KEV 2026-08-04. Public exploit code and a working PoC chain are circulating (GitHub: 0xgh057r3c0n/CVE-2026-9198).
- **Threat Actor Attribution:** Not publicly attributed at time of this report; exploitation observed is consistent with opportunistic internet-wide scanning for exposed Langflow instances rather than a targeted campaign.
- **MITRE ATT&CK Technique IDs:** T1190 (Exploit Public-Facing Application), T1078 (Valid Accounts — forged SUPERUSER token), T1059.006 (Command and Scripting Interpreter: Python)
- **MITRE ATLAS Relevance:** Falls under the ML Model Access tactic — unauthorized platform-level access to an AI workflow/agent builder that, once compromised, exposes any credentials, data connectors, or downstream tool integrations configured within the victim's flows.
- **IOCs:** No vendor-published IOC list at time of writing; monitor Langflow server logs for anomalous calls to `/api/v1/auto_login` followed immediately by `/api/v1/validate/code` from the same source IP with no prior authenticated session.
- **CISA Remediation Due Date:** Per standard KEV non-ransomware/non-emergency timeline; confirm exact due date against the live catalog entry, as CISA record layout did not surface a distinct due date separate from the addition date in this sweep.

## Affected Technology Context
Langflow is deployed by organizations building internal LLM-powered automation, chatbots, and agentic workflows — it typically holds API keys, database credentials, and third-party service connectors (email, CRM, cloud storage) configured as part of its flows. Because the exploit chain grants a SUPERUSER-equivalent session, a successful attacker does not merely gain code execution on the host — they gain the ability to read, export, or repurpose every credential and data connection wired into every flow hosted on that instance. This is the third Langflow CVE the program has logged in under three months, following an unauthenticated root RCE via `exec_globals` (CVE-2026-0770, RR-035) and an earlier authorization flaw (CVE-2026-55255, RR-028) — a pattern that should be treated as a platform-level trust concern rather than three isolated bugs.

## Intelligence Source Links
- CISA KEV Alert (Aug 4 batch): https://www.cisa.gov/news-events/alerts/2026/08/04/cisa-adds-three-known-exploited-vulnerabilities-catalog
- GitHub PoC: https://github.com/0xgh057r3c0n/CVE-2026-9198
- SentinelOne vulnerability database: https://www.sentinelone.com/vulnerability-database/cve-2026-9198/
- VulDB entry: https://vuldb.com/vuln/379892
- KEVIntel exploitation tracking: https://kevintel.com/CVE-2026-9198

# Threat Intelligence Report — Langflow Unauthenticated Root RCE via `exec_globals`

## CVE Details

| Field | Value |
|---|---|
| **CVE ID** | CVE-2026-0770 |
| **Vulnerability Name** | Langflow — Inclusion of Functionality from Untrusted Control Sphere (unauthenticated RCE) |
| **Affected Vendor/Product** | Langflow (open-source AI agent/workflow orchestration platform), versions 0 through 1.7.3 |
| **CVSS Score** | 9.8 (Critical) — AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H |
| **Vulnerable Component** | `exec_globals` parameter handling in the `/api/v1/validate/code` endpoint |
| **Date Added to KEV** | 2026-07-21 |
| **CISA Remediation Due Date** | 2026-07-24 (3-day emergency mandate under BOD 26-04) |
| **Exploitation Type** | Unauthenticated remote code execution as root — no credentials, no user interaction required |
| **Discovered By** | Trend Micro (Zero Day Initiative), tracked internally as ZDI-CAN-27325 / advisory ZDI-26-036 |

## Executive Overview
Langflow's `/validate` endpoint accepts an `exec_globals` parameter intended to scope variables available during code validation. The endpoint fails to constrain the origin of that parameter, allowing an unauthenticated attacker to inject and execute arbitrary code in the context of the root account — the platform's own build/execution model becomes the attack primitive. Because Langflow is deployed to orchestrate LLM calls, tool invocations, and multi-step autonomous agent tasks, a compromised instance hands the attacker not just a shell but a foothold inside whatever cloud, data, and tool-access fabric the platform was wired into.

## Technical Details
- **CVE ID:** CVE-2026-0770
- **CVSS 3.1:** 9.8 Critical (AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H)
- **Affected vendor/product/version:** Langflow, all versions 0 through 1.7.3
- **Vulnerability type:** Improper control of code generation / inclusion of functionality from an untrusted control sphere — attacker-supplied `exec_globals` is passed into the validation endpoint's code-execution path with no authentication check and no sandboxing of the resulting execution context
- **Exploitation status:** Actively exploited. KEVIntel sensors first observed exploitation attempts on 2026-06-27 — roughly three weeks before the KEV listing — recording over 220 attempts from 64 unique source IPs
- **Threat actor attribution:** Not formally attributed to a named group; telemetry is consistent with opportunistic, mass internet-scanning activity rather than a single targeted campaign
- **MITRE ATT&CK:** T1190 (Exploit Public-Facing Application), T1552.005 (Unsecured Credentials: Cloud Instance Metadata API), T1611 (Escape to Host — root-level code execution on the underlying container/VM)
- **MITRE ATLAS:** AML.T0010 (ML Supply Chain Compromise — via a compromised agent-orchestration dependency), AML.T0048 (External Harms — unauthorized actions taken using the compromised agent's tool access)
- **IOCs:** KEVIntel-observed payloads attempting to (1) execute reconnaissance and command-execution checks, (2) download second-stage scripts, and (3) access environment variables, cloud instance metadata, and credential files — consistent with AWS credential and container metadata theft. Historical requests of interest: `/api/v1/validate/code`
- **CISA remediation due date:** 2026-07-24 (KEV added 2026-07-21; 3-business-day BOD 26-04 emergency mandate)

## Affected Technology Context
Langflow is a low-code visual builder for LLM-powered agents and workflows, widely adopted by enterprises and individual developers experimenting with agentic AI. Because flows are commonly configured with API keys, cloud credentials, and tool-execution permissions, an unauthenticated RCE at the platform layer is architecturally equivalent to handing an attacker the keys to every credential and tool the platform touches — not merely the host it runs on. Organizations running Langflow on cloud compute (the KEVIntel telemetry shows attackers specifically probing for AWS credentials and container metadata) should treat any internet-facing, unpatched instance as presumptively compromised until proven otherwise. This is Langflow's fourth actively-exploited KEV entry since May 2025, following CVE-2025-3248 (subsequently weaponized in "agentic ransomware" by the JadePuffer gang to autonomously dump PostgreSQL databases), CVE-2026-33017, and CVE-2026-55255 (RR-028, logged 2026-07-13) — an unusually dense concentration of critical, unauthenticated findings in a single agentic-AI product line.

## Intelligence Source Links
- CISA KEV addition: https://www.cisa.gov/news-events/alerts/2026/07/21/cisa-adds-four-known-exploited-vulnerabilities-catalog
- NVD: https://nvd.nist.gov/vuln/detail/CVE-2026-0770
- Zero Day Initiative advisory: https://www.zerodayinitiative.com/advisories/ZDI-26-036/
- GitHub Security Advisory: https://github.com/advisories/GHSA-g22f-v6f7-2hrh
- BleepingComputer: https://www.bleepingcomputer.com/news/security/cisa-orders-feds-to-patch-actively-exploited-langflow-rce-flaw/
- KEVIntel sensor telemetry: https://kevintel.com/CVE-2026-0770

## Risk Rating
**Critical** — CVSS 9.8, unauthenticated root-level RCE, confirmed active exploitation with credential-theft payloads, 3-day federal remediation mandate, and the fourth KEV-listed critical flaw in this platform in fourteen months.

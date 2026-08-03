# Threat Intelligence Report
## 2026-08-MSRC-Azure-CosmosDB-CrossTenantEscape
**Date:** 2026-08-03 | **Source:** MSRC / Microsoft Security Advisory (published 2026-07-30) | **Severity:** Critical | **Category:** Cloud-Security

## Executive Overview
Wiz Research disclosed "CosmosEscape" (CVE-2026-66803), a critical improper-access-control vulnerability in Azure Cosmos DB's Gremlin API that allowed a crafted query to escape the service's multi-tenant query sandbox and achieve code execution on a shared gateway component. From that foothold, an attacker could retrieve a platform-wide signing secret and use it to derive the primary access key of any customer's Cosmos DB account on demand — a cross-tenant compromise path that, if exploited maliciously, could have granted an attacker full read/write access to any Cosmos DB database on the Azure platform, including Microsoft's own internal databases. Microsoft states it found no evidence of customer impact and has fully remediated the issue platform-wide; no customer action is required for this specific finding.

## Technical Details
- **CVE ID:** CVE-2026-66803
- **CVSS Score:** No official base score published by Microsoft at time of advisory; the disclosed CVSS 3.1 vector components (`AV:N/AC:L/PR:N/UI:N/S:C/C:H/I:H/A:H`) place this in the Critical range consistent with unauthenticated, low-complexity, scope-changing, full-impact compromise
- **Affected Vendor/Product/Version:** Microsoft Azure Cosmos DB — Gremlin API / multi-tenant gateway infrastructure (platform-side; no customer-deployed software version applies)
- **Vulnerability Type:** Improper Access Control / Sandbox Escape leading to Remote Code Execution
- **Exploitation Status:** No known exploit — responsibly disclosed by Wiz Research; Microsoft reports no evidence of in-the-wild exploitation or customer impact
- **Threat Actor Attribution:** N/A — researcher-discovered, not observed in active attacks
- **MITRE ATT&CK Technique IDs:** T1611 (Escape to Host — sandbox/container escape analog), T1552.005 (Unsecured Credentials: Cloud Instance Metadata API — analogous platform-secret exposure pattern), T1078.004 (Valid Accounts: Cloud Accounts — downstream risk if a derived key were misused)
- **IOCs:** Not applicable — vulnerability was fully remediated by Microsoft prior to public disclosure; no customer-observable indicators
- **CISA Remediation Due Date:** Not applicable — not a KEV entry; platform-side fix, no customer patch required

## Affected Technology Context
Azure Cosmos DB is Microsoft's flagship globally-distributed, multi-model NoSQL database, widely used for e-commerce catalogs, IoT telemetry, gaming state, and financial transaction data across thousands of enterprise tenants. The exploit chain — a Gremlin query escaping its sandbox, achieving code execution on a shared multi-tenant gateway, and surfacing a platform-wide signing secret — is architecturally significant because it demonstrates that a single flaw in shared cloud-provider infrastructure can theoretically compromise tenant isolation across an entire hyperscaler service, independent of any customer misconfiguration. This case is a direct illustration of the cloud shared-responsibility model's provider-side half: no amount of customer-side hardening (network rules, IAM policy, encryption at rest) would have prevented or detected this specific exposure, because the vulnerability lived entirely within Microsoft's multi-tenant control plane. Wiz reported the issue to Microsoft in November 2025; Microsoft deployed an emergency hotfix within two days and completed the full platform-wide remediation, including elimination of the platform-wide key architecture itself, by July 2026.

## Intelligence Source Links
- Wiz Research writeup: https://www.wiz.io/blog/cosmosescape-taking-over-every-database-in-azure-cosmos-db
- The Hacker News coverage: https://thehackernews.com/2026/07/azure-cosmos-db-flaw-exposed-platform.html
- SecurityWeek coverage: https://www.securityweek.com/critical-flaw-led-to-azure-cosmos-db-pwnage/
- SC Media coverage: https://www.scworld.com/news/microsoft-patches-azure-cosmos-db-stopping-widespread-cross-service-attack
- Microsoft Security Advisory (via TheWindowsUpdate.com summary): https://thewindowsupdate.com/2026/07/30/cve-2026-66803-azure-cosmos-db-remote-code-execution-vulnerability/

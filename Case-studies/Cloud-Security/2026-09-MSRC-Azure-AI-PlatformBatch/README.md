# 2026-09-MSRC-Azure-AI-PlatformBatch
**Date:** 2026-09-21 | **Source:** Microsoft Security Response Center | **Category:** AI-Governance (dual: Cloud-Security) | **Risk Rating:** High

## Summary
Microsoft disclosed a mid-cycle batch of Azure AI-platform vulnerabilities around 2026-09-17 to 2026-09-19, headlined by two maximum-severity missing-authentication elevation-of-privilege flaws: CVE-2026-85889 in Azure AI Foundry (CVSS 10.0) and CVE-2026-85885 in Microsoft 365 Copilot (CVSS 9.9, command injection). Both were fixed server-side by Microsoft with no customer action required, and both were responsibly disclosed with no confirmed in-the-wild exploitation. This is the second consecutive week this program has logged a critical Azure AI-platform disclosure (following last week's Azure Cosmos DB "CosmosEscape" cross-tenant finding), reinforcing an emerging pattern of rapid AI-feature expansion outpacing trust-boundary maturity across Microsoft's cloud AI stack.

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
- **CVE/Advisory ID:** CVE-2026-85889 (Azure AI Foundry); CVE-2026-85885 (Microsoft 365 Copilot)
- **CVSS Score:** CVE-2026-85889: 10.0 Critical (CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:C/C:H/I:H/A:H, CWE-306); CVE-2026-85885: 9.9 Critical (CVSS:3.1/AV:N/AC:L/PR:L/UI:N/S:C/C:H/I:H/A:H, CWE-77)
- **Affected Technology:** Azure AI Foundry (all versions); Microsoft 365 Copilot (all versions)
- **Frameworks Applied:** NIST AI RMF, ISO 42001, NIST CSF 2.0, NIST 800-53 Rev 5
- **Exploitation Status:** No confirmed in-the-wild exploitation for either CVE; both responsibly disclosed and remediated server-side by Microsoft before this report
- **Vendor Due Date:** No customer patching required — cloud-side fix applied by Microsoft

## Related Cases
Related to four additional Azure elevation-of-privilege CVEs disclosed in the same batch window (Microsoft Fabric CVE-2026-69843, Azure Billing CVE-2026-62874, Azure Database for PostgreSQL CVE-2026-85878, Azure Cosmos DB CVE-2026-87701 — all CVSS 9.6-10.0, all server-side Microsoft-remediated), logged as register-only entries this run given they are non-AI-platform-specific and follow the identical "Microsoft-fixed, no customer action" remediation pattern. Also connects to last week's `2026-08-MSRC-Azure-CosmosDB-CrossTenantEscape` case in this program's history, continuing the observed pattern of Microsoft's AI/cloud feature-expansion trust-boundary gaps.

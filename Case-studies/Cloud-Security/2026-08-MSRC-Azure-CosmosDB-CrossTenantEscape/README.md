# 2026-08-MSRC-Azure-CosmosDB-CrossTenantEscape
**Date:** 2026-08-03 | **Source:** MSRC / Microsoft Security Advisory | **Category:** Cloud-Security | **Risk Rating:** High (governance) / Critical (historical, pre-remediation)

## Summary
Wiz Research disclosed "CosmosEscape" (CVE-2026-66803), a critical vulnerability in Azure Cosmos DB's Gremlin API that could have allowed an attacker to escape the service's multi-tenant sandbox, achieve code execution on a shared gateway, and derive the primary access key for any customer's Cosmos DB account — a hyperscaler-scale cross-tenant compromise path. Microsoft fully remediated the issue platform-wide, including eliminating the platform-wide key architecture, and confirms no evidence of customer impact. This case is documented for third-party/cloud-provider risk management purposes rather than technical remediation, since no customer-side action is required. NIST 800-53 SA-9/CA-3, NIST CSF 2.0 GOVERN function, and ISO 27001 A.5.23/A.5.19 apply. Status: vendor-risk documentation and confirmation tracking in progress per POA&M.

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
- **CVE/Advisory ID:** CVE-2026-66803
- **CVSS Score:** Not officially published; disclosed vector consistent with Critical range
- **Affected Technology:** Microsoft Azure Cosmos DB (Gremlin API / multi-tenant gateway, platform-side)
- **Frameworks Applied:** NIST CSF 2.0, NIST 800-53 Rev 5, ISO 27001:2022, CIS Controls v8
- **Exploitation Status:** No known exploit — responsibly disclosed and fully remediated pre-publication
- **CISA Due Date:** Not applicable (not a KEV entry)

## Related Cases
Related to `Cloud-Security/2026-06-MSRC-Azure-HorizonDB` as a second illustration of provider-side Azure data-platform vulnerabilities within this reporting period; relevant to any case involving cloud shared-responsibility-model analysis.

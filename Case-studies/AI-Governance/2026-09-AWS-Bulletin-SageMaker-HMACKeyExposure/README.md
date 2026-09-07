# 2026-09-AWS-Bulletin-SageMaker-HMACKeyExposure
**Date:** 2026-09-07 | **Source:** AWS Security Bulletins | **Category:** AI-Governance (dual: Cloud-Security) | **Risk Rating:** High

## Summary
Amazon SageMaker Python SDK versions through 3.11.0 (v3 line) and 2.256.0 (v2 line) stored an HMAC signing key in cleartext within the `@step` and `@remote` decorator pipeline component's API responses (CVE-2026-83551, CVSS 7.2). Any authenticated user able to read those API responses on a shared AWS account — for example, a lower-privileged data scientist sharing a SageMaker Studio domain or pipeline environment with other teams — could extract another user's HMAC signing key and forge signatures to execute arbitrary code within that other user's ML pipeline execution context. AWS published the fix (v3.11.0 and v2.256.0) on 2026-09-01. This is a cross-tenant/cross-user privilege-escalation pattern within a shared AI/ML platform account, distinct from but conceptually related to this week's AWS Labs MCP-server findings (see `2026-09-AWS-Bulletin-MCP-Server-InputValidation`).

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
- **CVE/Advisory ID:** CVE-2026-83551 (AWS Bulletin 2026-093-AWS)
- **CVSS Score:** 7.2 (High) — CVSS:3.1/AV:N/AC:L/PR:H/UI:N/S:U/C:H/I:H/A:H
- **Affected Technology:** Amazon SageMaker Python SDK v3.11.0 and earlier; v2.256.0 and earlier (fixed in those respective versions)
- **Frameworks Applied:** NIST AI RMF, ISO 42001, NIST CSF 2.0, NIST 800-53 Rev 5
- **Exploitation Status:** No confirmed in-the-wild exploitation; requires authenticated (PR:H — high-privilege prerequisite per CVSS vector) access to the shared AWS account
- **Vendor Due Date:** No CISA KEV listing; AWS recommends immediate SDK upgrade

## Related Cases
Third AWS-published AI/ML-platform finding logged this run alongside `AI-Governance/2026-09-AWS-Bulletin-MCP-Server-InputValidation`. Where the MCP-server findings concern an AI agent's trust boundary against the systems it acts on, this finding concerns a multi-tenant trust boundary between different human users sharing the same SageMaker environment — both point to the same underlying program observation: AWS's rapid AI/ML tooling expansion (SageMaker pipelines, agent MCP servers) is outpacing the maturity of the trust-boundary and least-privilege controls around who or what can act on whose behalf within a shared account.

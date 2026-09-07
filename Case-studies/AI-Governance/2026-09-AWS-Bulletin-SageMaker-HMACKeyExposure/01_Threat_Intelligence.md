# Threat Intelligence Report
## 2026-09-AWS-Bulletin-SageMaker-HMACKeyExposure
**Date:** 2026-09-07 | **Source:** AWS Security Bulletin 2026-093-AWS (published 2026-09-01) | **Severity:** High | **Category:** AI-Governance / Cloud-Security

## Executive Overview
Amazon SageMaker's `@step` and `@remote` Python SDK decorators let data scientists turn ordinary Python functions into steps of a managed ML pipeline or into jobs that run remotely on SageMaker-managed compute, without hand-writing pipeline definition code. To coordinate execution, the SDK's pipeline component issues an HMAC signing key used to authenticate requests within that pipeline's execution context. CVE-2026-83551 found that this signing key was stored and returned in cleartext within API responses reachable by any authenticated user on the AWS account — not scoped to the key's owning user. An attacker with ordinary (not necessarily administrative) authenticated access to a shared SageMaker Studio domain, multi-user pipeline environment, or shared AWS account could read another user's HMAC key from these responses and use it to forge valid signatures, allowing them to execute arbitrary code within that other user's pipeline execution context — effectively a cross-user privilege escalation and code-execution path inside a single shared AWS account's ML platform.

## Technical Details
- **CVE ID:** CVE-2026-83551
- **CVSS Score:** 7.2 (High) — CVSS:3.1/AV:N/AC:L/PR:H/UI:N/S:U/C:H/I:H/A:H (network vector, low complexity, but requires the attacker already hold high-level authenticated privileges on the account — this is a lateral/cross-tenant escalation, not an unauthenticated remote exploit)
- **Affected Vendor/Product/Version:** Amazon SageMaker Python SDK v3.11.0 and earlier; v2.256.0 and earlier; fixed in v3.11.0 and v2.256.0 respectively (published 2026-09-01)
- **Vulnerability Type:** Cleartext storage of sensitive information (CWE-312) — HMAC signing key exposed via API response instead of being scoped/redacted to its owning principal
- **Exploitation Status:** No confirmed in-the-wild exploitation; AWS-disclosed and patched proactively
- **Threat Actor Attribution:** None — vendor/researcher-disclosed hardening fix
- **MITRE ATT&CK Technique IDs:** T1552 (Unsecured Credentials) for the cleartext key exposure; T1078 (Valid Accounts) once the forged signature is used to impersonate another user's pipeline context
- **IOCs:** Pipeline or `@remote` job executions authenticated with an HMAC signature not attributable to the expected owning principal; unexpected cross-user pipeline execution activity in SageMaker CloudTrail logs
- **CISA Remediation Due Date:** Not applicable — not KEV-listed

## Affected Technology Context
This finding matters most in organizations that run shared, multi-tenant SageMaker environments — a common pattern where a single AWS account or SageMaker Studio domain hosts multiple data science teams or individual practitioners with varying trust levels, on the assumption that SageMaker's own access controls isolate each user's pipeline executions from the others. CVE-2026-83551 breaks that assumption specifically for the `@step`/`@remote` decorator pattern, which has become a popular lightweight alternative to full SageMaker Pipelines definitions precisely because it lowers the barrier for individual data scientists to productionize ad hoc ML code. Any organization that adopted `@step`/`@remote` for that reason should assume broader usage — and broader exposure — than a formal pipeline-governance review might expect, since these decorators are often used experimentally, outside the change-management process applied to registered production pipelines.

## Intelligence Source Links
- AWS Security Bulletin 2026-093-AWS (referenced via CVE record): https://radar.offseq.com/threat/cve-2026-83551-cwe-312-cleartext-storage-of-sensitive-information-in-aws-sagemaker-python-sdk-8e0ba1195c61e993
- NVD: https://nvd.nist.gov/vuln/detail/CVE-2026-83551
- AWS Security Bulletins index: https://aws.amazon.com/security/security-bulletins/

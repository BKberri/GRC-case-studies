# Risk Assessment — CVE-2026-48282 (Adobe ColdFusion RDS Path Traversal RCE)

## Risk Statement
An unauthenticated path traversal vulnerability in Adobe ColdFusion's RDS FILEIO handler allows arbitrary file write and, via a CFML web shell, full remote code execution as the ColdFusion service account — potentially SYSTEM-level access on Windows deployments — on any internet-reachable ColdFusion instance with RDS authentication disabled.

## Likelihood: 5/5 (Actively exploited in the wild, within hours of disclosure)
- Confirmed active exploitation detected by KEVIntel honeypots roughly two hours after technical analysis went public.
- No authentication required when RDS authentication is disabled — a common production misconfiguration.
- CISA KEV addition and multiple national CERT alerts (Canada, Belgium) confirm widespread, ongoing exploitation.

## Impact: 5/5 (Severe — unauthenticated RCE as SYSTEM-level service account)
- Successful exploitation grants code execution with ColdFusion service account privileges, commonly SYSTEM on Windows — a full host compromise, not a limited-scope flaw.
- ColdFusion applications frequently sit in front of business-critical data (databases, file stores, integrated backend systems), so host compromise carries direct data-exposure and lateral-movement risk.
- Long ColdFusion deployment lifespans mean vulnerable, unpatched instances can persist well past this remediation window if not actively tracked.

## Risk Score: 25 (5 × 5) — **Critical**

## Inherent Risk: Critical
## Residual Risk: Medium (patching closes the flaw; residual risk from any pre-patch compromise requires web-shell/forensic sweep to fully retire)

## Business Risk Translation
This is a full-host-compromise vulnerability on a platform that frequently runs mission-critical enterprise applications with long operational lifespans. The gap between patch availability (2026-06-30) and active mass exploitation (within ~2 hours of public technical detail) illustrates why "patch promptly" is not sufficient guidance — organizations need pre-established emergency patch pathways for CVSS 10.0 unauthenticated RCE findings specifically.

## Compliance Note
Where ColdFusion applications process regulated data (PII, payment data, healthcare data), a confirmed compromise may trigger breach-notification obligations under applicable regulations (state breach notification laws, GLBA, HIPAA, or similar) — GRC should coordinate with legal/privacy teams immediately if forensic review finds evidence of prior exploitation.

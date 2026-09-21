# 2026-09-AWS-Bulletin-IAM-MultiTenant-Batch
**Date:** 2026-09-21 | **Source:** AWS Security Bulletins | **Category:** Cloud-Security | **Risk Rating:** High

## Summary
AWS published two distinct security bulletins this week both touching identity and multi-tenant isolation boundaries: CVE-2026-86830, an incorrect-privilege-assignment flaw in TEAM (Temporary Elevated Access Management, AWS's open-source sample solution built on IAM Identity Center) that could grant an authenticated application user unintended temporary elevated access to managed AWS accounts; and CVE-2026-86831, a pod-identifier-collision flaw in the aws-network-policy-agent component of Amazon EKS that can bypass NetworkPolicy enforcement across Kubernetes namespaces sharing a hyphen-adjacent naming pattern. Both were responsibly disclosed with fixes available and no confirmed in-the-wild exploitation, but both represent trust-boundary gaps in tools organizations use specifically to manage least-privilege access — TEAM for temporary elevated AWS account access, and EKS Network Policy Agent for network-level tenant isolation within a cluster.

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
- **CVE/Advisory ID:** CVE-2026-86830 (AWS Bulletin 2026-112-AWS); CVE-2026-86831 (AWS Bulletin 2026-113-AWS)
- **CVSS Score:** Not published numerically in either bulletin; AWS labels CVE-2026-86831 "Important — requires attention"
- **Affected Technology:** TEAM (Temporary Elevated Access Management) prior to v1.5.1; Amazon VPC CNI Managed Add-on v1.14.0-1.22.3 and Network Policy Agent before v1.4.0
- **Frameworks Applied:** NIST CSF 2.0, NIST 800-53 Rev 5, ISO 27001:2022, CIS Controls v8, AWS Well-Architected Security Pillar
- **Exploitation Status:** No active exploitation reported for either CVE; both responsibly disclosed
- **Vendor Due Date:** No CISA KEV listing; AWS recommends upgrading to fixed versions (TEAM v1.5.1+, VPC CNI Add-on v1.22.4+, Network Policy Agent v1.4.0+)

## Related Cases
Continues this program's standing focus on AWS IAM governance and multi-account/multi-tenant isolation findings (see `2026-09-CISA-KEV-Cisco-ISE-AuthBypass` for an analogous API-authorization gap in a non-cloud IAM platform, and prior weeks' AWS Labs MCP-server and SageMaker findings for the broader AWS AI/ML trust-boundary pattern this program tracks).

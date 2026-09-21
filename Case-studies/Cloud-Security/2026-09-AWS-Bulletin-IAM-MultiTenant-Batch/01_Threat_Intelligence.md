# Threat Intelligence Report
## 2026-09-AWS-Bulletin-IAM-MultiTenant-Batch
**Date:** 2026-09-21 | **Source:** AWS Security Bulletins 2026-112-AWS (2026-09-14) and 2026-113-AWS (2026-09-16) | **Severity:** High | **Category:** Cloud-Security

## Executive Overview
AWS published two security bulletins in this report window that both concern identity and isolation boundaries rather than conventional remote-code-execution vulnerabilities. The first, in TEAM (Temporary Elevated Access Management, an AWS-published open-source reference solution built on IAM Identity Center for granting time-limited elevated access), contains an incorrect-privilege-assignment flaw that could let an authenticated application user obtain unintended temporary elevated access to AWS accounts under TEAM's management. The second, in the aws-network-policy-agent component of Amazon EKS, stems from how pod identifiers are constructed — by concatenating pod name and namespace with a hyphen, a character legal in both — creating identifier collisions across namespaces that can silently bypass Kubernetes NetworkPolicy enforcement, an isolation failure between workloads that should not be able to reach each other.

## Technical Details

### CVE-2026-86830 — TEAM Incorrect Privilege Assignment
- **CVSS Score:** Not published numerically (AWS bulletins in this class typically omit CVSS)
- **Affected Vendor/Product/Version:** TEAM (open-source AWS sample solution for temporary elevated access via IAM Identity Center), versions prior to 1.5.1
- **Vulnerability Type:** Incorrect Privilege Assignment
- **Description:** An authenticated application user could obtain unintended temporary elevated access to AWS accounts managed by TEAM
- **Exploitation Status:** No active exploitation mentioned; disclosed via coordinated disclosure (researcher: Jani Muuriaisniemi, CUJO AI)
- **Remediation:** Upgrade to TEAM v1.5.1 or later; patch any forked/derivative code. No workaround available.

### CVE-2026-86831 — Amazon EKS Network Policy Agent Namespace Collision
- **CVSS Score:** Not specified numerically; AWS labels "Important — requires attention"
- **Affected Vendor/Product/Version:** Amazon VPC CNI Managed Add-on v1.14.0-1.22.3; Network Policy Agent before v1.4.0
- **Vulnerability Type:** Improper Validation of Pod Identifier Uniqueness
- **Description:** Pod identifiers are built by concatenating pod name + namespace with a hyphen (a legal character in both), creating identifier collisions across namespaces that can bypass NetworkPolicy enforcement — a cross-tenant/cross-namespace isolation failure in EKS
- **Exploitation Status:** No active exploitation mentioned
- **Remediation:** Upgrade Network Policy Agent to v1.4.0+ and VPC CNI Managed Add-on to v1.22.4+. Workaround: avoid hyphens in namespace names.

**Threat Actor Attribution:** None for either CVE.
**MITRE ATT&CK Technique IDs:** T1078.004 (Valid Accounts: Cloud Accounts) for TEAM; T1599 (Network Boundary Bridging) for the EKS NetworkPolicy bypass.
**CISA Remediation Due Date:** Not applicable — not KEV-listed.

## Affected Technology Context
Both findings matter specifically because of what they undermine: TEAM exists precisely to enforce least-privilege, time-boxed elevated access rather than standing admin rights, so a privilege-assignment flaw in TEAM itself defeats the control it was built to provide. Similarly, Kubernetes NetworkPolicy is the primary mechanism organizations use to enforce network-level isolation between workloads or tenants within a shared EKS cluster; a bypass here undermines multi-tenant cluster architectures that assume NetworkPolicy enforcement is reliable. Organizations that adopted either tool specifically to strengthen least-privilege or isolation posture should treat this disclosure as a signal to re-verify, not just patch and move on.

## Intelligence Source Links
- AWS Security Bulletin 2026-112-AWS: https://aws.amazon.com/security/security-bulletins/2026-112-aws/
- AWS Security Bulletin 2026-113-AWS: https://aws.amazon.com/security/security-bulletins/2026-113-aws/

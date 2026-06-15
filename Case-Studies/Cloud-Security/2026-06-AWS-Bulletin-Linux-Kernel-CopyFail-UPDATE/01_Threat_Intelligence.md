# Threat Intelligence Summary — UPDATED
## Case: AWS Bulletin 2026-030 — Linux Kernel "Copy.fail / DirtyFrag" LPE Family — Fargate Patch Confirmed
**Date Updated:** 2026-06-15 | **Original Date:** 2026-06-08 | **Source:** AWS Security Bulletin 2026-030 (updated June 11, 2026) | **Analyst:** Blaise Kingko

---

### Update Summary
AWS updated bulletin 2026-030 on June 11, 2026. Key update: Fargate platform version patches have been deployed to all AWS regions by June 15, 2026. Bottlerocket v1.61.0 is now GA. Customer-managed compute (EKS EC2 node groups, self-managed EC2, Bottlerocket hosts) **still requires customer action**.

---

### 1. CVE / Bulletin IDs
- Bulletin: AWS-2026-030
- CVE-2026-46300 ("Fragnesia") — espintcp module — CVSS 7.8
- CVE-2026-31431 — algif_aead module — CVSS 7.8
- CVE-2026-43284 — xfrm_user module — CVSS 7.4
- CVE-2026-43500 — esp modules — CVSS 7.4

### 2. Vulnerability Family
Local privilege escalation (LPE) family affecting Linux kernel cryptography/IPsec/networking subsystems. Exploiting any member of this family allows a local user or container process to escalate from user-space to kernel-level (root) privileges — a critical post-compromise step for persistent foothold and lateral movement.

### 3. Attack Vector
**Local** — attacker must have existing code execution on the host (container escape, compromised workload, insider). Not remotely exploitable directly, but chains with remote vulnerabilities to achieve full root.

### 4. Exploitation Status
No public exploitation of AWS compute environments confirmed. The LPE family remains a theoretical risk on unpatched systems; no PoC published publicly as of June 15, 2026.

### 5. Updated Patch Status (as of June 15, 2026)

| Component | Patch Status |
|---|---|
| AWS Fargate (all regions) | ✅ Patched — confirmed per bulletin update June 11 |
| EKS-optimized AMI | ✅ Patched AMI published — customer rotation required |
| Bottlerocket v1.61.0 | ✅ GA — customer update required |
| Amazon Linux 2023 kernel update | ✅ Available via ALAS2023 |
| Self-managed EC2 (AL2/RHEL/Ubuntu) | ⚠️ Customer must apply vendor kernel patch |

### 6. Framework Mapping (Unchanged)
- **NIST CSF 2.0:** PR.PS-02 (software platforms use secure configs), PR.PS-04 (software maintained commensurate with risk)
- **NIST 800-53 Rev 5:** SI-2 (Flaw Remediation), CM-2 (Baseline Configuration), CM-6 (Configuration Settings), RA-5 (Vulnerability Monitoring)
- **ISO 27001:2022:** A.8.8 (Technical Vulnerability Management), A.8.9 (Configuration Management)
- **CIS Controls v8:** Control 7 (Continuous Vulnerability Management), Safeguard 7.4; Control 4 (Secure Configuration)

### 7. Recommended Immediate Action (Updated)
Rotate all EKS managed node groups to latest EKS-optimized AMI (patched build); update Bottlerocket hosts to v1.61.0; apply ALAS2023 kernel update to self-managed Amazon Linux 2023 EC2 instances. Run CSPM scan (AWS Security Hub, Wiz, or Lacework) to confirm zero non-compliant kernel versions in estate. Target completion: June 22, 2026.

### 8. Risk Rating
**High** (unchanged from original; Fargate patch reduces AWS-managed surface to zero; customer-managed residual risk remains High until customer action completed)

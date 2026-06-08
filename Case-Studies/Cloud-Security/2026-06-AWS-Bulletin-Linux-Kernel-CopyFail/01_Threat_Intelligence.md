# Threat Intelligence Summary
## Case: AWS Bulletin 2026-030 — "Copy.fail" / "DirtyFrag" Linux Kernel Privilege Escalation Family
**Date Identified:** 2026-06-08 | **Source:** AWS Security Bulletin 2026-030-AWS (last updated 2026-06-04) | **Analyst:** Blaise Kingko

---

### 1. Overview
AWS published a consolidated, ongoing bulletin (2026-030-AWS) tracking the "Copy.fail" / "DirtyFrag" family of Linux kernel local privilege-escalation (LPE) vulnerabilities. The family spans multiple CVEs in kernel networking modules:

| CVE | Module | Issue |
|---|---|---|
| CVE-2026-46300 ("Fragnesia") | espintcp | Local privilege escalation |
| CVE-2026-31431 | algif_aead | Privilege escalation |
| CVE-2026-43284 ("DirtyFrag" / Copy.fail 2) | xfrm_user, esp4, esp6 | Privilege escalation via fragment reassembly |
| CVE-2026-43500 | esp/rxrpc | Related LPE variant |

### 2. Affected Vendor / Product
Linux Kernel (versions 4.14, 5.4, 5.10, 5.15, 6.1, 6.12, 6.18 across Amazon Linux); downstream impact to AWS managed services that run customer or AWS-managed kernels.

### 3. CVSS / Severity
Reported in the 7.8–8.8 range across the family (local, low-complexity privilege escalation; no CVE in the set has reached KEV status as of this run, but exploitation proofs-of-concept are circulating publicly per Elastic Security Labs and Wiz research).

### 4. Exploitation Type
Local privilege escalation (container breakout / host-to-root escalation potential in multi-tenant compute). No remote-code-execution vector; requires local code execution as a precondition (e.g., compromised container, malicious workload, insider).

### 5. CISA Remediation Due Date
Not KEV-listed; no BOD 22-01 due date applies. AWS-driven remediation timeline below governs.

### 6. AWS Affected Services & Patch Status (as of 2026-06-04)
| Service | Status |
|---|---|
| Amazon Linux (AL1/AL2/AL2023) | Patched kernels released for 4.14–6.18 lines |
| Bottlerocket | Patched in v1.61.0 |
| ECS | All regions patched |
| EKS | EKS-optimized AMIs updated; customers must roll nodes |
| Fargate | Platform versions patched in all regions by 2026-06-09 |
| EMR | Patch rollout in progress |
| SageMaker | Notebook instances created/restarted after 2026-05-20 auto-patched; Inference Endpoints/Studio/Canvas after 2026-05-26 auto-patched |

### 7. Threat Actor Attribution
None. This is a vulnerability-disclosure / patch-management event, not an active campaign. Treat as a "race to patch before weaponization" scenario — historically, kernel LPE chains of this type are weaponized within 30–60 days of public PoC availability.

### 8. Why This Matters for AWS Multi-Account Environments
Any organization running self-managed EKS node groups, persistent EC2 fleets, or container workloads on Bottlerocket/Amazon Linux must explicitly roll nodes and AMIs — AWS patching the control plane does **not** patch customer-managed compute. This is precisely the "shared responsibility" gap that GRC programs must validate, not assume.

### 9. Sources
- AWS Security Bulletin 2026-030-AWS, "Ongoing updates on Copy.fail and variants" (https://aws.amazon.com/security/security-bulletins/2026-030-aws/)
- Elastic Security Labs, "Copy Fail and DirtyFrag: Linux Page Cache Bugs in the Wild"
- Wiz Research, "Dirty Frag (CVE-2026-43284) Linux Privilege Escalation"

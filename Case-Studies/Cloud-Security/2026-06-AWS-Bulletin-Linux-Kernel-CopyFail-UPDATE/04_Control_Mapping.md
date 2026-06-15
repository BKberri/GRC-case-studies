# Control Mapping Matrix — UPDATED
## Case: AWS Bulletin 2026-030 — Linux Kernel "Copy.fail / DirtyFrag" LPE Family
**Date Updated:** 2026-06-15 | **Analyst:** Blaise Kingko

*(Control mapping framework unchanged from original bundle 2026-06-08. Retained here for completeness per program artifact requirements.)*

---

## Cross-Framework Control Mapping

| Control Domain | NIST CSF 2.0 | NIST 800-53 Rev 5 | ISO 27001:2022 Annex A | CIS Controls v8 |
|---|---|---|---|---|
| **Patch / Kernel Update** | PR.PS-04 | SI-2 | A.8.8 | Control 7.4 |
| **Configuration Baseline** | PR.PS-02 | CM-2, CM-6 | A.8.9 | Control 4.1, 4.2 |
| **Vulnerability Scanning / CSPM** | ID.RA-01, DE.CM-08 | RA-5 | A.8.8 | Control 7.1, 7.5 |
| **Container Security** | PR.PS-02, PR.IR-01 | SI-2, CM-7 | A.8.9, A.8.22 | Control 4, Control 12 |
| **Cloud Shared Responsibility** | GV.SC-06 | CA-7, SA-9 | A.5.23 | Control 4 |

---

## Updated Control Gap Status

| Gap (Original) | Status (Updated) |
|---|---|
| Fargate not yet patched | ✅ CLOSED — AWS patched all regions by June 15 |
| EKS AMI rotation not started | ⚠️ OPEN — patched AMI available; customer action required |
| CSPM scan not run | ⚠️ OPEN — run after node rotation to confirm |
| Bottlerocket v1.61.0 not available | ✅ CLOSED — v1.61.0 GA; customer update required |

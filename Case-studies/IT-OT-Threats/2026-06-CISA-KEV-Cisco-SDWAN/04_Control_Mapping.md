# Control Mapping Matrix
## Case: CVE-2026-20245 — Cisco Catalyst SD-WAN Manager Command Injection (root)
**Date:** 2026-06-15 | **Analyst:** Blaise Kingko

| Control Domain | NIST CSF 2.0 | NIST 800-53 Rev 5 | ISO 27001:2022 | CIS Controls v8 | Recommendation |
|---|---|---|---|---|---|
| **Patch Management** | PR.PS-04 | SI-2 | A.8.8 | Control 7.4 | Apply Cisco patch immediately |
| **Privileged Access Management** | PR.AA-05 | AC-6 (Least Privilege), AC-2 (Account Management) | A.5.15, A.5.18 | Control 5.4, 6.8 | Enforce MFA + PAW access for all vManage admin accounts |
| **Network Segmentation** | PR.IR-01 | SC-7 | A.8.22 | Control 12.2 | Restrict vManage to dedicated OOB management network |
| **Configuration Change Monitoring** | DE.CM-03 | CM-3, AU-12 | A.8.32, A.8.15 | Control 8.5 | Alert SIEM on any SD-WAN policy change; require change ticket correlation |
| **Admin Account Audit** | ID.AM-05 | AC-2 | A.5.16 | Control 5.1 | Audit all vManage accounts; remove stale/unnecessary accounts |
| **File Integrity / Audit Logging** | DE.CM-03, DE.AE-03 | AU-9, SI-7 | A.8.15 | Control 8.2 | Enable and protect vManage audit logs; forward to SIEM |

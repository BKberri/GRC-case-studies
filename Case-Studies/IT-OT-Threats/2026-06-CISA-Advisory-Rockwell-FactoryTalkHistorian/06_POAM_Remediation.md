# POA&M / Remediation Plan — Rockwell FactoryTalk Historian SE Multiple Vulnerabilities

| # | Action | Owner | Target Date | Status |
|---|---|---|---|---|
| 1 | Inventory all FactoryTalk Historian SE deployments and current version | OT/ICS Engineering | 2026-06-29 | Open |
| 2 | Apply vendor patch/mitigation for CVE-2025-13036 (insecure deserialization, critical) | OT/ICS Engineering | 2026-07-06 | Open |
| 3 | Rotate hardcoded/default credentials per Rockwell guidance (CVE-2025-44019) | OT/ICS Engineering | 2026-07-06 | Open |
| 4 | Remediate improper access control configuration (CVE-2025-36539) | OT/ICS Engineering | 2026-07-06 | Open |
| 5 | Verify/strengthen IT/OT network segmentation around historian servers | Security Architecture | 2026-07-13 | Open |
| 6 | Document closure evidence (patch versions, credential rotation confirmation, segmentation verification) | GRC | 2026-07-15 | Open |

## Specific Remediation
Apply Rockwell Automation's published vendor patches/mitigations for all three CVEs per ICSA-26-167-02; rotate hardcoded/default credentials; confirm network segmentation between historian servers and the broader OT/ICS environment limits lateral movement exposure pending patch completion.

## Note on Advisory Status
This is a CISA ICS advisory (not yet KEV-listed). No confirmed active exploitation as of this report; remediation timeline follows standard OT patch-cycle priority given the critical-severity RCE component (CVE-2025-13036), rather than emergency out-of-cycle deployment.

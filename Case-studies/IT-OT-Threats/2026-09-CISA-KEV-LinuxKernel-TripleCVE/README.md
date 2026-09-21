# 2026-09-CISA-KEV-LinuxKernel-TripleCVE
**Date:** 2026-09-21 | **Source:** CISA KEV | **Category:** IT-OT-Threats | **Risk Rating:** Critical

## Summary
CISA added three Linux kernel vulnerabilities to the Known Exploited Vulnerabilities catalog on 2026-09-18, all confirmed under active exploitation per Red Hat as of 2026-09-19: a race condition in the AF_ALG crypto socket subsystem (CVE-2025-39964), an out-of-bounds write in the netfilter ebtables SNAT bridge target (CVE-2026-53266), and an improper condition-handling flaw in the kernel TLS receive path (CVE-2025-39682). All three are local-attack-vector kernel flaws requiring existing low-privilege access, consistent with a post-compromise privilege-escalation or persistence pattern rather than an initial-access vector. CISA flagged the affected products as potentially end-of-life/end-of-service, and specific technical exploitation details have not been publicly disclosed.

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
- **CVE/Advisory ID:** CVE-2025-39964; CVE-2026-53266; CVE-2025-39682 (all added to KEV 2026-09-18)
- **CVSS Score:** CVE-2025-39964: 7.8 (CNA) / 5.5 (NVD re-score, disputed C:N/I:N vs C:H/I:H); CVE-2026-53266: 8.8; CVE-2025-39682: 9.8 (CNA) / 7.1 (NVD, "Undergoing Analysis")
- **Affected Technology:** Linux Kernel — AF_ALG crypto sockets, netfilter ebtables (bridge subsystem), and kernel TLS receive path. Specific affected version ranges not published by CISA beyond upstream kernel.org commit references; CISA notes possible EoL/EoS product status.
- **Frameworks Applied:** NIST CSF 2.0, NIST 800-53 Rev 5, ISO 27001:2022, CIS Controls v8
- **Exploitation Status:** Confirmed actively exploited (Red Hat, as of 2026-09-19); no public technical exploitation writeup found as of this sweep
- **CISA Remediation Due Date:** 2026-09-21 (today)

## Related Cases
This continues a recurring pattern this program has tracked (see prior AWS-Bulletin-Linux-Kernel-CopyFail case and ABB Ability Edgenius CVE-2026-31431, also a Linux kernel "Copy Fail" privilege-escalation finding) — Linux kernel local-privilege-escalation and memory-safety flaws are a persistent, high-frequency KEV category given the kernel's presence across nearly every server, container host, and embedded/OT Linux deployment in the enterprise estate.

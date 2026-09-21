# Threat Intelligence Report
## 2026-09-CISA-KEV-LinuxKernel-TripleCVE
**Date:** 2026-09-21 | **Source:** CISA KEV (added 2026-09-18) | **Severity:** Critical | **Category:** IT-OT-Threats

## Executive Overview
CISA added three distinct Linux kernel vulnerabilities to its KEV catalog on the same date (2026-09-18), each independently confirmed under active exploitation by Red Hat as of 2026-09-19. All three are local-attack-vector flaws — meaning exploitation requires the attacker already hold some level of access to the target system — consistent with their most likely use as privilege-escalation or persistence mechanisms following an initial compromise via another vector, rather than as an initial point of entry themselves. Given the Linux kernel's presence across virtually the entire modern server, container-host, and embedded-Linux estate, these findings warrant broad review even though each individual CVE's public technical detail remains limited.

## Technical Details

### CVE-2025-39964 — AF_ALG Crypto Socket Race Condition
- **CVSS Score:** CNA: 7.8 (CVSS:3.1/AV:L/AC:L/PR:L/UI:N/S:U/C:H/I:H/A:H); NVD re-score: 5.5 (CVSS:3.1/AV:L/AC:L/PR:L/UI:N/S:U/C:N/I:N/A:H) — note the scoring dispute between CNA and NVD on confidentiality/integrity impact; risk-register purposes use the higher CNA score.
- **Vulnerability Type:** Race Condition (CWE-362) — concurrent writes to the same AF_ALG socket interleave unpredictably, corrupting internal socket state
- **Exploitation Status:** Actively exploited (Red Hat, confirmed 2026-09-19)

### CVE-2026-53266 — Netfilter ebtables SNAT Out-of-Bounds Write
- **CVSS Score:** 8.8 (CVSS:3.1/AV:L/AC:L/PR:L/UI:N/S:C/C:H/I:H/A:H)
- **Vulnerability Type:** Out-of-Bounds Write (CWE-787) — an Ethernet source-address rewrite in the ebtables SNAT bridge target writes into a splice-imported, nonlinear socket-buffer memory page without adequate write-safety checks
- **Exploitation Status:** Actively exploited (Red Hat, confirmed 2026-09-19)

### CVE-2025-39682 — Kernel TLS Receive Path Condition-Handling Flaw
- **CVSS Score:** CNA: 9.8 (CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H); NVD: 7.1 (CVSS:3.1/AV:L/AC:L/PR:L/UI:N/S:U/C:H/I:N/A:H), status "Undergoing Analysis" — significant scoring divergence between the network-vector CNA score and the local-vector NVD assessment; treat as unresolved pending NVD's finalized analysis.
- **Vulnerability Type:** Improper Check for Unusual or Exceptional Conditions (CWE-754) — a zero-length record already queued on the rx_list bypasses expected record-type handling in recvmsg(), desynchronizing subsequent TLS record processing
- **Exploitation Status:** Actively exploited (Red Hat, confirmed 2026-09-19)

**Threat Actor Attribution:** None publicly disclosed for any of the three CVEs.
**MITRE ATT&CK Technique IDs:** T1068 (Exploitation for Privilege Escalation) applies to all three given the local-vector, low-privilege-required pattern.
**CISA Remediation Due Date:** 2026-09-21

## Affected Technology Context
Because these are upstream Linux kernel flaws rather than distribution-specific patches, the remediation path depends on each organization's Linux distribution and kernel update cadence (RHEL, Ubuntu, Debian, Amazon Linux, etc.) rather than a single vendor patch. CISA's note that affected products "could be end-of-life (EoL) and/or end-of-service (EoS)" is a material flag: organizations running older, unsupported kernel versions may not receive a backported fix at all and should treat kernel version currency as a standing risk-register item independent of this specific KEV entry.

## Intelligence Source Links
- CISA KEV Catalog: https://www.cisa.gov/known-exploited-vulnerabilities-catalog
- NVD: https://nvd.nist.gov/vuln/detail/CVE-2025-39964 ; https://nvd.nist.gov/vuln/detail/CVE-2026-53266 ; https://nvd.nist.gov/vuln/detail/CVE-2025-39682
- The Hacker News: https://thehackernews.com/2026/09/cisa-flags-three-linux-kernel.html

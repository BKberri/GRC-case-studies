# Threat Intelligence Report — Ubiquiti UniFi OS Triple-CVE Takeover Chain

## CVE Details

| Field | Value |
|---|---|
| **CVE IDs** | CVE-2026-34908 (Improper Access Control), CVE-2026-34909 (Path Traversal), CVE-2026-34910 (Improper Input Validation / Command Injection) |
| **Vulnerability Name** | Ubiquiti UniFi OS — Unauthenticated Device Takeover Chain |
| **Affected Vendor/Product** | All UniFi OS-powered devices: Cloud Gateways, Network Controllers, Protect NVRs, Access Hubs, Talk appliances |
| **CVSS Score** | 10.0 (Critical) for each of the three CVEs |
| **Date Added to KEV** | 2026-06-23 |
| **Exploitation Type** | Unauthenticated access control bypass → path traversal → command injection, chained to full root-level device takeover |
| **CISA Remediation Due Date** | 2026-06-26 (3-day mandate, BOD 26-04) |

## Exploitation Summary
Three chained vulnerabilities allow an unauthenticated attacker to fully take over any UniFi OS-powered device. CVE-2026-34908 (improper access control) provides the initial unauthenticated entry point. CVE-2026-34909 (path traversal) is then used to access and manipulate files on the underlying operating system, including account data. CVE-2026-34910 (improper input validation) enables network command injection, completing the chain to full device control. CISA confirmed active exploitation, including a Mirai/Gafgyt-class botnet campaign targeting vulnerable devices. A vendor fix (UniFi OS Server v5.0.8) was available as of May 21, 2026 — over a month before KEV listing — meaning the exploitation window reflects a patch-deployment gap rather than a true zero-day.

## Why This Matters
UniFi OS underpins network infrastructure (Cloud Gateways, Network Controllers) as well as physical security systems (Protect NVRs) and access control (Access Hubs) across a very large number of small/mid-size business and enterprise branch deployments. A pre-authentication, full-takeover chain on this device class converts every internet-reachable UniFi controller into a potential botnet node and a pivot point into the networks, video surveillance, and physical access systems it manages.

## Framework Mapping
- **NIST CSF 2.0:** PR.AA-05 (Access permissions managed), PR.PS-04 (Software maintained/updated), DE.CM-01 (Networks monitored)
- **NIST 800-53 Rev 5:** AC-3 (Access Enforcement), SI-2 (Flaw Remediation), SI-10 (Information Input Validation), SC-7 (Boundary Protection)
- **ISO/IEC 27001:2022 Annex A:** A.8.8 (Management of Technical Vulnerabilities), A.8.9 (Configuration Management), A.8.16 (Monitoring Activities)
- **CIS Controls v8:** Control 7 (Continuous Vulnerability Management), Control 4 (Secure Configuration of Enterprise Assets), Control 13 (Network Monitoring and Defense)

## Recommended Immediate Action
Upgrade all UniFi OS devices to UniFi OS Server v5.0.8 or later immediately; for any device that cannot be patched within 72 hours, remove it from direct internet exposure and restrict management access to a VPN or dedicated management network.

## Risk Rating
**Critical** — Maximum CVSS (10.0) across three chained CVEs, confirmed active exploitation via botnet campaign, pre-authentication full device takeover, broad install base across network, video, and access-control infrastructure.

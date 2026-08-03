# Threat Intelligence Report
## 2026-08-CISA-KEV-Arista-VeloCloud-CommandInjection
**Date:** 2026-08-03 | **Source:** CISA KEV (added 2026-07-27) | **Severity:** Critical | **Category:** IT-OT-Threats

## Executive Overview
Arista Networks' VeloCloud Orchestrator (VCO) — the on-premises management plane for VeloCloud SD-WAN deployments — contains an unauthenticated OS command injection vulnerability (CVE-2026-16812) that Arista and CISA confirm is being actively exploited in the wild. An attacker with nothing more than network access to the VCO web interface can execute arbitrary commands on the orchestrator host, with no credentials, no user interaction, and no complex preconditions required. Because VCO is the single control point for an organization's entire SD-WAN fabric, compromise of the orchestrator is functionally equivalent to compromise of every branch, campus, and cloud edge device it manages.

## Technical Details
- **CVE ID:** CVE-2026-16812
- **CVSS 3.1 Score:** 10.0 (Critical) — Vector: `AV:N/AC:L/PR:N/UI:N/S:C/C:H/I:H/A:H`
- **Affected Vendor/Product/Version:** Arista Networks VeloCloud Orchestrator (VCO), on-premises deployments. Confirmed vulnerable prior to 5.2.3.14, 6.1.3.4, and 6.4.2.4. VCO 7.0.0.1 and later is not affected.
- **Vulnerability Type:** OS Command Injection (CWE-78) — improper neutralization of special elements used in an OS command
- **Exploitation Status:** Actively exploited in the wild (confirmed by Arista; added to CISA KEV 2026-07-27)
- **Threat Actor Attribution:** Not publicly attributed at time of this report; exploitation observed against internet-exposed VCO instances
- **MITRE ATT&CK Technique IDs:** T1190 (Exploit Public-Facing Application), T1059 (Command and Scripting Interpreter), T1210 (Exploitation of Remote Services — lateral movement to managed edges)
- **IOCs:** Not yet publicly published by Arista at time of this report; monitor Arista Security Advisory 0144 for updates
- **CISA Remediation Due Date:** 2026-07-30 (three-day remediation window from KEV addition — reflects unauthenticated, no-precondition exploitability)

## Affected Technology Context
VeloCloud Orchestrator is the centralized control-plane console for VMware/Arista SD-WAN fabrics — it pushes configuration, routing policy, and firmware to every VeloCloud Edge device in an enterprise's WAN. Because VCO sits above the data plane, an attacker who gains code execution on the orchestrator inherits the "keys to the kingdom": the ability to push malicious configuration or firmware to every branch office, retail location, or cloud gateway the fabric touches, redirect or intercept WAN traffic, and pivot into segmented environments that individual edge devices would otherwise isolate. Many VCO deployments are internet-facing by design (edges phone home to the orchestrator across the public internet), which materially increases the exposed attack surface relative to internally-hosted management planes. This case is consistent with a broader 2026 pattern of threat actors targeting SD-WAN and network orchestration platforms (Cisco SD-WAN, Ivanti, Fortinet) as high-leverage single points of compromise for enterprise WANs.

## Intelligence Source Links
- CISA KEV Alert: https://www.cisa.gov/news-events/alerts/2026/07/27/cisa-adds-two-known-exploited-vulnerabilities-catalog
- CISA KEV Catalog: https://www.cisa.gov/known-exploited-vulnerabilities-catalog
- Arista Security Advisory 0144: https://www.arista.com/en/support/advisories-notices/security-advisory/24364-security-advisory-0144
- The Hacker News coverage: https://thehackernews.com/2026/07/attackers-exploit-arista-velocloud.html
- The Register coverage: https://www.theregister.com/security/2026/07/28/arista-patches-actively-exploited-velocloud-bug-as-cisa-puts-admins-on-the-clock/

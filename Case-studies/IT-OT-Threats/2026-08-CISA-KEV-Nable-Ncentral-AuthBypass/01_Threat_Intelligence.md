# Threat Intelligence Report
## 2026-08-CISA-KEV-Nable-Ncentral-AuthBypass
**Date:** 2026-08-10 | **Source:** CISA KEV (added 2026-08-03 and 2026-08-04) | **Severity:** Critical | **Category:** IT-OT-Threats

## Executive Overview
N-able N-central is an RMM platform widely deployed by managed service providers (MSPs) and enterprise IT teams to centrally administer, patch, and remotely control large fleets of endpoints. N-able published an initial security advisory for an authentication-bypass vulnerability (CVE-2026-18556) on 2026-08-01 after observing active exploitation, and shipped a fix in N-central 2026.2. That fix proved incomplete: attackers identified an alternate authentication-bypass path exploiting the same underlying logic flaw, tracked separately as CVE-2026-18577, which N-able addressed with N-central 2026.3 Hotfix 1 (build 2026.3.1.7) released 2026-08-02. Both CVEs allow an unauthenticated attacker to gain administrative access to the N-central server itself.

## Technical Details
- **CVE IDs:** CVE-2026-18556 (CVSS 3.1: 7.4) and CVE-2026-18577 (CVSS 3.1: 8.1) — both classified as Authentication Bypass Using an Alternate Path or Channel (CWE-288)
- **Affected Vendor/Product/Version:** N-able N-central — CVE-2026-18556 covers releases through 2026.1 (fixed in 2026.2); CVE-2026-18577 covers builds before 2026.3.1.7 (fixed in N-central 2026.3 Hotfix 1)
- **Vulnerability Type:** Authentication Bypass Using an Alternate Path or Channel
- **Exploitation Status:** Actively exploited in the wild since 2026-08-01, prior to and continuing after N-able's initial patch
- **Threat Actor Attribution:** Not publicly attributed at time of this report
- **MITRE ATT&CK Technique IDs:** T1190 (Exploit Public-Facing Application), T1078 (Valid Accounts), T1219 (Remote Access Software — abuse of built-in "Take Control" functionality), T1572 (Protocol Tunneling — Cloudflare Tunnel/cloudflared for persistence)
- **IOCs:** Presence of unauthorized Cloudflare Tunnel (cloudflared) binaries or outbound connections on N-central servers or managed endpoints; unexpected "Take Control" session initiation events not tied to a known administrator
- **CISA Remediation Due Date:** Confirm against live catalog entries for both CVEs (added 2026-08-03 and 2026-08-04 respectively)

## Affected Technology Context
N-central occupies a uniquely high-leverage position in any environment where it is deployed: it is the trusted management plane with pre-established remote-control access to every endpoint it administers. In MSP deployments, a single compromised N-central instance can be a pivot point into every downstream client organization the MSP serves — a supply-chain-style blast radius similar in kind (though narrower in reported scale so far) to the 2021 Kaseya VSA incident that this program's operator should recognize as the closest historical analog. The observed attacker behavior — using the platform's own "Take Control" feature rather than deploying custom malware, then establishing Cloudflare Tunnel persistence — is a "living off the land" pattern that is materially harder to detect than conventional malware deployment because it uses the RMM platform exactly as designed, just without authorization.

## Intelligence Source Links
- CISA KEV Alert (Aug 3): https://www.cisa.gov/news-events/alerts/2026/08/03/cisa-adds-one-known-exploited-vulnerability-catalog
- CISA KEV Alert (Aug 4 batch): https://www.cisa.gov/news-events/alerts/2026/08/04/cisa-adds-three-known-exploited-vulnerabilities-catalog
- The Hacker News coverage: https://thehackernews.com/2026/08/n-able-says-attackers-take-over-n.html
- N-able security update blog: https://www.n-able.com/blog/n-central-security-update-august-6-2026
- Horizon3.ai analysis: https://horizon3.ai/attack-research/vulnerabilities/cve-2026-18556-cve-2026-18577/
- Rapid7 analysis: https://www.rapid7.com/blog/post/etr-cve-2026-18577-n-able-n-central-authentication-bypass-exploited-in-the-wild/

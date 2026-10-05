# Threat Intelligence Report, CVE-2026-104286
## Fortinet FortiMail Unauthenticated Path Traversal / Arbitrary File Write

**Case ID:** 2026-10-CISA-KEV-FortiMail-PathTraversal
**Date Identified:** 2026-10-01
**Analyst:** Blaise Kingko
**Classification:** Critical, Actively Exploited, CISA KEV

---

## 1. Vulnerability Summary

| Field | Detail |
|---|---|
| CVE ID | CVE-2026-104286 |
| Vendor / Product | Fortinet FortiMail (secure email gateway) |
| Affected Versions | 8.0.0–8.0.1, 7.6.0–7.6.6, 7.4.0–7.4.8, 7.2.0–7.2.9 (7.2 requires migration off-branch) |
| CVSS Score | 9.8 (Critical) |
| CWE | Path Traversal (CWE-22) + Improper Neutralization of NULL Byte (CWE-158) |
| CISA KEV Added | 2026-10-01 |
| CISA Remediation Due Date | 2026-10-04 (federal civilian deadline has elapsed as of this report) |
| Exploitation Status | Actively exploited in the wild; multiple researchers report attackers writing files to achieve persistent, no-password backdoor access |
| Patch Availability | **No vendor patch available at time of this report.** Fixed builds (8.0.2, 7.6.7, 7.4.9) are listed by Fortinet as "upcoming," not yet downloadable |

## 2. Technical Description

An unauthenticated attacker can send specially crafted HTTP/HTTPS requests to a FortiMail management or web interface that combine directory traversal sequences with NULL-byte injection to defeat the gateway's path-sanitization logic. The flaw allows arbitrary files to be written to the underlying filesystem outside the intended web root. Public reporting (SecurityWeek, SOCRadar, Suped, Strix) describes attackers using the primitive to drop authentication-bypassing artifacts, effectively creating a persistent backdoor that requires no credentials. Because FortiMail sits at the perimeter as an internet-facing mail security gateway, this is a pre-authentication, remotely exploitable flaw with no user interaction required.

## 3. Exploitation Timeline

- **2026-10-01**, Fortinet publishes advisory FG-IR-26-175; CISA adds CVE-2026-104286 to the KEV catalog the same day, citing confirmed active exploitation.
- **2026-10-02**, Independent researchers (SOCRadar, Techtimes) confirm in-the-wild backdooring of unpatched FortiMail gateways.
- **2026-10-04**, CISA federal remediation deadline passes; no vendor-supplied patch has shipped (interim workaround only).

## 4. Framework Mapping

- **NIST CSF 2.0:** PR.PS-06 (Application Security), DE.CM-01 (Network Monitoring), RS.MI-02 (Incident Mitigation)
- **NIST SP 800-53 Rev 5:** SI-10 (Information Input Validation), SI-2 (Flaw Remediation), SC-7 (Boundary Protection), IR-4 (Incident Handling)
- **ISO/IEC 27001:2022:** A.8.8 (Management of Technical Vulnerabilities), A.8.26 (Application Security Requirements)
- **CIS Controls v8:** Control 16 (Application Software Security), Control 12 (Network Infrastructure Management)

## 5. Recommended Immediate Action

Because no vendor patch currently exists, treat this as an emergency containment event rather than a standard patch cycle: disable Identity-Based Encryption (IBE) support (the vulnerable code path) via CLI, and remove the FortiMail management interface from direct internet exposure, restricting access to a trusted out-of-band management network. Independently verify no backdoor files have already been written before relying on the workaround alone.

**Risk Rating: Critical**

---
*Sources: Fortinet PSIRT advisory FG-IR-26-175; CISA KEV catalog (dateAdded 2026-10-01, dueDate 2026-10-04); SecurityWeek, "Exploited Fortinet FortiMail Zero-Day Calls for Urgent Action"; SOCRadar, "FortiMail Zero-Day Under Active Exploitation."*

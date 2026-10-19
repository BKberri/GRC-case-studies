# Threat Intelligence Report, CVE-2026-102764
## BeyondTrust Remote Support Authentication Bypass Exploited by Suspected Nation-State Actor

**Case ID:** 2026-10-CISA-KEV-BeyondTrust-RemoteSupport-AuthBypass
**Date Identified:** 2026-10-16
**Analyst:** Blaise Kingko
**Classification:** Critical, Actively Exploited Since August, CISA KEV, Nation-State Attribution

---

## 1. Vulnerability Summary

| Field | Detail |
|---|---|
| CVE ID | CVE-2026-102764 |
| Vendor / Product | BeyondTrust Remote Support (RS); Privileged Remote Access (PRA) patched as a precaution (no confirmed exploit path found in testing) |
| Affected Versions | Remote Support 26.2.3 and earlier |
| CVSS Score | Not published with a numeric score in available reporting at time of this entry; vendor and government advisories (BeyondTrust BT26-05, CCCS AL26-025) characterize it as Critical |
| CWE | Authentication Bypass |
| CISA KEV Added | 2026-10-16 |
| Exploitation Status | Actively exploited as a zero-day since late August 2026, roughly seven weeks before CISA's KEV addition |
| Patch Availability | Remote Support and PRA SaaS customers patched 2026-10-08; self-hosted installations require manual patching unless automatic updates are enabled |

## 2. Technical Description

The flaw allows an unprivileged remote attacker to perform unauthorized file operations on an unpatched BeyondTrust Remote Support appliance, bypassing authentication entirely. Mandiant (Google Threat Intelligence Group) attributes exploitation to a suspected China-nexus espionage actor tracked as Armory Castle (formerly UNC5221) by Mandiant and as Warp Panda by CrowdStrike. Observed post-exploitation activity included escalating to root by enabling SUID permissions, deploying the Sawfly web shell and the Bareclaw tunneler malware, wiping logs to frustrate forensic review, and moving laterally using compromised administrator credentials. Shadowserver telemetry identifies over 1,400 internet-exposed Remote Support instances, a population size that does not indicate how many remain unpatched.

## 3. Exploitation Timeline

- **Late August 2026**, exploitation begins as a zero-day against BeyondTrust Remote Support appliances, later attributed to the suspected China-nexus actor Armory Castle/Warp Panda.
- **2026-10-08**, BeyondTrust patches Remote Support and Privileged Remote Access SaaS customers.
- **2026-10-16**, CISA adds CVE-2026-102764 to the KEV catalog, approximately seven weeks after exploitation began.
- **As of this report (2026-10-19)**, self-hosted installations not covered by automatic updates remain exposed until manually patched, and any appliance reachable from the internet on a vulnerable version during the roughly seven-week exploitation window should be treated as potentially compromised.

## 4. Framework Mapping

- **NIST CSF 2.0:** PR.AA-02 (Authentication), DE.CM-01 (Network Monitoring), RS.MI-02 (Incident Mitigation), RC.CO-01 (Recovery Communications)
- **NIST SP 800-53 Rev 5:** IA-2 (Identification and Authentication), AC-6 (Least Privilege), SI-2 (Flaw Remediation), IR-4 (Incident Handling), AU-6 (Audit Record Review, given confirmed log-wiping)
- **ISO/IEC 27001:2022:** A.8.5 (Secure Authentication), A.8.8 (Management of Technical Vulnerabilities), A.5.24 (Incident Management Planning)
- **CIS Controls v8:** Control 5 (Account Management), Control 6 (Access Control Management), Control 8 (Audit Log Management)

## 5. Recommended Immediate Action

Patch every self-hosted Remote Support instance immediately if not already covered by automatic updates, and, given confirmed nation-state exploitation dating back roughly seven weeks before public disclosure, treat every internet-reachable appliance that ran a vulnerable version during that window as potentially compromised rather than assuming the patch alone resolves exposure; this includes reviewing for SUID-permission changes, the Sawfly web shell, Bareclaw tunneler artifacts, wiped logs, and use of compromised administrator credentials for lateral movement, per Mandiant's published indicators.

**Risk Rating: Critical**

---
*Sources: BeyondTrust advisory BT26-05; Canadian Centre for Cyber Security Alert AL26-025; CISA KEV catalog (dateAdded 2026-10-16); BleepingComputer, "BeyondTrust patches zero-day exploited in attacks since August"; Mandiant/Google Threat Intelligence Group reporting on Armory Castle (UNC5221) / Warp Panda.*

# Threat Intelligence Report — SharePoint Server Deserialization RCE with Machine Key Theft

## CVE Details

| Field | Value |
|---|---|
| **CVE ID** | CVE-2026-50522 |
| **Vulnerability Name** | Microsoft SharePoint Server Deserialization of Untrusted Data |
| **Affected Vendor/Product** | Microsoft SharePoint Server — Subscription Edition, 2019, 2016 (on-premises) |
| **CVSS Score** | 9.8 (Critical) — AV:N/AC:L, network-exploitable, low attack complexity per Microsoft |
| **Vulnerable Component** | Deserialization handling requiring Site Owner-level authentication to trigger arbitrary code execution |
| **Date Added to KEV** | 2026-07-22 |
| **CISA Remediation Due Date** | 2026-07-25 (3-day emergency mandate under BOD 26-04) |
| **Exploitation Type** | Deserialization RCE, followed by IIS machine key theft enabling persistent forged-token access |
| **Discovered By** | DEVCORE researcher "splitline," credited by Microsoft |

## Executive Overview
CVE-2026-50522 is a deserialization flaw in on-premises SharePoint Server: an attacker authenticated with at least Site Owner privileges can write and execute arbitrary code remotely. Microsoft rated it "Exploitation More Likely" in its own advisory. A public proof-of-concept exploit was released 2026-07-20, and active exploitation followed within hours. The defining characteristic of this incident is not the RCE itself but what attackers do immediately after: pulling the server's IIS machine keys in a single request, then using those keys to forge authentication tokens that remain valid — and exploitable — even after the server is patched.

## Technical Details
- **CVE ID:** CVE-2026-50522
- **CVSS Score and vector:** 9.8 Critical. Per Microsoft's advisory: "The attack vector is Network (AV:N) because this vulnerability is remotely exploitable... The attack complexity is Low (AC:L) because an attacker does not require significant prior knowledge of the system and can achieve repeatable success with the payload."
- **Affected vendor/product/version:** Microsoft SharePoint Server, all supported on-premises versions — Subscription Edition, 2019, and 2016
- **Vulnerability type:** Deserialization of untrusted data — an attacker authenticated as at least Site Owner can write arbitrary code that is deserialized and executed on the server
- **Exploitation status:** Actively exploited. Public PoC released 2026-07-20; watchTowr confirmed active exploitation within hours, specifically observing attackers pulling SharePoint machine keys via a single request
- **Threat actor attribution:** Not formally attributed; Defused Cyber independently observed exploitation delivering a .NET deserialization payload to a SharePoint sign-in endpoint with no authentication material in captured requests, consistent with the unauthenticated-profile post-exploitation stage
- **MITRE ATT&CK:** T1190 (Exploit Public-Facing Application), T1552 (Unsecured Credentials — machine key theft), T1606 (Forge Web Credentials — forged authentication tokens using stolen machine keys), T1078 (Valid Accounts, via forged tokens)
- **IOCs:** Machine-key-harvesting requests targeting the SharePoint sign-in endpoint; payloads carrying no authentication material (consistent with the vulnerability's exploitation profile); network exfiltration of IIS machine key material
- **CISA remediation due date:** 2026-07-25 (KEV added 2026-07-22; 3-business-day BOD 26-04 emergency mandate)

## Broader SharePoint Exploitation Wave — July 2026
CVE-2026-50522 is the third SharePoint Server vulnerability confirmed under active exploitation in a wave of attacks this month, following CVE-2026-56164 (CVSS 5.3) and CVE-2026-58644 (CVSS 9.8), both weaponized as zero-days ahead of their fix in the record-setting July 2026 Patch Tuesday release. CISA has separately warned that threat actors are exploiting CVE-2026-32201, CVE-2026-45659, CVE-2026-56164, and CVE-2026-58644 together to gain unauthorized access to on-premises SharePoint instances, with post-exploitation activity consistently involving IIS machine key theft and deserialization techniques to establish persistence. Organizations should treat any on-premises SharePoint Server not yet fully patched and key-rotated against this entire cluster of vulnerabilities as a standing, cumulative exposure — not a single discrete finding.

## Affected Technology Context
SharePoint Server is core collaboration and document-management infrastructure for many enterprises, frequently holding sensitive internal documents, and in hybrid deployments, acting as a bridge between on-premises identity and cloud services. The machine-key-theft technique observed here is what makes this finding materially more dangerous than a typical RCE: IIS machine keys are used to protect ASP.NET view state and forms authentication tickets, so an attacker holding stolen keys can forge valid, trusted authentication tokens indefinitely — surviving a patch that closes only the original code-execution vector. Any organization treating "patch applied" as equivalent to "incident closed" for this CVE is working from a false sense of remediation.

## Intelligence Source Links
- Microsoft Security Response Center: https://msrc.microsoft.com/update-guide/vulnerability/CVE-2026-50522
- The Hacker News: https://thehackernews.com/2026/07/critical-sharepoint-rce-cve-2026-50522.html
- Help Net Security: https://www.helpnetsecurity.com/2026/07/22/sharepoint-cve-2026-50522-exploited/
- Security Affairs: https://securityaffairs.com/195760/security/public-poc-triggers-active-exploitation-of-critical-sharepoint-rce-vulnerability-cve-2026-50522.html
- CISA KEV addition: https://www.cisa.gov/news-events/alerts/2026/07/22/cisa-adds-two-known-exploited-vulnerabilities-catalog

## Risk Rating
**Critical** — CVSS 9.8, confirmed active exploitation within hours of public PoC release, machine-key theft enabling persistence that survives patching, part of a broader ongoing SharePoint exploitation wave, and a 3-day federal remediation mandate.

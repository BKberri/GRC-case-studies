# Microsoft SharePoint Code Injection (CVE-2026-65660) — Threat Intelligence Report

## Case Study Metadata

| Field | Details |
|---|---|
| **Case Study ID** | CS-ITOT-2026-09-003 |
| **Date Published** | 2026-09-28 |
| **Incident/Disclosure Date** | 2026-09-25 (CISA KEV addition date) |
| **Author** | Blaise Kingko |
| **Threat Category** | IT/OT — Application / Collaboration Platform (on-premises SharePoint Server) |
| **CVE / Advisory ID** | CVE-2026-65660 |
| **CVSS Score** | 8.8 HIGH (CVSS 3.1) — CVSS:3.1/AV:N/AC:L/PR:L/UI:N/S:U/C:H/I:H/A:H |
| **Affected Vendor** | Microsoft |
| **Affected Product** | SharePoint Enterprise Server 2016, SharePoint Server 2019, SharePoint Server Subscription Edition (on-premises deployments only) |
| **Intelligence Source** | CISA KEV Catalog / NVD / Microsoft Security Response Center (MSRC) / Previdian (third-party research) |
| **Exploitation Status** | Actively exploited (KEV-confirmed); third-party researchers report a two-stage exploitation pattern in observed attempts |

---

## 1. Incident Summary

### 1.1 What Happened

On September 25, 2026, CISA added CVE-2026-65660, a code injection vulnerability in Microsoft Office SharePoint, to the Known Exploited Vulnerabilities (KEV) Catalog, confirming active exploitation in the wild. The flaw is an instance of CWE-94 (Improper Control of Generation of Code / Code Injection): per Microsoft and NVD, it allows "an authorized attacker to execute code over a network." The vulnerability affects on-premises SharePoint Server deployments — SharePoint Enterprise Server 2016, SharePoint Server 2019, and SharePoint Server Subscription Edition — and does not affect SharePoint Online / Microsoft 365. CISA set a federal civilian remediation due date of September 28, 2026 — three days after KEV addition, and the same date as this report's publication. As of publication, that deadline has just elapsed for any organization that has not yet patched, and this finding should be treated as an overdue emergency remediation item rather than a routine patch-cycle entry.

### 1.2 Why It Matters

SharePoint Server hosts an organization's internal document repositories, collaboration sites, and — in many enterprise deployments — workflow and business-process automation that other applications depend on, making it a high-value target whose compromise exposes broad swaths of internal data and can serve as a pivot point into connected systems. This is also not this program's first SharePoint finding of 2026: it follows the July 2026 case study on SharePoint machine-key theft (2026-07-CISA-KEV-SharePoint-MachineKeyTheft), and this program's own historical tracking notes that SharePoint had already seen a third of four related CVEs in an earlier 2026 disclosure batch actively exploited. Taken together, on-premises SharePoint Server has now been a recurring, high-value KEV target multiple times in a single calendar year — a pattern significant enough on its own to warrant a standing risk posture rather than a case-by-case response (see §2.3 and the strategic recommendation in 06_POAM_Remediation.md).

### 1.3 Affected Environments

- **IT Systems:** On-premises Microsoft SharePoint Server farms — SharePoint Enterprise Server 2016 (before build 16.0.5565.1001), SharePoint Server 2019 (before build 16.0.10417.20198), and SharePoint Server Subscription Edition (before build 16.0.19725.20522). This includes associated web front-end servers, application servers, and the SQL Server back end hosting SharePoint content and configuration databases. SharePoint Online / Microsoft 365 tenants are **not** affected by this CVE.
- **OT/ICS Systems:** None directly. SharePoint Server is enterprise collaboration and document-management software, not an industrial control or field-device platform. Indirect exposure exists only where an organization uses on-premises SharePoint to host OT-adjacent documentation, engineering drawings, vendor manuals, or change-management workflows for plant/ICS environments — in which case compromise of the SharePoint farm could expose sensitive OT documentation or disrupt OT-adjacent business processes without touching OT systems directly (see §2.3).
- **Industries at Risk:** Broad, cross-sector. On-premises SharePoint Server remains common in regulated and legacy-heavy sectors — government, defense, healthcare, financial services, higher education, manufacturing, and utilities — where migration to SharePoint Online/M365 has lagged due to data residency, customization, integration, or connectivity constraints.
- **Geographic Scope:** Global. KEV listing reflects confirmed exploitation without a stated geographic restriction; on-premises SharePoint Server has a large, long-tailed global installed base given its multi-decade history as Microsoft's flagship on-premises collaboration platform.

---

## 2. Technical Analysis

### 2.1 Vulnerability Details

| Field | Details |
|---|---|
| **Vulnerability Type** | Code Injection — Improper Control of Generation of Code (CWE-94) |
| **Attack Vector** | Network |
| **Attack Complexity** | Low |
| **Privileges Required** | **Low** — the attacker must already hold at least a low-privilege, authenticated account or session within the SharePoint environment. This is not a pre-authentication/unauthenticated RCE. |
| **User Interaction** | None required |
| **Scope** | Unchanged |
| **Confidentiality Impact** | High |
| **Integrity Impact** | High |
| **Availability Impact** | High |

**On the PR:L designation — read this carefully.** Microsoft's CNA-reported CVSS 3.1 vector for CVE-2026-65660 is `AV:N/AC:L/PR:L/UI:N/S:U/C:H/I:H/A:H`, base score 8.8 (High). The `PR:L` component is the single most operationally significant detail in this finding and this program is stating it plainly: **exploitation requires the attacker to already hold low-privilege, authenticated access to the SharePoint environment.** This is meaningfully different from a fully unauthenticated, pre-auth remote code execution flaw, and this report will not describe it as "unauthenticated" — the vector string does not support that characterization, and doing so would overstate the flaw's reachability from an anonymous external position.

What this means in practice: the most relevant real-world attack scenario is **not** an anonymous internet scanner popping an exposed SharePoint server cold. It is an attacker who has already obtained some foothold with low-level SharePoint access — for example, a compromised low-privilege employee or contractor account (via phishing, credential stuffing, or reuse from another breach), or an external party granted limited guest/collaboration access to a SharePoint site (a common configuration for vendor portals, extranets, and partner collaboration spaces) — using that low-privilege foothold as the launchpad to inject and execute code with far greater impact than their assigned permissions should allow. This makes CVE-2026-65660 a privilege-escalation-to-RCE chain in practical terms, even though NVD classifies it as a code injection finding, and it places a premium on account hygiene, least-privilege site permissions, and monitoring for anomalous authenticated activity, not just perimeter exposure.

**Affected versions (per NVD):**
- Microsoft SharePoint Enterprise Server 2016 — before 16.0.5565.1001
- Microsoft SharePoint Server 2019 — before 16.0.10417.20198
- Microsoft SharePoint Server Subscription Edition — before 16.0.19725.20522

All three are on-premises SharePoint Server product lines. SharePoint Online (part of Microsoft 365) is a distinct, Microsoft-operated service and is not listed as affected.

### 2.2 Attack Chain

1. **Initial Access** — Attacker obtains or already holds a low-privilege, authenticated SharePoint account or session. Realistic paths to this precondition include a phished or credential-stuffed low-privilege employee/contractor account, an internal user account already compromised through unrelated means, or a legitimately provisioned external guest/limited-access account (vendor portal, partner extranet, client collaboration site) being abused by the party who holds it or by whoever compromises it.
2. **Execution** — Using that low-privilege access, the attacker submits crafted input that SharePoint's server-side logic improperly renders into executable code rather than safely handling as data (the CWE-94 code injection condition), resulting in arbitrary code execution on the SharePoint server with a privilege level exceeding what the attacker's original account should grant.
3. **Persistence** — Server-side code execution on a SharePoint application or web front-end server can be used to establish persistence — web shells, scheduled tasks, or modified SharePoint solution/feature packages that survive routine service restarts — consistent with persistence techniques observed against SharePoint Server in this program's July 2026 machine-key-theft case study.
4. **Impact** — With code execution achieved, the attacker can access or exfiltrate any content the SharePoint farm's service accounts can reach (document libraries, list data, potentially connected line-of-business system data via SharePoint's integration surface), tamper with hosted content or workflows, and — per Previdian's published research (see below) — potentially proceed to a second exploitation stage building on the initial code-execution foothold.

**Reported two-stage exploitation pattern.** Third-party security research firm Previdian published analysis titled "CVE-2026-65660: Previdian Observes Two-Stage SharePoint Exploitation Attempts," indicating that observed real-world exploitation attempts against this CVE have followed a multi-stage attack chain rather than a single-shot exploit. This program has not independently reviewed the full technical detail of Previdian's findings beyond what the publication's title conveys, and is citing it here specifically as corroborating evidence that active exploitation in the wild has reportedly involved staged/sequential attacker actions — consistent with the general shape of "use code injection to gain a foothold, then take a follow-on action" described in the attack chain above — without asserting the specific technical mechanics of either stage. Organizations conducting incident response or threat hunting against this CVE should independently review Previdian's full published analysis (see References) rather than relying on this summary alone.

### 2.3 IT/OT Convergence Risk

SharePoint Server is enterprise collaboration and document-management software; it does not sit inside an OT/ICS control environment and this finding carries no direct IT/OT convergence risk in the traditional sense (no PLC, HMI, SIS, or field-device exposure). This program is stating that directly rather than manufacturing an OT angle for a product that doesn't carry one.

The relevant convergence question for asset-heavy and industrial organizations is narrower and indirect: where an on-premises SharePoint farm is used to host OT-adjacent artifacts — engineering drawings, P&IDs, vendor documentation, change-management or maintenance-work-order workflows, or safety procedure libraries for a plant environment — compromise of that SharePoint instance exposes sensitive operational documentation and can disrupt OT-adjacent business processes (e.g., a maintenance approval workflow) without ever touching the OT network itself. Organizations should treat this as a deployment-specific inventory question — "does our SharePoint farm host content or workflows that OT operations depend on or that would reveal sensitive plant information if exposed?" — rather than a blanket IT/OT finding.

### 2.4 Root Cause

The root cause is improper control of code generation (CWE-94) in SharePoint Server's server-side processing logic: input that should be handled strictly as data is, under certain conditions reachable by an authenticated low-privilege user, instead interpreted and executed as code. This is consistent with a broader pattern this program has now observed across multiple SharePoint Server CVEs disclosed in 2026 — including the deserialization and machine-key-theft issues covered in the July 2026 case study — pointing to a recurring architectural challenge in how SharePoint Server's extensibility and customization surface (web parts, workflows, and server-side rendering paths) validates and constrains input from authenticated but lower-trust users, rather than an isolated one-off coding defect in a single code path.

---

## References & Sources (this file)

| Source | URL |
|---|---|
| NVD, CVE-2026-65660 detail record | https://nvd.nist.gov/vuln/detail/CVE-2026-65660 |
| Microsoft Security Response Center, CVE-2026-65660 update guide | https://msrc.microsoft.com/update-guide/vulnerability/CVE-2026-65660 |
| Previdian, "CVE-2026-65660: Previdian Observes Two-Stage SharePoint Exploitation Attempts" | https://blog.previdian.com/cve-2026-65660-previdian-observes-two-stage-sharepoint-exploitation-attempts/ |
| CISA Known Exploited Vulnerabilities Catalog | https://www.cisa.gov/known-exploited-vulnerabilities-catalog |

*Full reference list with access dates is consolidated in 05_Executive_Summary.md and the case README.*

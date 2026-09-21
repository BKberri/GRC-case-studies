# Threat Intelligence Report
## 2026-09-MSRC-Azure-AI-PlatformBatch
**Date:** 2026-09-21 | **Source:** Microsoft Security Response Center (reported via secondary corroboration, MSRC portal JS-rendered and not independently fetched — CVE IDs/CVSS corroborated across 3+ independent sources each) | **Severity:** High | **Category:** AI-Governance / Cloud-Security

## Executive Overview
Microsoft disclosed a batch of Azure elevation-of-privilege vulnerabilities in mid-September 2026, with the two most severe affecting AI-specific platforms: Azure AI Foundry (Microsoft's managed platform for building, evaluating, and deploying AI models and agents) and Microsoft 365 Copilot (Microsoft's embedded AI assistant across the M365 productivity suite). Both vulnerabilities allowed privilege escalation without requiring the attacker to already hold valid credentials for the affected function, and both were fixed by Microsoft directly on the service side — meaning no customer patch or configuration change was required to close the vulnerability itself, though customers should still review for signs of exploitation prior to the fix.

## Technical Details

### CVE-2026-85889 — Azure AI Foundry Missing Authentication
- **CVSS Score:** 10.0 Critical — CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:C/C:H/I:H/A:H
- **Vulnerability Type:** Missing Authentication for Critical Function (CWE-306)
- **Description:** An unauthenticated attacker could remotely elevate privileges in Azure AI Foundry due to a missing authentication check on a critical function — no credentials or user interaction required.
- **Exploitation Status:** Responsibly disclosed (researcher: Rémy Marot); no evidence of in-the-wild exploitation; not in CISA KEV.
- **Remediation:** Server-side Microsoft fix applied; customers should review logs from before 2026-09-17 for privileged activity, new service principals, role assignments, and API connections as a precaution.

### CVE-2026-85885 — Microsoft 365 Copilot Command Injection
- **CVSS Score:** 9.9 Critical — CVSS:3.1/AV:N/AC:L/PR:L/UI:N/S:C/C:H/I:H/A:H
- **Vulnerability Type:** Improper Neutralization of Special Elements Used in a Command (CWE-77)
- **Description:** Improper neutralization of special elements in a command allows an already-authorized (low-privilege) attacker with network access to escalate privileges within Copilot.
- **Exploitation Status:** No active exploitation found; awaiting formal NVD analysis.
- **Remediation:** Server-side Microsoft fix indicated; tenant-side action requirement not independently confirmed as of this sweep.

**Threat Actor Attribution:** None for either CVE.
**MITRE ATLAS/ATT&CK Technique IDs:** ML Model Access (ATLAS), T1078 (Valid Accounts) / T1068 (Exploitation for Privilege Escalation) for the post-authentication Copilot path.
**CISA Remediation Due Date:** Not applicable — cloud-side fix, not KEV-listed.

## Affected Technology Context
Azure AI Foundry and Microsoft 365 Copilot represent two different but related trust-boundary surfaces in Microsoft's AI stack: Foundry is the developer-facing platform for building and deploying custom AI models/agents, while Copilot is the embedded, end-user-facing AI assistant layered across Office/M365 data. A missing-authentication flaw in Foundry threatens the integrity of the AI development and deployment pipeline itself; a command-injection elevation-of-privilege flaw in Copilot threatens the boundary between what an ordinary authorized user can ask Copilot to do versus what elevated action it should be able to perform on their behalf. Both point to the same underlying governance question this program has flagged repeatedly: as AI assistant and agent platforms gain deeper, more privileged integration with enterprise data and infrastructure, the authentication and authorization boundaries around that integration are still catching up.

## Intelligence Source Links
- The Hacker News (secondary, MSRC primary not independently fetched): https://thehackernews.com/2026/09/microsoft-patches-cvss-100-azure-ai.html
- Strix CVE database: https://www.strix.ai/cve/CVE-2026-85885
- thewindowsupdate.com (MSRC syndication): https://thewindowsupdate.com/2026/09/17/

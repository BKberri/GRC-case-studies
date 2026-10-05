# Threat Intelligence Report, Storm-3168 (JADEPUFFER)
## First Documented Agentic/AI-Orchestrated Destructive Cloud Attack

**Case ID:** 2026-10-MSRC-Storm3168-AgenticAzureAttack
**Date Identified:** 2026-09-25 (program catch-up entry, see Note below)
**Analyst:** Blaise Kingko
**Classification:** Critical, Confirmed Real-World Incident (Non-CVE)
**Dual-Category:** AI-Governance / Cloud-Security

> **Program Gap Note:** Microsoft published this advisory 2026-09-25, inside the prior run's report window (2026-09-21 to 2026-09-28), but it was not captured by that sweep. It is logged this run as a catch-up entry, dated to its original disclosure date rather than backdated, consistent with this program's no-silent-drop principle (cf. the CVE-2026-63077 TeamCity gap logged the prior run).

---

## 1. Incident Summary

| Field | Detail |
|---|---|
| Threat Actor | Storm-3168 (also tracked as JADEPUFFER) |
| Source | Microsoft Security blog, "Storm-3168: Agentic-driven cloud attacks using compromised service principals" |
| Published | 2026-09-25 |
| Target | Microsoft Azure tenant(s); unnamed affected organization |
| Classification | Confirmed real-world destructive cloud attack, not a theoretical disclosure |
| Significance | First documented case of an "agentic" / AI-orchestrated attack pattern conducting coordinated, parallelized destructive operations across a cloud environment |

## 2. Technical Description, Attack Chain

**Initial Access (T1078.004, Valid Cloud Accounts):** A service principal's client ID, secret, and tenant ID were exposed in a public GitHub issue's edit history. The owner had edited the post to remove the secret, but the plaintext credential remained recoverable via the public revision history, illustrating that redacting a visible secret does not invalidate or remove it from exposure.

**Discovery Phase (~15.5 hours):** Using the compromised service principal, the actor performed over 300 successful read operations enumerating Azure VMs, subscriptions, and resource groups. A second compromised principal enumerated resources across two subscriptions in approximately five seconds. Both used the identical network fingerprint and user agent (`python-requests/2.34.2`), and the actor separately probed internet-facing Azure App Services against sensitive paths (WordPress admin, PHP-CGI, LangFlow validation endpoints, T1190, Exploit Public-Facing Application).

**Destruction Phase (~7 minutes, ~150 operations across 35 minutes):** The actor issued five unique tokens from the compromised principal, four dedicated to deletion operations, one to inventory/key retrieval, with two deletion tokens executing in parallel for 70 seconds, indicating intentional, coordinated parallelization rather than manual, sequential administration. Over 100 storage-account deletion attempts were made (most succeeding until Azure resource locks intervened); SQL database deletions failed due to an unsupported API version; Key Vault, Function App, and App Service plan deletions succeeded. The actor also attempted to delete Azure Site Recovery locks and Backup protection locks (T1490, Inhibit System Recovery), directly targeting the organization's ability to recover.

**Post-Destruction Credential Harvesting (~30 minutes):** Over 30 successful `ListKeys` operations were executed against storage accounts, including Site Recovery–related accounts, positioning the actor for potential future data exfiltration even after the destructive phase concluded.

## 3. The "Agentic" Significance

Microsoft explicitly frames this as part of "a broader shift toward AI-orchestrated attacks, where threat actors can coordinate complex post-compromise operations across cloud environments with greater speed and scale." The parallelized token usage and compressed destruction timeline (7 minutes for the active-deletion phase) are consistent with automated, agent-driven orchestration rather than a human operator manually issuing sequential commands, a qualitatively different threat model than traditional manual intrusion, and directly relevant to this program's standing interest in AI/agentic attack-surface risk.

## 4. Framework Mapping

- **NIST AI RMF:** MAP 1.1 (context of AI-relevant risk, adversarial use of AI/automation to accelerate attack operations), MANAGE 4.1 (risk response for AI-enabled threats)
- **NIST CSF 2.0:** GV.OC-01 (Organizational Context), PR.AA-05 (Access Permissions), DE.CM-01 (Network Monitoring), RS.MI-02 (Incident Mitigation)
- **NIST SP 800-53 Rev 5:** AC-6 (Least Privilege), IR-4 (Incident Handling), CP-9 (System Backup), CP-10 (System Recovery)
- **MITRE ATT&CK:** T1078.004, T1526, T1190, T1485, T1490
- **ISO/IEC 42001:2023:** Clause 8.4 (AI system impact assessment), applicable to the defender's own AI-assisted response tooling (Microsoft's "Project Perception" agents) as much as to the offensive use case

## 5. Indicators of Compromise

| Type | Value |
|---|---|
| IP Address | 45.131.66[.]106 (App Service probing, ARM requests) |
| IP Address | 34.153.223[.]102 (App Service probing) |
| IP Address | 64.20.53[.]230 (App Service probing) |
| User Agent | python-requests/2.34.2 |

## 6. Recommended Immediate Action

Treat any secret ever committed to a public or semi-public repository, including one later "removed" by edit, as permanently compromised and rotate it immediately. Restrict service principal RBAC scope to least privilege, enforce resource locks on backup/recovery infrastructure specifically (since this actor targeted recovery controls directly), and evaluate migration from long-lived service principal secrets to managed identities where feasible.

**Risk Rating: Critical**

---
*Sources: Microsoft Security Blog, "Storm-3168: Agentic-driven cloud attacks using compromised service principals" (2026-09-25); WorkOS, "Storm-3168 explained"; CyberPress, "Storm-3168 Uses Compromised Service Principals to Launch Agentic Attacks on Azure Cloud."*

# Microsoft SharePoint Code Injection (CVE-2026-65660) — Executive Summary

| Field | Details |
|---|---|
| **Case Study ID** | CS-ITOT-2026-09-003 |
| **Risk Register Cross-Reference** | RR-084 |
| **Report Period** | 2026-09-21 to 2026-09-28 |
| **Date** | 2026-09-28 |
| **Author** | Blaise Kingko |
| **Risk Rating** | High (Score 20; see 02_Risk_Assessment.md §4.1 for the explicit rationale distinguishing this from this period's Critical-rated findings) |

---

## 7. Executive Summary

### The Situation

CISA added CVE-2026-65660, a code injection vulnerability affecting on-premises Microsoft SharePoint Server, to its Known Exploited Vulnerabilities Catalog on September 25, 2026, confirming it is being actively exploited. The affected products are SharePoint Enterprise Server 2016, SharePoint Server 2019, and SharePoint Server Subscription Edition — on-premises deployments only; SharePoint Online / Microsoft 365 is not affected. Microsoft rates the flaw 8.8 (High) on CVSS 3.1. Critically, exploitation requires the attacker to already hold low-privilege, authenticated access to the SharePoint environment — this is not an anonymous, unauthenticated attack, and this report does not describe it as one. The realistic attack scenario is a compromised low-privilege internal account, or an external party with limited guest/collaboration access, using that foothold to execute code with far greater impact than their access should allow. Third-party researchers at Previdian report observing a two-stage exploitation pattern in real-world attempts. CISA's federal remediation deadline is September 28, 2026 — today, as of this report — which means any organization that has not yet patched is already past the deadline and should treat this as an overdue emergency action, not a scheduled task.

### The Risk to Us

This is not an isolated event: it is at least the program's second or third distinct SharePoint on-premises finding logged in 2026, following the July 2026 case on SharePoint machine-key theft, and consistent with this program's earlier tracking that a third of four related SharePoint CVEs disclosed earlier this year were confirmed exploited. On-premises SharePoint Server has become a recurring, high-value target for attackers throughout the year — a pattern, not a coincidence. Where SharePoint Server hosts business-critical workflows, controlled documents, or externally-shared extranet content, a successful exploitation exposes that content and can disrupt the processes built on top of it; where SharePoint sites grant external guest or vendor access, that access is precisely the kind of low-privilege foothold this vulnerability's exploitation path depends on.

### What We Are Doing

- Prioritizing emergency patching of all on-premises SharePoint Server farms to the fixed builds identified by Microsoft, treating this as an overdue-deadline item given CISA's September 28 due date has passed as of publication.
- Reviewing SharePoint guest and external-sharing access to identify and tighten the specific population of low-privilege accounts that could satisfy this vulnerability's authentication precondition.
- Coordinating incident-response readiness to verify no prior compromise occurred before patched systems are returned to full production trust, consistent with this program's standard guidance for actively-exploited application-platform findings.
- Cross-referencing this finding against the July 2026 SharePoint machine-key-theft case to confirm that earlier remediation (including machine-key rotation) was fully completed, since incomplete prior remediation compounds risk under this new finding.
- Tracking this finding to full closure under Risk Register row RR-084 and Plan of Action & Milestones item(s) in 06_POAM_Remediation.md.

### What We Need From Leadership

- **Emergency change-approval authority** to patch production SharePoint Server farms outside standard change windows, given the deadline has already elapsed.
- **A decision on guest/external-access policy** for SharePoint extranet sites where business need for external collaboration must be balanced against the access-governance tightening this finding calls for.
- **Sponsorship for a strategic review of on-premises SharePoint Server's future in our environment.** Given that this is at least the second or third SharePoint on-premises KEV finding this program has logged in a single calendar year, we recommend leadership sponsor a considered evaluation of migrating remaining on-premises SharePoint Server workloads to SharePoint Online / Microsoft 365 as a strategic risk-reduction measure. This is a recommendation to evaluate, not a mandate to migrate immediately — legitimate reasons (data residency, customization, connectivity, cost) may keep on-premises deployment the right choice for parts of our environment, and that determination should be made deliberately with full business input, not reactively in response to a single CVE. See 06_POAM_Remediation.md for the specific strategic recommendation and proposed evaluation timeline.

---

## References & Sources

| Source | URL | Date Accessed |
|---|---|---|
| NVD, CVE-2026-65660 detail record | https://nvd.nist.gov/vuln/detail/CVE-2026-65660 | 2026-09-28 |
| Microsoft Security Response Center, CVE-2026-65660 update guide | https://msrc.microsoft.com/update-guide/vulnerability/CVE-2026-65660 | 2026-09-28 |
| Previdian, "CVE-2026-65660: Previdian Observes Two-Stage SharePoint Exploitation Attempts" | https://blog.previdian.com/cve-2026-65660-previdian-observes-two-stage-sharepoint-exploitation-attempts/ | 2026-09-28 |
| CISA Known Exploited Vulnerabilities Catalog | https://www.cisa.gov/known-exploited-vulnerabilities-catalog | 2026-09-28 |

---

## Revision History

| Version | Date | Author | Changes |
|---|---|---|---|
| 1.0 | 2026-09-28 | Blaise Kingko | Initial publication |

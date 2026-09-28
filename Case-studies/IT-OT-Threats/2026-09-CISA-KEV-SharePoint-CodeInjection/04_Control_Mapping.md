# Microsoft SharePoint Code Injection (CVE-2026-65660) — Framework Control Mapping

| Field | Details |
|---|---|
| **Case Study ID** | CS-ITOT-2026-09-003 |
| **Risk Register Cross-Reference** | RR-084 |
| **Date** | 2026-09-28 |
| **Author** | Blaise Kingko |

---

## 3. Framework Impact Analysis

### 3.1 NIST CSF 2.0 Mapping

| CSF Function | Subcategory | Gap or Finding |
|---|---|---|
| **GOVERN** | GV.RM-04 (risk appetite and tolerance statements inform decisions) | Organizations lacking an explicit risk-tolerance statement for "internet-facing application platform with authenticated-user exploitation history" will struggle to consistently prioritize this finding against other concurrent KEV entries this reporting period. |
| **IDENTIFY** | ID.AM-02 (software platforms and applications are inventoried); ID.RA-01 (vulnerabilities are identified and recorded) | Requires an accurate inventory of on-premises SharePoint Server instances, build versions, and — critically — an inventory of which sites grant external guest/partner access, since that population defines the realistic PR:L-exploitable attack surface. |
| **PROTECT** | PR.AA-05 (access permissions and authorizations are managed, incorporating least privilege); PR.PS-06 (secure software development practices are integrated) | Least-privilege enforcement on SharePoint site permissions and guest/external-sharing governance directly reduces the population of accounts that satisfy this CVE's PR:L precondition; PR.PS-06 reflects the upstream vendor code-injection root cause this program cannot control but should track via patch SLA. |
| **DETECT** | DE.CM-01 (networks and network services are monitored); DE.CM-03 (personnel activity and technology usage are monitored) | Requires monitoring for anomalous authenticated SharePoint activity — a low-privilege or guest account performing actions inconsistent with its normal usage pattern is the key detection signal for this specific attack chain, more so than network-perimeter monitoring alone. |
| **RESPOND** | RS.AN-03 (forensic analysis is performed); RS.MI-02 (incidents are mitigated) | Response plan should include IoC review before returning a patched SharePoint farm to production, consistent with this program's guidance across other 2026 perimeter/application-platform findings — patching without prior compromise verification risks destroying forensic evidence of a pre-patch intrusion. |
| **RECOVER** | RC.RP-01 (recovery plan is executed) | Recovery planning should explicitly address the RPO caution in 03_BIA.md §3 — a backup taken after initial compromise but before detection can reintroduce a persistence mechanism on restore. |

### 3.2 NIST SP 800-53 Rev 5 Control Mapping

| Control Family | Control ID | Control Name | Finding |
|---|---|---|---|
| Access Control | AC-6 | Least Privilege | Directly relevant given the PR:L exploitation precondition — enforcing least privilege on SharePoint site permissions and guest access reduces the realistic attacker population. |
| Access Control | AC-2 | Account Management | External guest/partner account provisioning and periodic access review for SharePoint extranet sites should be governed under formal account-management procedures, not ad hoc site-owner discretion. |
| System and Information Integrity | SI-2 | Flaw Remediation | Core control for this finding — timely patching to the fixed builds (16.0.5565.1001+ / 16.0.10417.20198+ / 16.0.19725.20522+) is the primary remediation action; see 06_POAM_Remediation.md. |
| System and Information Integrity | SI-10 | Information Input Validation | Addresses the underlying CWE-94 root cause at the vendor code level; tracked here as a control this program cannot directly implement but should verify is addressed in the vendor patch. |
| System and Information Integrity | SI-4 | System Monitoring | Supports detection of anomalous authenticated activity consistent with exploitation of the PR:L precondition. |
| Audit and Accountability | AU-6 | Audit Record Review, Analysis, and Reporting | Post-incident and ongoing review of SharePoint audit logs for authenticated-user activity anomalies, particularly around guest/external accounts. |
| Contingency Planning | CP-9 | System Backup | Supports the RPO caution in 03_BIA.md — backup integrity verification should account for possible pre-detection compromise. |

### 3.3 ISO 27001:2022 Annex A Mapping

| Annex A Clause | Control | Finding |
|---|---|---|
| A.8.8 | Management of Technical Vulnerabilities | Core control — this finding is a textbook case for a formal technical-vulnerability-management process with a defined emergency patch SLA for KEV-listed findings. |
| A.8.28 | Secure Coding | Addresses the upstream vendor root cause (CWE-94 improper input handling); relevant to track as a vendor-assurance expectation even though the organization does not control SharePoint Server's source code directly. |
| A.5.15 | Access Control | Directly relevant given the PR:L precondition — access control policy for SharePoint site permissions and guest/external sharing is a primary compensating control. |
| A.8.16 | Monitoring Activities | Supports detection of anomalous authenticated behavior consistent with exploitation of this CVE's attack chain. |
| A.5.30 | ICT Readiness for Business Continuity | Ties to the BIA's RTO/RPO framing (03_BIA.md) — SharePoint-dependent business processes should be reflected in continuity planning proportionate to their criticality tier. |

### 3.4 CIS Controls v8 Mapping

| CIS Control | Safeguard | Finding / Remediation |
|---|---|---|
| CIS Control 7 — Continuous Vulnerability Management | 7.4 (Perform automated application patch management); 7.5 (Perform automated vulnerability scans) | Emergency patch deployment to fixed SharePoint Server builds is the primary remediation; ongoing vulnerability scanning should specifically flag any SharePoint farm still on a pre-fix build. |
| CIS Control 6 — Access Control Management | 6.1 (Establish an access granting process); 6.2 (Establish an access revoking process) | Governs provisioning and de-provisioning of SharePoint guest/external-collaboration accounts — the population most relevant to the PR:L precondition. |
| CIS Control 16 — Application Software Security | 16.11 (Leverage vetted modules or services for application security components) | Reflects reliance on Microsoft's own secure-development lifecycle for SharePoint Server; the organization's control is limited to timely consumption of the vendor's fix. |
| CIS Control 8 — Audit Log Management | 8.5 (Collect detailed audit logs) | Supports detection of anomalous authenticated SharePoint activity, consistent with DE.CM-03 and AU-6 above. |

---

## References

| Source | URL |
|---|---|
| NVD, CVE-2026-65660 | https://nvd.nist.gov/vuln/detail/CVE-2026-65660 |
| MSRC, CVE-2026-65660 update guide | https://msrc.microsoft.com/update-guide/vulnerability/CVE-2026-65660 |
| CISA KEV Catalog | https://www.cisa.gov/known-exploited-vulnerabilities-catalog |

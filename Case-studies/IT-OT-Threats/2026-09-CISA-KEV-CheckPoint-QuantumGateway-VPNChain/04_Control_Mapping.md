# Framework Control Mapping
## Check Point Quantum Security Gateway & Management Server Dual RCE (CVE-2026-85102 / CVE-2026-93616)

| Field | Details |
|---|---|
| **Case Study ID** | CS-ITOT-2026-09-002 |
| **Risk Register Reference** | RR-080 |
| **Report Period** | 2026-09-21 to 2026-09-28 |
| **Date** | 2026-09-28 |
| **Author** | Blaise Kingko |

---

## 3. Framework Impact Analysis

### 3.1 NIST CSF 2.0 Mapping

| CSF Function | Subcategory | Gap or Finding |
|---|---|---|
| **GOVERN** | GV.RM-04 (risk response and monitoring reflects risk tolerance) | No standing emergency-patch SLA tied to CISA KEV additions existed before this event; the three-day federal deadline exceeded most vendor's normal change-control cadence. |
| **GOVERN** | GV.SC-06 (supplier risk assessed pre-relationship, monitored ongoing) | Check Point sits in a single-vendor concentration for both perimeter VPN and its management plane, which is exactly the concentration this finding shows the risk of. |
| **IDENTIFY** | ID.AM-02 (software platforms and applications inventoried) | Organizations needed an accurate inventory of exact Gaia OS / Gaia Embedded build and jumbo hotfix take to determine exposure quickly; incomplete asset inventories slowed triage. |
| **IDENTIFY** | ID.RA-01 (vulnerabilities identified and recorded) | Gap closed by this case study; the underlying finding is whether the organization had a process to ingest KEV additions same-day rather than on the next scheduled vulnerability review. |
| **PROTECT** | PR.AA-01 (identities and credentials managed for authorized users/processes) | Not directly the root cause, both CVEs are pre-authentication, but relevant to limiting blast radius: strong device and administrator identity controls on the management server limit what a post-compromise attacker can do next. |
| **PROTECT** | PR.PS-04 (log configuration and audit records generated and available) | Gateways and management servers without verbose logging of certificate validation failures and file upload activity cannot support the compromise assessment this incident requires. |
| **PROTECT** | PR.PS-01 (configuration management practices established) | Root cause of both CVEs sits in the vendor's own code, but the organization's own patch and configuration management cadence for internet-facing appliances is the control that determines how long the organization stays exposed after a fix ships. |
| **DETECT** | DE.CM-01 (networks and network services monitored for anomalous events) | Certificate validation failures during VPN negotiation and unexpected file writes on the management server are both detectable signals that most organizations were not specifically monitoring for prior to this disclosure. |
| **DETECT** | DE.CM-09 (computing hardware and software monitored for unauthorized changes) | Unauthorized policy pushes from a compromised management server would show up here if change monitoring on gateway configuration is in place; many environments monitor endpoint change but not centrally-pushed firewall policy change. |
| **RESPOND** | RS.MA-01 (incident response plan executed once an incident is declared) | This event tests whether the incident response plan has a defined path for "vendor discloses active exploitation of our internet-facing perimeter device," distinct from a generic malware or phishing playbook. |
| **RESPOND** | RS.AN-03 (analysis performed to establish what occurred during an incident) | Compromise assessment for devices exposed during the exploitation window (systems internet-reachable between initial exploitation and patch application) is the specific analysis this incident requires beyond simply patching. |
| **RECOVER** | RC.RP-01 (recovery plan executed once activated) | Recovery for the management server needs to restore from a validated pre-compromise configuration baseline, not simply reapply the current (possibly attacker-influenced) policy state; see 03_BIA.md Section 3. |

### 3.2 NIST SP 800-53 Rev 5 Control Mapping

| Control Family | Control ID | Control Name | Finding |
|---|---|---|---|
| System and Communications Protection | SC-8 | Transmission Confidentiality and Integrity | VPN transmission integrity depends on the certificate validation step CVE-2026-85102 defeats; the control objective is intact in design but was not achieved in the vendor's implementation. |
| System and Communications Protection | SC-17 | Public Key Infrastructure Certificates | Directly implicated by CVE-2026-85102's root cause, improper certificate trust validation during VPN negotiation; organizations should confirm PKI trust anchors and revocation checking are correctly enforced post-patch, not assumed. |
| System and Information Integrity | SI-2 | Flaw Remediation | Core control gap exercised by this incident: time from vendor patch availability to deployment across the full gateway and management-server fleet, measured against the CISA three-day deadline. |
| System and Information Integrity | SI-4 | System Monitoring | Detection of exploitation attempts against either CVE requires monitoring tuned to certificate negotiation failures and management-server upload activity, which is a non-default logging and alerting configuration for many deployments. |
| Risk Assessment | RA-5 | Vulnerability Monitoring and Scanning | Organizations need a scanning and vendor-advisory ingestion process fast enough to catch a KEV addition with a three-day remediation window, which is faster than most quarterly or monthly scan cadences support on its own. |
| Access Control | AC-17 | Remote Access | The VPN gateway is the remote access control point itself; its compromise is a direct failure of the mechanism AC-17 is meant to secure. |
| Identification and Authentication | IA-3 | Device Identification and Authentication | Certificate-based device and endpoint authentication during VPN negotiation is the specific mechanism CVE-2026-85102 undermines. |
| Configuration Management | CM-8 | System Component Inventory | An accurate, current inventory of exact appliance model, OS build, and jumbo hotfix take is the prerequisite for determining exposure and confirming remediation; incomplete inventories were the single biggest source of triage delay in comparable prior incidents. |
| Contingency Planning | CP-2 | Contingency Plan | The business impact analysis in 03_BIA.md and the recovery priority tiering it establishes should be reflected in the organization's formal contingency plan for perimeter infrastructure loss. |
| Incident Response | IR-4 | Incident Handling | This event requires an incident handling path specific to "confirmed active exploitation of an internet-facing security appliance," including compromise assessment before treating patching alone as remediation complete. |

### 3.3 ISO 27001:2022 Mapping

| Annex A Clause | Control | Finding |
|---|---|---|
| A.8.24 | Use of Cryptography | Directly relevant to CVE-2026-85102's root cause in certificate trust validation; organizations should verify cryptographic trust configuration on the gateway, not assume it is correct because a certificate is present. |
| A.8.8 | Management of Technical Vulnerabilities | Core control tested by this event: identifying that CVE-2026-85102 and CVE-2026-93616 applied to the organization's specific deployment and acting inside the CISA remediation window. |
| A.8.20 | Networks Security | The gateway's role in network segmentation, including any IT/OT boundary function, is the asset this finding places at risk; network security controls around and behind the gateway should be reviewed as a compensating layer, not solely the gateway's own patch status. |
| A.8.9 | Configuration Management | Confirming exact firmware and hotfix state across the fleet, and confirming the management server's pushed configuration was not altered during the exposure window, both fall under configuration management. |
| A.5.23 | Information Security for Use of Cloud Services | Applicable where the management server or its logging/SIEM integration is cloud-hosted; verify the same exposure assessment extends to any cloud-adjacent component of the management architecture. |
| A.8.16 | Monitoring Activities | Monitoring for certificate validation failures and unexpected management-server file activity is the specific detection capability this incident calls for. |
| A.5.30 | ICT Readiness for Business Continuity | The recovery priority tiering established in the business impact analysis should inform ICT continuity planning specifically for perimeter and management-plane infrastructure. |

### 3.4 CIS Controls v8 Mapping

| CIS Control | Safeguard | Finding / Remediation |
|---|---|---|
| CIS Control 7: Continuous Vulnerability Management | 7.1, 7.5, 7.6 | Establish and follow a documented process to ingest CISA KEV additions and act within vendor and regulatory remediation windows; automate vulnerability scans against the specific gateway and management-server asset class. |
| CIS Control 12: Network Infrastructure Management | 12.1, 12.5 | Maintain an up-to-date, accurate inventory of network infrastructure including exact firmware and hotfix version; centrally manage and securely configure network infrastructure devices, which includes hardening the management server itself against the class of weakness CVE-2026-93616 exploited. |
| CIS Control 4: Secure Configuration of Enterprise Assets and Software | 4.1 | Establish and maintain a secure configuration baseline for the gateway and management server, including disabling or restricting any upload functionality on the management server not required for normal operation. |
| CIS Control 13: Network Monitoring and Defense | 13.1, 13.3 | Deploy and tune network monitoring capable of detecting certificate validation anomalies during VPN negotiation and unusual file-write or script-execution activity on the management server. |

---

## Revision History

| Version | Date | Author | Changes |
|---|---|---|---|
| 1.0 | 2026-09-28 | Blaise Kingko | Initial publication |

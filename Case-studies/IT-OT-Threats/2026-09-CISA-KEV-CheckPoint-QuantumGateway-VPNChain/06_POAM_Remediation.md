# Plan of Action & Milestones (POA&M)
## Check Point Quantum Security Gateway & Management Server Dual RCE (CVE-2026-85102 / CVE-2026-93616)

| Field | Details |
|---|---|
| **Case Study ID** | CS-ITOT-2026-09-002 |
| **Risk Register Reference** | RR-080 |
| **Report Period** | 2026-09-21 to 2026-09-28 |
| **Date** | 2026-09-28 |
| **Author** | Blaise Kingko |

This POA&M tracks remediation for CVE-2026-85102 (Quantum Security Gateway, unauthenticated RCE via improper certificate validation) and CVE-2026-93616 (Quantum/Multi-Domain Security Management, unauthenticated RCE via path traversal), both added to the CISA KEV catalog on 2026-09-22 with a federal remediation deadline of 2026-09-25.

---

## 6. Recommended Controls & Remediation

### Immediate Actions (0–7 Days)

| POAM ID | Weakness | Framework Ref | Remediation Action | Resources Required | Milestone/Target Date | Status | Owner |
|---|---|---|---|---|---|---|---|
| POAM-001 | Unpatched Quantum Security Gateway fleet vulnerable to unauthenticated RCE via CVE-2026-85102 | NIST 800-53 SI-2, SC-17; CSF PR.PS-01; ISO A.8.8 | Apply Check Point jumbo hotfix take per sk1000117 to all internet-facing Quantum Security Gateway appliances | Network security engineering, emergency change approval, Check Point TAC support | 2026-09-25 | Complete | Network Security Engineering |
| POAM-002 | Unpatched Quantum/Multi-Domain Security Management vulnerable to unauthenticated RCE via CVE-2026-93616 | NIST 800-53 SI-2; CSF PR.PS-01; ISO A.8.8 | Apply Check Point jumbo hotfix take per sk1000171 to all Quantum Security Management and Multi-Domain Security Management servers | Network security engineering, emergency change approval, Check Point TAC support | 2026-09-25 | Complete | Network Security Engineering |
| POAM-003 | Unknown whether internet-exposed gateways or management servers were compromised prior to patching | NIST 800-53 IR-4, RS.AN-03 | Run forensic compromise assessment on every gateway and management server that was internet-reachable during the exposure window (2026-09-22 through patch date) | Incident response team, forensic tooling, log retention from affected devices | 2026-09-29 | In Progress | Incident Response Team |
| POAM-004 | Internal-segment and non-internet-facing gateways not yet confirmed patched | NIST 800-53 SI-2 | Extend jumbo hotfix deployment to remaining gateway and management-server instances outside the initial internet-facing patch wave | Network security engineering, standard change window | 2026-09-29 | In Progress | Network Security Engineering |
| POAM-005 | Certificate trust configuration not independently verified post-patch | NIST 800-53 SC-17; ISO A.8.24 | Verify PKI trust anchors and revocation checking on patched gateways are correctly enforced, not merely assumed restored by the patch | Network security engineering, PKI/identity team | 2026-09-30 | Open | Network Security Engineering |

### Short-Term Actions (8–30 Days)

| POAM ID | Weakness | Framework Ref | Remediation Action | Resources Required | Milestone/Target Date | Status | Owner |
|---|---|---|---|---|---|---|---|
| POAM-006 | No detection coverage for certificate validation failures or anomalous management-server file activity | NIST 800-53 SI-4; CSF DE.CM-01; CIS Control 13 | Deploy and tune SIEM/IDS rules for VPN certificate negotiation failures and unexpected file writes or script execution on the management server | SOC / detection engineering, SIEM engineering time | 2026-10-10 | Open | SOC / Detection Engineering |
| POAM-007 | Management server upload functionality broader than operationally necessary | NIST 800-53 CM-7; ISO A.8.9; CIS Control 4 | Review and restrict management server upload/admin-facing functionality to the minimum required for operations; disable or firewall any unused upload paths | Network security engineering, Check Point configuration review | 2026-10-15 | Open | Network Security Engineering |
| POAM-008 | Asset inventory does not reliably capture exact Gaia OS/Embedded build and jumbo hotfix take per device | NIST 800-53 CM-8; CSF ID.AM-02; CIS Control 12 | Update CMDB with confirmed build and hotfix take for every gateway and management-server instance, tied to a recurring reconciliation process | IT asset management, network security engineering | 2026-10-20 | Open | IT Asset Management |
| POAM-009 | No formal emergency-patch SLA tied to CISA KEV additions | NIST 800-53 RA-5; CSF GV.RM-04 | Establish and document an emergency-patch SLA triggered automatically by a CISA KEV addition affecting owned assets, independent of standard change cadence | GRC/risk management, change advisory board sign-off | 2026-10-22 | Open | GRC / Risk Management |

### Strategic Recommendations (30–90 Days)

| POAM ID | Weakness | Framework Ref | Remediation Action | Resources Required | Milestone/Target Date | Status | Owner |
|---|---|---|---|---|---|---|---|
| POAM-010 | Centralized management server architecture concentrates control-plane risk with no compensating segmentation | CSF GV.SC-06, ID.RA-01; ISO A.8.20 | Conduct an architecture review of the management server's blast radius and evaluate network segmentation or tiering of the management plane itself | Network architecture team, GRC/risk management | 2026-12-15 | Open | Network Architecture / GRC |
| POAM-011 | Continued reliance on internet-facing perimeter VPN as the default remote-access model, now the fourth such KEV entry this program has logged this year | CSF GV.RM-04; NIST 800-53 AC-17 | Evaluate compensating or replacement remote-access architectures (for example, brokered/zero-trust access models) given the recurring pattern of perimeter VPN appliance KEV entries | CISO office, network architecture, budget approval | 2026-12-27 | Open | CISO Office |
| POAM-012 | No tested incident response procedure for a combined gateway-plus-management-plane compromise scenario | NIST 800-53 IR-4, CP-2; CSF RS.MA-01 | Run a tabletop exercise simulating simultaneous gateway and management-server compromise, validating the recovery priority tiering in 03_BIA.md | Incident response team, business continuity, tabletop facilitation | 2026-11-30 | Open | Incident Response Team |

### OT-Specific Controls

| POAM ID | Weakness | Framework Ref | Remediation Action | Resources Required | Milestone/Target Date | Status | Owner |
|---|---|---|---|---|---|---|---|
| POAM-013 | Sites using a Quantum Security Gateway as the sole IT/OT segmentation boundary cannot yet confirm segmentation integrity was not violated | ISO A.8.20; NIST 800-53 SC-7; CSF ID.RA-01 | Validate OT-facing segmentation rules on patched gateways against baseline policy and confirm no unauthorized rule changes occurred during the exposure window | IT/OT convergence team, OT network engineering | 2026-10-05 | In Progress | IT/OT Convergence Team |
| POAM-014 | Remote vendor and engineering access into OT networks routed through affected gateways not yet re-verified | NIST 800-53 AC-17; CSF PR.AA-01 | Re-verify and, where warranted, rotate credentials and access grants for third-party vendor and engineer remote access paths that route through affected gateways | IT/OT convergence team, vendor management, identity team | 2026-10-10 | Open | IT/OT Convergence Team |

---

## Revision History

| Version | Date | Author | Changes |
|---|---|---|---|
| 1.0 | 2026-09-28 | Blaise Kingko | Initial publication |

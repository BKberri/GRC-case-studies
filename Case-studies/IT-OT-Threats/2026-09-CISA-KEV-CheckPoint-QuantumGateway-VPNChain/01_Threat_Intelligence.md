# CISA KEV: Check Point Quantum Security Gateway & Management Server Dual RCE | VPN-to-Management Plane Chain Risk Analysis
## Threat Intelligence Report

---

## Case Study Metadata

| Field | Details |
|---|---|
| **Case Study ID** | CS-ITOT-2026-09-002 |
| **Date Published** | 2026-09-28 |
| **Incident Date** | 2026-09-22 (CISA KEV addition) |
| **Author** | Blaise Kingko |
| **Threat Category** | IT/OT: Network (VPN gateway + centralized security management plane) |
| **CVE / Advisory ID** | CVE-2026-85102, CVE-2026-93616 |
| **CVSS Score** | 9.8 Critical (both CVEs) |
| **Affected Vendor** | Check Point Software Technologies |
| **Affected Product** | Quantum Security Gateway (Gaia OS / Gaia Embedded) and Quantum Security Management / Multi-Domain Security Management, R80.x–R82.20 |
| **Intelligence Source** | CISA KEV, NIST NVD, Check Point Security Advisory |
| **Exploitation Status** | Actively exploited (KEV-confirmed) |

---

## 1. Incident Summary

### 1.1 What Happened
On September 22, 2026, CISA added two Check Point vulnerabilities to its Known Exploited Vulnerabilities catalog after confirming active exploitation of both. CVE-2026-85102 lets an attacker with no valid credentials defeat the certificate check a Check Point VPN gateway is supposed to run before trusting a connection, and use that gap to run arbitrary code directly on the gateway. CVE-2026-93616 lets an attacker with no valid credentials upload and execute a malicious script on the Check Point server that manages security policy for those gateways. Check Point issued its own "Action Required" advisory the same week confirming active exploitation, and CISA gave federal civilian agencies a three-business-day remediation window, with a due date of September 25.

### 1.2 Why It Matters
A VPN gateway exists specifically to keep unauthenticated attackers out while letting trusted remote users in. Both vulnerabilities defeat that purpose without a single valid credential, and one of them reaches the system that sets policy for every gateway a given deployment manages, not just the one under direct attack.

### 1.3 Affected Environments
- **IT Systems:** Internet-facing VPN concentrators, perimeter firewalls, remote-access gateways, and the centralized management servers that administer them across enterprise networks.
- **OT/ICS Systems:** Sites that use a Check Point Quantum Security Gateway as the IT/OT boundary firewall, or as the VPN path for remote vendor, integrator, or engineer access into a control network, inherit both vulnerabilities directly. The gateway is frequently the only device standing between the corporate network and the OT zone.
- **Industries at Risk:** Any sector running Check Point Quantum appliances at the network perimeter, with particular exposure for financial services, healthcare, manufacturing, energy, utilities, and other critical infrastructure operators that use Check Point specifically to segment IT from OT.
- **Geographic Scope:** Global. Quantum Security Gateway and Quantum/Multi-Domain Security Management are deployed worldwide across the affected R80.x–R82.20 version trains, and exploitation requires only network reachability to the appliance, not a specific region or industry.

---

## 2. Technical Analysis

### 2.1 Vulnerability Details

**CVE-2026-85102: Check Point Multiple Products Improper Certificate Validation Vulnerability**

| Field | Details |
|---|---|
| **Vulnerability Type** | Improper Certificate Validation (CWE-295) |
| **Attack Vector** | Network |
| **Attack Complexity** | Low |
| **Privileges Required** | None |
| **User Interaction** | None |
| **Scope** | Unchanged |
| **Confidentiality Impact** | High |
| **Integrity Impact** | High |
| **Availability Impact** | High |
| **CVSS 3.1 Base Score** | 9.8 (Critical): CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H |

NVD/CNA description: "Improper certificate trust validation during VPN negotiation in Check Point Quantum Security Gateway may allow an unauthenticated remote attacker to execute arbitrary code on the Gateway."

**CVE-2026-93616: Check Point Multiple Products Path Traversal Vulnerability**

| Field | Details |
|---|---|
| **Vulnerability Type** | Path Traversal / Arbitrary File Upload (CWE-22) |
| **Attack Vector** | Network |
| **Attack Complexity** | Low |
| **Privileges Required** | None |
| **User Interaction** | None |
| **Scope** | Unchanged |
| **Confidentiality Impact** | High |
| **Integrity Impact** | High |
| **Availability Impact** | High |
| **CVSS 3.1 Base Score** | 9.8 (Critical): CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H |

NVD/CNA description: "A directory traversal and file upload vulnerability allows an unauthenticated attacker to upload and execute arbitrary scripts on Check Point Management Server."

### 2.2 Attack Chain

Each CVE stands on its own as a complete, unauthenticated path to remote code execution. Neither needs the other to be dangerous.

**Path A: VPN Gateway (CVE-2026-85102):**
1. **Initial Access**: An attacker reaches the gateway's VPN negotiation endpoint over the network, no credentials required.
2. **Execution**: The gateway's certificate trust validation logic fails to properly verify the presented certificate during negotiation, and the attacker uses that gap to reach a code execution primitive on the Gaia OS / Gaia Embedded platform.
3. **Impact**: Arbitrary code execution on the gateway itself, with the gateway's own high-privilege access to decrypted VPN traffic, routing tables, and any adjacent network zones it bridges.

**Path B: Management Server (CVE-2026-93616):**
1. **Initial Access**: An attacker reaches an unauthenticated upload function on Quantum Security Management or Multi-Domain Security Management.
2. **Execution**: Insufficient path sanitization lets the attacker traverse outside the intended upload directory and place an executable script inside a web-reachable path, then trigger it.
3. **Persistence**: A management server that pushes policy on a schedule or on demand gives an attacker a durable foothold from which to alter firewall rules, VPN configuration, or logging settings across every gateway it administers.
4. **Impact**: Arbitrary code execution on the management server, and from there, potential control over the policy and configuration pushed to every managed gateway.

**Composite Chain (Analyst Assessment, Not a Confirmed TTP):** Because CVE-2026-85102 and CVE-2026-93616 were disclosed by the same vendor in the same week and both affect infrastructure that is architecturally linked, gateways are managed by exactly this class of management server, they form a realistic two-vulnerability chain on paper. An attacker who takes the management server through CVE-2026-93616 inherits the ability to push malicious policy, configuration, or even a hostile certificate trust store to every gateway under that server's control, which would make the management server compromise the more severe of the two by blast radius alone. There is no public evidence as of this writing that the two vulnerabilities are being exploited together by a single threat actor as one observed chain. This composite scenario is this analyst's own risk reasoning connecting two separately disclosed CVEs from the same vendor and disclosure week, not a confirmed attacker technique, and it is presented here as a plausible worst case that the risk assessment and remediation plan treat with the seriousness that possibility warrants.

### 2.3 IT/OT Convergence Risk
Check Point Quantum Security Gateways are a common choice for the IT/OT boundary firewall precisely because they combine VPN, firewall, and intrusion prevention in one appliance. That combination now cuts the other way. A gateway serving as the sole segmentation point between the corporate network and an OT environment, and simultaneously as the VPN path for remote vendor or engineer access into that same OT environment, means CVE-2026-85102 hands an unauthenticated attacker a foothold on the one device the OT network's isolation depends on. Where the management server for that gateway is centralized alongside IT infrastructure, CVE-2026-93616 gives an attacker a path from the IT side into the policy engine controlling OT-facing segmentation rules, without ever touching the OT network directly.

### 2.4 Root Cause
CVE-2026-85102 traces to a failure in certificate trust validation during VPN negotiation. The gateway did not correctly verify the chain of trust or the validity of the certificate presented by the connecting party before proceeding to establish the session, which is the specific weakness class captured by CWE-295. CVE-2026-93616 traces to insufficient sanitization of file paths supplied during an upload operation on the management server, which allowed a supplied path to traverse outside the intended storage directory, the weakness class captured by CWE-22. Both are, in their own way, input and trust validation failures at the boundary where an unauthenticated party first touches the product, which is exactly the boundary a perimeter security product exists to defend.

---

## References & Sources

| Source | URL | Date Accessed |
|---|---|---|
| CISA: Known Exploited Vulnerabilities Catalog Update | https://www.cisa.gov/news-events/alerts/2026/09/22/cisa-adds-four-known-exploited-vulnerabilities-catalog | 2026-09-28 |
| NVD: CVE-2026-85102 Detail | https://nvd.nist.gov/vuln/detail/CVE-2026-85102 | 2026-09-28 |
| NVD: CVE-2026-93616 Detail | https://nvd.nist.gov/vuln/detail/CVE-2026-93616 | 2026-09-28 |
| Check Point Security Advisory: Action Required | https://blog.checkpoint.com/security/security-advisory-action-required-active-exploitation-of-cve-2026-85102-and-a-management-pre-authentication-vulnerability-cve-2026-93616/ | 2026-09-28 |
| Check Point Support: sk1000117 | https://support.checkpoint.com/results/sk/sk1000117 | 2026-09-28 |
| Check Point Support: sk1000171 | https://support.checkpoint.com/results/sk/sk1000171 | 2026-09-28 |

Exact jumbo hotfix take thresholds by version train (which specific build resolves each CVE on which R80–R82.20 release) are maintained by Check Point in sk1000117 and sk1000171 and should be pulled directly from those pages at patch time rather than reproduced here, since Check Point updates them as new takes ship.

---

## Revision History

| Version | Date | Author | Changes |
|---|---|---|---|
| 1.0 | 2026-09-28 | Blaise Kingko | Initial publication |

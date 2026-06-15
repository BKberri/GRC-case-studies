# Risk Assessment
## Case: CVE-2026-45657 / CVE-2026-47291 — Microsoft June 2026 Patch Tuesday: Wormable Kernel & HTTP.sys RCE
**Date:** 2026-06-15 | **Analyst:** Blaise Kingko | **Classification:** Critical

---

## 1. Risk Identification

| Field | CVE-2026-45657 | CVE-2026-47291 |
|---|---|---|
| **Risk ID** | RR-012 | RR-013 |
| **Threat Category** | Cloud-Security / IT-OT-Threats — Wormable OS Kernel RCE | Cloud-Security — Web Protocol Stack RCE |
| **Affected Asset** | All Windows endpoints, servers, Azure IaaS VMs | All Windows IIS/HTTP.sys web servers, Azure IaaS |
| **CVSS v3.1** | 9.8 Critical | 9.8 Critical |
| **Attack Vector** | Network — no auth, no user interaction | Network — no auth, no user interaction |
| **Special Risk Factor** | WORMABLE — self-propagating across networks | Configurable registry mitigation available |

---

## 2. Likelihood Assessment

| Factor | CVE-2026-45657 | CVE-2026-47291 |
|---|---|---|
| **Likelihood Score** | **4 / 5** | **4 / 5** |
| **Rationale** | Not yet confirmed exploited; wormable profile = PoC public likely within days. EternalBlue went from disclosure to WannaCry in 59 days. Treat as imminent. | No confirmed exploit; trivially exploitable architecture. HTTP.sys mass exploitation risk if PoC emerges. |
| **Exploit Complexity** | Low — network only, no auth, no interaction | Low — network packet to HTTP.sys port |

---

## 3. Impact Assessment

| Factor | CVE-2026-45657 | CVE-2026-47291 |
|---|---|---|
| **Impact Score** | **5 / 5** | **5 / 5** |
| **Rationale** | SYSTEM-level code execution on every unpatched Windows system. Wormable = entire unpatched estate can be compromised in minutes once exploit propagates. WannaCry analogue. | Full server RCE on internet-facing web servers. Initial access to web-hosting infrastructure, lateral movement into cloud environment from DMZ. |

---

## 4. Risk Scoring

| Metric | CVE-2026-45657 | CVE-2026-47291 |
|---|---|---|
| **Likelihood** | 4 | 4 |
| **Impact** | 5 | 5 |
| **Risk Score** | 20 | 20 |
| **Risk Rating** | **Critical** | **Critical** |
| **Inherent Risk** | Critical | Critical |

---

## 5. Cloud-Specific Risk Factors

### Azure IaaS / Windows Server VMs
- CVE-2026-45657 (Wormable Kernel): Azure IaaS VMs running Windows Server are exposed. Microsoft manages the hypervisor layer but the guest OS kernel is customer responsibility. East-west propagation within a VNet segment could compromise an entire workload environment.
- CVE-2026-47291 (HTTP.sys): Azure IaaS web servers with public-facing IIS/HTTP.sys are directly exposed. NSG rules limiting inbound HTTP to known IPs are an effective compensating control if patching is delayed.
- Hyper-V CVEs (CVE-2026-47652, CVE-2026-45641, CVE-2026-45607): VM guest escape vulnerabilities are the most dangerous for cloud environments — a compromised VM can escape to the hypervisor host. Microsoft has responsibility for patching the Azure hypervisor platform; customer VMs require guest OS updates.

### AWS Windows EC2 / ECS/EKS Windows Nodes
- Windows EC2 instances running unpatched Windows Server/Windows 10/11 AMIs are vulnerable to all three CVE clusters
- EC2 security groups restricting inbound SMB/TCP lateral movement reduce wormable propagation risk
- SSM Patch Manager should be used to enforce patch compliance across all Windows EC2

---

## 6. Existing Controls

| Control | CVE-2026-45657 | CVE-2026-47291 |
|---|---|---|
| Endpoint patch management (WSUS/Intune/SSM) | In place — emergency deployment required | In place — emergency deployment required |
| Network segmentation (NSGs, SGs, VPC) | Reduces east-west worm propagation risk | HTTP/HTTPS inbound restriction reduces exposure |
| EDR / XDR (CrowdStrike/Defender for Endpoint) | Partial detection capability; kernel exploit may evade EDR pre-patch | Network-layer RCE may be detected post-execution |
| Registry MaxRequestBytes setting (CVE-2026-47291 only) | N/A | Available — verify all web servers have default or lower value set |
| Web Application Firewall | N/A | WAF may block malformed HTTP requests triggering overflow |

---

## 7. Residual Risk

CVE-2026-45657: Without patch, even with network segmentation, residual risk is **Critical** — wormable propagation can jump segments via compromised bridging hosts. After patch: Low.

CVE-2026-47291: With MaxRequestBytes registry mitigation in place, risk reduces to Medium until patch is applied. After patch: Low.

---

## 8. Risk Treatment

**TREAT — Emergency patch deployment required for both CVEs within 72 hours.** No acceptable risk tolerance for CVSS 9.8 wormable or web-exploitable RCEs.

# Control Mapping Matrix
## Case: CVE-2026-45657 / CVE-2026-47291 — Microsoft June 2026 Patch Tuesday: Wormable Kernel & HTTP.sys RCE
**Date:** 2026-06-15 | **Analyst:** Blaise Kingko

---

## Cross-Framework Control Mapping

| Control Domain | NIST CSF 2.0 | NIST 800-53 Rev 5 | ISO 27001:2022 Annex A | CIS Controls v8 | Status |
|---|---|---|---|---|---|
| **OS Patch Management** | PR.PS-04 | SI-2 (Flaw Remediation) | A.8.8 (Technical Vulnerability Mgmt) | Control 7.4 (Automated App Patch Mgmt) | Emergency deployment required; treat as Tier 1 per BOD 26-04 |
| **Configuration Hardening** | PR.PS-02 | CM-6 (Configuration Settings), CM-7 (Least Functionality) | A.8.9 (Configuration Management) | Control 4.1 (Establish/maintain secure config) | MaxRequestBytes registry setting for HTTP.sys mitigation |
| **Network Segmentation** | PR.IR-01 | SC-7 (Boundary Protection), SC-39 (Process Isolation) | A.8.22 (Segregation of Networks) | Control 12.2 (Establish secure network arch) | Critical for limiting worm propagation before patch is deployed |
| **Vulnerability Scanning** | ID.RA-01 | RA-5 (Vulnerability Scanning) | A.8.8 | Control 7.1, 7.5 | Rescan post-patch to confirm remediation; identify unpatched systems |
| **EDR / Threat Detection** | DE.CM-09, DE.AE-02 | SI-4 (System Monitoring), AU-6 | A.8.16 (Monitoring Activities) | Control 13.7, 13.8 | Ensure EDR signatures updated; enable kernel-level telemetry |
| **Backup & Recovery** | RC.RP-01, RC.RP-04 | CP-9 (System Backup), CP-10 (Recovery) | A.8.13 (Information Backup), A.5.29 (Continuity of Security) | Control 11.2, 11.3 | Verify immutable backup integrity; test restore pre-exploit |
| **Worm Propagation Containment** | DE.CM-01, RS.MI-02 | SC-7, SC-5 (DoS Protection), IR-4 | A.8.22, A.5.26 | Control 12.3, 17.4 | Enforce SMB/RPC restriction between network segments |
| **Cloud Shared Responsibility** | GV.SC-06, PR.AA-05 | CA-7 (Continuous Monitoring), SA-9 | A.5.21 (ICT Supply Chain), A.5.23 (Cloud Security) | Control 4 | Microsoft patches hypervisor; customer patches guest OS — verify each layer |
| **Change Management** | PR.PS-03 | CM-3 (Config Change Control), CM-4 | A.8.32 (Change Management) | Control 4.2 | Document emergency change record for out-of-cycle patch deployment |
| **Incident Response Readiness** | RS.AN-03, RS.MI-01 | IR-4, IR-8 | A.5.24 (IR Planning), A.5.26 | Control 17 | Activate IR plan if exploitation evidence observed; brief BC/DR team on worm scenario |

---

## Cloud Provider Responsibility Matrix

| Layer | CVE-2026-45657 (Kernel) | CVE-2026-47291 (HTTP.sys) | Hyper-V CVEs |
|---|---|---|---|
| **Azure Hypervisor** | Microsoft responsibility | Microsoft responsibility | Microsoft responsibility — patch pushed automatically |
| **Azure Guest OS (Windows VM)** | **Customer responsibility** — apply cumulative update | **Customer responsibility** — apply cumulative update | N/A (host-layer) |
| **AWS EC2 (Windows)** | **Customer responsibility** — update via SSM/WSUS | **Customer responsibility** | N/A |
| **Azure App Service (Windows)** | Microsoft-managed PaaS — monitor Microsoft communications | N/A | N/A |
| **AWS Lambda / PaaS** | Microsoft/AWS-managed — no customer action for managed services | N/A | N/A |

---

## Gap Analysis

| Gap | Severity | Recommendation |
|---|---|---|
| Incomplete Windows patch coverage in cloud IaaS | Critical | Enable AWS SSM Patch Manager and Azure Update Manager for 100% Windows patch coverage with compliance reporting |
| No emergency patch SLA defined | High | Define: CVSS >= 9.0 + wormable/network-exploitable = 72-hour emergency patch SLA across all Windows estates |
| SMB not blocked between VNet/VPC segments | High | Block SMB (TCP 445) between subnets/VNets that do not require file share access; eliminates primary worm propagation vector |
| HTTP.sys MaxRequestBytes not enforced enterprise-wide | Medium | Enforce via Group Policy / SSM Document to set MaxRequestBytes ≤ 65,534 on all web-serving Windows hosts |
| EDR kernel telemetry not enabled on all endpoints | High | Enable CrowdStrike kernel sensor / Defender for Endpoint kernel telemetry on 100% of Windows endpoints |
| Immutable backup coverage < 100% | High | Extend Veeam / AWS Backup / Azure Backup immutable storage to all critical Windows workloads before ransomware event |

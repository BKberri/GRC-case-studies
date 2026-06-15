# Plan of Action & Milestones (POA&M) — Remediation Plan
## Case: CVE-2026-45657 / CVE-2026-47291 — Microsoft June 2026 Patch Tuesday: Wormable Kernel & HTTP.sys RCE
**Date:** 2026-06-15 | **Analyst:** Blaise Kingko | **Risk Rating:** Critical

---

## POA&M Summary

| Field | Value |
|---|---|
| **Primary Weaknesses** | CVE-2026-45657 (Wormable Windows Kernel UAF RCE, CVSS 9.8) and CVE-2026-47291 (HTTP.sys Integer Overflow RCE, CVSS 9.8) |
| **Responsible Parties** | Cloud Platform Engineering (Azure/AWS VMs), Endpoint Engineering (on-prem Windows), IT Operations |
| **Patch Source** | Microsoft June 2026 Cumulative Update (available via Windows Update, WSUS, Intune, AWS SSM, Azure Update Manager) |
| **Emergency Target** | 100% critical Windows systems patched by June 18, 2026 (72 hours from disclosure date) |
| **Full Estate Target** | 100% Windows estate patched by June 22, 2026 |

---

## Remediation Milestones

| Milestone | Action | Owner | Due Date | Status |
|---|---|---|---|---|
| **M1 — Registry Workaround (HTTP.sys)** | Set `HKLM\SYSTEM\CurrentControlSet\Services\HTTP\Parameters\MaxRequestBytes = 16384` (or any value ≤ 65,534) on ALL internet-facing IIS/HTTP.sys servers via GPO and SSM Document. Eliminates CVE-2026-47291 exposure immediately without rebooting. | Windows Sysadmin / Cloud Ops | 2026-06-15 (TODAY) | Immediate |
| **M2 — Network Segmentation Review** | Confirm SMB (TCP 445) is blocked between all network segments that do not require it. Apply NSG/Security Group rules to block SMB east-west on cloud VNets/VPCs. Apply Windows Firewall rules on endpoints. Limits worm propagation if exploit goes public before patch. | Network Engineering / Cloud Security | 2026-06-15 (TODAY) | Immediate |
| **M3 — Backup Integrity Verification** | Verify last-known-good backup for all Tier 1 and Tier 2 systems. Confirm immutable/offline backup exists for all domain controllers, file servers, ERP systems, cloud databases. | Backup/Recovery Team | 2026-06-16 | Priority |
| **M4 — Emergency Patch Deployment: Internet-Facing Servers** | Apply June 2026 cumulative update to all internet-facing Windows servers (IIS, RDP gateways, VPN concentrators, load balancer backends). Prioritize based on public IP exposure. | Cloud Platform Eng / Windows Sysadmin | 2026-06-16 | Priority |
| **M5 — Emergency Patch Deployment: Domain Controllers** | Apply June 2026 cumulative update to all Windows domain controllers. DCs are primary lateral movement targets for wormable exploits. Coordinate maintenance window to minimize AD replication disruption. | Windows Infrastructure | 2026-06-17 | Priority |
| **M6 — Patch Deployment: Azure IaaS Windows VMs** | Deploy June 2026 update via Azure Update Manager to all Windows Server VMs across all subscriptions. Generate compliance report from Azure Policy confirming 0 non-compliant VMs. | Cloud Platform Engineering | 2026-06-17 | Priority |
| **M7 — Patch Deployment: AWS EC2 Windows Instances** | Deploy via AWS Systems Manager Patch Manager. Run `AWS-RunPatchBaseline` SSM document targeting all Windows EC2 instances. Generate compliance report confirming 0 non-compliant instances. | Cloud Platform Engineering | 2026-06-17 | Priority |
| **M8 — Patch Deployment: Remaining Windows Estate** | Roll June 2026 update to all remaining workstations and servers via Intune/WSUS. Non-compliant devices go into conditional access quarantine until updated. | Endpoint Engineering | 2026-06-18 | Target |
| **M9 — Post-Patch Vulnerability Scan** | Run authenticated scan across 100% Windows estate confirming CVE-2026-45657 and CVE-2026-47291 are no longer detected. Generate compliance report for CISO sign-off. | Vulnerability Management | 2026-06-20 | Pending |
| **M10 — Remove HTTP.sys Workaround** | Remove registry workaround setting (MaxRequestBytes) from systems where June 2026 update has been confirmed installed. Registry value is no longer needed post-patch and should not be left as a permanent configuration. | Windows Sysadmin | 2026-06-20 | Pending |
| **M11 — CMDB Update** | Update CMDB with June 2026 patch level for all systems. Document emergency change record. | IT Asset Management | 2026-06-22 | Pending |
| **M12 — Hyper-V CVE Verification** | For Azure-hosted Windows VMs: confirm Microsoft's platform update for Hyper-V CVEs (CVE-2026-47652, CVE-2026-45641, CVE-2026-45607) has been applied via Azure Service Health. For on-premises Hyper-V hosts: apply June 2026 Server update to Hyper-V host OS. | Cloud Platform Eng / Windows Infrastructure | 2026-06-22 | Pending |

---

## Compensating Controls (Parallel with Patch Deployment)

| Control | CVE Addressed | Duration |
|---|---|---|
| MaxRequestBytes registry setting ≤ 65,534 | CVE-2026-47291 | Until patch confirmed installed |
| Block SMB (TCP 445) between network segments via NSG/SG/Windows Firewall | CVE-2026-45657 (worm vector) | Permanent best-practice; retain after patch |
| Restrict RDP to VPN/bastion host only | CVE-2026-42985 (RDP RCE) | Permanent best-practice |
| EDR kernel telemetry enabled; June 2026 threat intelligence feeds updated | Both CVEs | Permanent |

---

## Escalation Criteria

| Trigger | Action |
|---|---|
| Public exploit / PoC released for CVE-2026-45657 before patch complete | Activate IR plan; isolate unpatched systems immediately; accelerate M5/M6/M7 to same-day |
| Evidence of exploitation in environment (EDR/SIEM alert) | IR plan activation; isolate affected segment; forensic investigation; brief CISO within 1 hour |
| Ransomware deployment detected | BCP/DR activation; isolate; contact cyber insurance carrier; SEC materiality assessment |

---

## Success Metrics

| Metric | Target |
|---|---|
| Internet-facing server patch completion | 100% by June 16 |
| Azure/AWS cloud VM patch completion | 100% by June 17 |
| Full Windows estate patch completion | 100% by June 18 |
| Post-patch scan clear rate | 0 systems showing CVE-2026-45657 or CVE-2026-47291 |
| HTTP.sys workaround deployed (pre-patch) | 100% of HTTP.sys-exposed servers by June 15 EOD |

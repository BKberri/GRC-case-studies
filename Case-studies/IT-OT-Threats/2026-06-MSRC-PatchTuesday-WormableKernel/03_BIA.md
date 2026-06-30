# Business Impact Analysis (BIA)
## Case: CVE-2026-45657 / CVE-2026-47291 — Microsoft June 2026 Patch Tuesday: Wormable Kernel & HTTP.sys RCE
**Date:** 2026-06-15 | **Analyst:** Blaise Kingko

---

## 1. Executive Summary

Microsoft's June 2026 Patch Tuesday delivered the largest update release in the history of the Patch Tuesday program (198–208 CVEs), anchored by two CVSS 9.8 unauthenticated RCEs with no user interaction required. CVE-2026-45657 is a wormable Windows Kernel flaw — security researchers explicitly compare it to EternalBlue (MS17-010), the exploit that enabled WannaCry and NotPetya to cause an estimated $10 billion in global damages in 2017. CVE-2026-47291 is a separate HTTP.sys network stack overflow that allows complete web server takeover by sending a single malicious packet.

For any organization operating Windows infrastructure — on-premises or in cloud — this is an emergency-tier patching event, not a routine Patch Tuesday.

---

## 2. Scope of Affected Systems

| Environment | Exposure |
|---|---|
| On-premises Windows workstations and servers | All unpatched Windows 10/11 and Server 2019/2022/2025 |
| Azure IaaS (Windows Server VMs) | All unpatched Windows guest OSes |
| AWS EC2 Windows instances | All unpatched Windows AMIs |
| Hybrid domain-joined environments | Full estate — wormable propagation can traverse VPN/ExpressRoute/Direct Connect links |
| IIS web servers (any cloud or on-prem) | CVE-2026-47291: All HTTP.sys-exposed hosts |
| Azure Hyper-V (customer VMs) | VM guest escape risk (CVE-2026-47652 family) |

---

## 3. Business Process Impact Scenarios

### Scenario A — Ransomware via Wormable Kernel Exploit (Highest Concern)
- **Mechanism:** Threat actor acquires or develops working exploit for CVE-2026-45657; deploys ransomware payload that self-replicates via worm across all unpatched Windows systems simultaneously
- **Precedent:** WannaCry (2017) using EternalBlue traversed 230,000 systems in 150 countries in < 24 hours; NotPetya caused $10B in damages
- **Business Impact:** Total Windows estate lockdown; production systems, file servers, domain controllers potentially unavailable; BCP/DR activation required
- **RTO/RPO Impact:** RTO extended to days–weeks; RPO at last clean backup (pre-infection)
- **Financial Impact:** $10M–$1B+ depending on organization size and estate coverage

### Scenario B — Web Server Compromise via HTTP.sys (CVE-2026-47291)
- **Mechanism:** Attacker sends malformed HTTP request to internet-facing IIS server; achieves SYSTEM-level access; pivots into cloud environment from DMZ
- **Business Impact:** Web application compromise; customer data at risk; initial access for broader cloud-environment breach
- **Financial Impact:** $2M–$20M (breach notification, remediation, reputational damage)

### Scenario C — VM Guest Escape via Hyper-V CVEs
- **Mechanism:** Attacker compromising a Windows VM uses Hyper-V escape vulnerability to break out to hypervisor host; gains access to all other VMs on the same physical host
- **Business Impact:** Multi-tenant environment breach; all VMs on affected host compromised; cloud isolation boundary failure
- **Financial Impact:** $5M–$50M depending on data residency on affected VMs

---

## 4. Financial Exposure Estimate

| Scenario | Low Estimate | High Estimate |
|---|---|---|
| Ransomware via wormable exploit | $10M | $500M+ |
| Web server breach via HTTP.sys | $2M | $20M |
| Hyper-V guest escape | $5M | $50M |
| **Emergency patching labor cost (opportunity cost)** | $500K | $5M |

---

## 5. Regulatory Exposure

| Regulation | Trigger | Impact |
|---|---|---|
| SEC 4-day material incident disclosure | Ransomware / breach constituting material impact | Must assess materiality within hours |
| SOX Section 302/404 | Ransomware disrupting financial reporting controls | Material weakness in ICFR possible |
| NYDFS Part 500 | Any cybersecurity event at covered entity | 72-hour notification obligation |
| HIPAA Breach Notification | PHI exposure in ransomware/breach scenario | 60-day notification to HHS OCR; media notification if > 500 in a state |
| BOD 26-04 (Federal agencies) | Both CVEs qualify as Tier 1 under new risk-based directive | Must remediate ahead of standard cadence |

---

## 6. RTO / RPO Considerations

| System | Normal RTO | Post-Ransomware RTO | Risk Driver |
|---|---|---|---|
| Domain Controllers | 4 hours | 24–72 hours | Worm propagation priority target |
| Core Business Applications | 4–8 hours | 3–14 days | Application servers typically Windows |
| Web-facing services | 1 hour | 2–5 days | HTTP.sys RCE → web tier compromise |
| Cloud IaaS environment | 2 hours | 1–7 days | VM propagation across VNet |

---

## 7. Continuity Recommendations

1. Activate emergency change control immediately for June 2026 cumulative update deployment
2. Implement network micro-segmentation to contain potential worm propagation in parallel with patching
3. Verify backup integrity and test restore procedures NOW — before any exploitation occurs
4. Ensure offline / immutable backups are in place for critical systems
5. Brief BC/DR teams on wormable threat scenario and confirm IR playbook is current

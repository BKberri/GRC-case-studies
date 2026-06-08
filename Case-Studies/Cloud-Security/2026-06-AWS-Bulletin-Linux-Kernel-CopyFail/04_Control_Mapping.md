# Control Mapping Matrix
## Case: AWS Bulletin 2026-030 — Copy.fail / DirtyFrag Linux Kernel LPE Family

| Framework | Reference | Control Title | Application to This Case |
|---|---|---|---|
| NIST CSF 2.0 | PR.PS-02 | Software is maintained, replaced, and removed commensurate with risk | Drives the kernel/AMI patch-and-replace cadence for EKS/ECS/EC2 fleets |
| NIST CSF 2.0 | DE.CM-09 | Computing hardware/software and runtime environments are monitored to find anomalous activity | Supports detection of exploitation attempts against unpatched kernels |
| NIST 800-53 Rev 5 | SI-2 (Flaw Remediation) | Identify, report, and correct system flaws | Core control for tracking and closing the kernel LPE family |
| NIST 800-53 Rev 5 | CM-2 (Baseline Configuration) | Maintain current baseline configurations | Ensures patched AMI/kernel versions become the enforced baseline |
| NIST 800-53 Rev 5 | CM-6 (Configuration Settings) | Establish and enforce configuration settings | Enforces minimum kernel version via IaC/AMI pipelines |
| NIST 800-53 Rev 5 | RA-5 (Vulnerability Monitoring and Scanning) | Scan for vulnerabilities and remediate | CSPM scan validates patch convergence across accounts |
| ISO 27001:2022 Annex A | A.8.8 | Management of Technical Vulnerabilities | Governs the vulnerability-to-remediation lifecycle for this CVE family |
| ISO 27001:2022 Annex A | A.8.9 | Configuration Management | Ensures patched configuration is the documented standard |
| ISO 27001:2022 Annex A | A.5.30 | ICT Readiness for Business Continuity | Supports node-replacement runbook readiness |
| CIS Controls v8 | Control 7 / Safeguard 7.4 | Perform Automated Application Patch Management | Primary remediation safeguard — automated AMI/node rotation |
| CIS Controls v8 | Control 4 | Secure Configuration of Enterprise Assets and Software | Baseline hardening of container hosts |
| CIS Controls v8 | Control 1 / Safeguard 1.1 | Establish and Maintain Detailed Enterprise Asset Inventory | Required precursor — must know which nodes/AMIs are affected |

### Mapping Notes
- This case sits squarely in the **shared-responsibility seam**: AWS owns control-plane patching; the customer owns node/AMI rotation. Control mapping should explicitly assign SI-2 and CM-6 ownership to the cloud platform team, with GRC providing independent verification via RA-5 scan evidence.
- Recommend adding this CVE family to the next quarterly vulnerability-management control test as a sample item for SI-2 effectiveness evidence (SOC 2 / ISO 27001 surveillance audit prep).

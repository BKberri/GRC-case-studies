# [INCIDENT TITLE] — Cloud Security Case Study
> **Example title format:** `AWS IAM Confused Deputy Attack — Cross-Account Privilege Escalation Risk Analysis`

---

## Case Study Metadata

| Field | Details |
|---|---|
| **Case Study ID** | CS-CLOUD-[YYYY-MM-###] |
| **Date Published** | [YYYY-MM-DD] |
| **Incident Date** | [YYYY-MM-DD or Month YYYY] |
| **Author** | Blaise Kingko |
| **Threat Category** | Cloud — [IAM / Storage / Network / Compute / Serverless / Container / CI-CD] |
| **CVE / Advisory ID** | [CVE-XXXX-XXXXX or Cloud Provider Bulletin ID] |
| **CVSS Score** | [X.X — Critical / High / Medium] |
| **Affected Provider** | [AWS / Azure / GCP / Multi-cloud] |
| **Affected Service** | [e.g., AWS IAM, Azure AD, S3, Kubernetes] |
| **Intelligence Source** | [AWS Security Bulletin / Azure MSRC / CISA KEV / NIST NVD] |
| **Exploitation Status** | [Actively exploited / PoC available / No known exploit] |

---

## 1. Incident Summary

### 1.1 What Happened
*2–3 sentences. State the facts: what cloud service, what misconfiguration or vulnerability, what the attacker achieved or could achieve. Write for a non-technical reader.*

[Insert plain-language summary here]

### 1.2 Why It Matters
*1–2 sentences connecting to business risk. Cloud incidents carry unique risks — data sovereignty, shared responsibility model failures, blast radius across accounts.*

[Insert business impact framing here]

### 1.3 Affected Cloud Scope
- **Cloud Provider:** [AWS / Azure / GCP / Multi-cloud]
- **Affected Services:** [List specific cloud services]
- **Account Scope:** [Single account / Multi-account / Organization-wide]
- **Data Classification:** [Public / Internal / Confidential / Restricted]
- **Regulatory Exposure:** [SOC 2 / FedRAMP / HIPAA / GDPR / PCI-DSS]

---

## 2. Technical Analysis

### 2.1 Vulnerability / Misconfiguration Details

| Field | Details |
|---|---|
| **Issue Type** | [Vulnerability / Misconfiguration / Design Flaw / Supply Chain] |
| **Attack Vector** | [Network / Adjacent / API / Identity] |
| **Attack Complexity** | [Low / Medium / High] |
| **Privileges Required** | [None / Low / High] |
| **Authentication Required** | [Yes / No] |
| **Blast Radius** | [Single resource / Account / Organization] |
| **Data at Risk** | [Type and sensitivity of data exposed] |

### 2.2 Attack Chain
*Walk through the attack step by step. Reference MITRE ATT&CK for Cloud technique IDs (TA0010 Exfiltration, T1537 Transfer Data to Cloud Account, etc.)*

1. **Initial Access** — [How attacker enters the cloud environment — ATT&CK T####]
2. **Discovery** — [How attacker maps the environment — ATT&CK T####]
3. **Privilege Escalation** — [How attacker escalates — ATT&CK T####]
4. **Lateral Movement** — [Cross-account or cross-service movement — ATT&CK T####]
5. **Collection / Exfiltration** — [What data or access is obtained — ATT&CK T####]
6. **Impact** — [Ultimate attacker objective — ATT&CK T####]

### 2.3 Shared Responsibility Model Analysis
*This section is specific to cloud case studies. Define where the failure sits in the shared responsibility model.*

| Responsibility Layer | Owner | Status |
|---|---|---|
| Physical infrastructure | Cloud Provider | ✅ Provider responsibility |
| Hypervisor / Platform | Cloud Provider | ✅ Provider responsibility |
| Operating System | [Customer / Provider] | [Who owns this and what failed] |
| Application | Customer | [What customer-side failure occurred] |
| **Identity & Access** | **Customer** | **[IAM configuration gap — most common failure point]** |
| **Data Classification** | **Customer** | **[Data protection gap]** |
| **Network Controls** | **Customer** | **[Network configuration gap]** |

### 2.4 IAM Analysis
*Complete this section for any incident involving identity, access, or privilege.*

- **Over-privileged roles or policies:** [Yes / No — describe]
- **Cross-account trust issues:** [Yes / No — describe]
- **Wildcard permissions present:** [Yes / No — describe]
- **Service account misuse:** [Yes / No — describe]
- **Lack of SCPs or permission boundaries:** [Yes / No — describe]
- **MFA enforcement:** [Yes / No — describe]

### 2.5 Root Cause
*What is the underlying architectural or process failure?*

[Insert root cause — be specific. "Misconfiguration" is not a root cause. "Lack of least-privilege enforcement at the organization SCP level across 500+ accounts" is a root cause.]

---

## 3. Framework Impact Analysis

### 3.1 NIST CSF 2.0 Mapping

| CSF Function | Subcategory | Gap or Finding |
|---|---|---|
| **GOVERN** | [e.g., GV.RM-02] | [Governance gap — e.g., no cloud security policy covering IAM standards] |
| **IDENTIFY** | [e.g., ID.AM-03] | [Asset management gap — e.g., unmanaged cloud accounts] |
| **PROTECT** | [e.g., PR.AA-05] | [Access control gap] |
| **DETECT** | [e.g., DE.CM-03] | [Detection gap — e.g., no anomalous IAM activity alerting] |
| **RESPOND** | [e.g., RS.MI-01] | [Response gap] |
| **RECOVER** | [e.g., RC.RP-02] | [Recovery gap] |

### 3.2 NIST SP 800-53 Control Mapping

| Control Family | Control ID | Control Name | Finding |
|---|---|---|---|
| Access Control | AC-2 | Account Management | [Finding] |
| Access Control | AC-3 | Access Enforcement | [Finding] |
| Access Control | AC-6 | Least Privilege | [Finding] |
| Audit & Accountability | AU-12 | Audit Record Generation | [Finding] |
| Configuration Mgmt | CM-7 | Least Functionality | [Finding] |
| Identification & Auth | IA-5 | Authenticator Management | [Finding] |
| System Integrity | SI-7 | Software Integrity | [Finding] |

### 3.3 ISO 27001:2022 Mapping

| Annex A Clause | Control | Finding |
|---|---|---|
| A.5.15 | Access control | [Finding] |
| A.5.18 | Access rights | [Finding] |
| A.8.3 | Information access restriction | [Finding] |
| A.8.5 | Secure authentication | [Finding] |
| A.8.9 | Configuration management | [Finding] |
| [Add others] | [Control] | [Finding] |

### 3.4 CIS Controls v8 Mapping

| CIS Control | Safeguard | Finding / Remediation |
|---|---|---|
| Control 1 | Inventory of Enterprise Assets | [Finding] |
| Control 3 | Data Protection | [Finding] |
| Control 5 | Account Management | [Finding] |
| Control 6 | Access Control Management | [Finding] |
| Control 8 | Audit Log Management | [Finding] |

### 3.5 Cloud Security Framework Mapping
*Additional cloud-specific framework references:*

| Framework | Reference | Finding |
|---|---|---|
| AWS Well-Architected — Security Pillar | [SEC-X] | [Finding] |
| CIS AWS Benchmark | [Control X.X] | [Finding] |
| CSA Cloud Controls Matrix | [Domain] | [Finding] |
| FedRAMP (if applicable) | [Control] | [Finding] |

---

## 4. Risk Assessment

### 4.1 Risk Scoring

| Dimension | Score | Rationale |
|---|---|---|
| **Likelihood** | [1–5] | [Exploitation status, attacker capability, how common this misconfiguration is] |
| **Impact** | [1–5] | [Blast radius, data sensitivity, regulatory exposure, revenue impact] |
| **Risk Score** | [L × I] | [Calculated] |
| **Risk Rating** | [Critical / High / Medium / Low] | [20-25=Critical, 10-19=High, 5-9=Medium, 1-4=Low] |

### 4.2 Inherent vs Residual Risk

| Risk State | Rating | Notes |
|---|---|---|
| **Inherent Risk** | [Without controls] | [Risk without any cloud security controls] |
| **Residual Risk** | [With current controls] | [Risk with existing IAM/CSPM/logging in place] |
| **Target Residual Risk** | [After remediation] | [Acceptable risk after full remediation] |

### 4.3 Cloud-Specific Risk Amplifiers
- [ ] Multi-account blast radius — single misconfiguration affects organization-wide
- [ ] Publicly exposed storage bucket or API endpoint
- [ ] No CSPM coverage detecting the misconfiguration
- [ ] CloudTrail / audit logging disabled or incomplete
- [ ] No SCP guardrails at the organization level
- [ ] Overly permissive cross-account trust relationships
- [ ] Secrets or credentials stored in code or environment variables
- [ ] No network segmentation — VPC peering with excessive access

---

## 5. Risk Model Implications

### 5.1 How This Challenges Traditional Risk Models
*The cloud shared responsibility model fundamentally changes where security accountability sits. Explain how this incident exposes gaps in how organizations model cloud risk.*

[Insert analysis — 2–4 paragraphs. Reference the shared responsibility model, CSPM limitations, identity-first security, and how traditional perimeter-based risk models fail in cloud.]

### 5.2 Where Traditional Controls Break Down

- **[Control assumption 1]:** [Why it fails in cloud — e.g., "Network perimeter controls don't protect against IAM-based lateral movement"]
- **[Control assumption 2]:** [Why it fails]
- **[Control assumption 3]:** [Why it fails]

### 5.3 Emerging Risk Pattern
*Connect this incident to the broader cloud threat landscape.*

[Insert pattern — e.g., identity as the new perimeter, increasing targeting of CI/CD pipelines, shadow IT creating unmanaged cloud exposure]

---

## 6. Recommended Controls & Remediation

### 6.1 Immediate Actions (0–7 Days)

| Action | Owner | Framework Reference | Priority |
|---|---|---|---|
| [Specific action — e.g., Audit all cross-account IAM roles and enforce ExternalId] | Cloud Security Team | NIST 800-53: AC-6 \| CIS Control 5.4 | 🔴 Critical |
| [Rotate any exposed credentials immediately] | IAM / DevSecOps | NIST 800-53: IA-5 | 🔴 Critical |
| [Enable CloudTrail across all accounts if not active] | Cloud Security | NIST 800-53: AU-12 | 🔴 Critical |

### 6.2 Short-Term Actions (8–30 Days)

| Action | Owner | Framework Reference | Priority |
|---|---|---|---|
| [Implement SCPs to enforce least-privilege at org level] | Cloud Architecture | NIST 800-53: AC-6 \| CSF: PR.AA-05 | 🟠 High |
| [Deploy CSPM tooling to detect similar misconfigs] | Cloud Security | NIST CSF: DE.CM | 🟠 High |

### 6.3 Strategic Recommendations

| Recommendation | Framework Reference | Business Rationale |
|---|---|---|
| [Implement Zero Trust architecture for cloud access] | NIST 800-207 \| CSF: PR.AA | [Business rationale] |
| [Establish Compliance-as-Code pipeline for IAM policies] | NIST 800-53: CM-2 \| CIS Control 4 | [Business rationale] |

### 6.4 Cloud-Specific Architectural Controls
- **SCPs (Service Control Policies):** Enforce organization-wide guardrails — deny actions no account should ever perform regardless of IAM permissions
- **Permission Boundaries:** Limit maximum permissions any IAM entity can grant — prevents privilege escalation through policy creation
- **CSPM:** Continuous posture monitoring to detect drift from security baseline in real time
- **Just-In-Time Access:** Eliminate standing privileges — grant elevated access only when needed and for limited duration
- **Immutable Audit Logs:** CloudTrail with log file validation enabled, stored in separate locked account

---

## 7. Executive Summary

*Write last. Maximum one page. Plain English. Board-level reader.*

### The Situation
[What happened in the cloud environment and what access or data was at risk]

### The Business Risk
[Revenue, regulatory, reputational exposure — specific to your industry and data classification]

### What We Are Doing
[Immediate and near-term actions — specific, not vague]

### What We Need From Leadership
[Resource, budget, policy decisions required]

---

## 8. References & Sources

| Source | URL | Date Accessed |
|---|---|---|
| AWS Security Bulletin | [URL] | [Date] |
| NIST NVD | https://nvd.nist.gov/vuln/detail/[CVE-ID] | [Date] |
| MITRE ATT&CK Cloud | https://attack.mitre.org/matrices/enterprise/cloud/ | [Date] |
| CIS AWS Benchmark | https://www.cisecurity.org/benchmark/amazon_web_services | [Date] |
| [Additional source] | [URL] | [Date] |

---

## 9. Revision History

| Version | Date | Author | Changes |
|---|---|---|---|
| 1.0 | [YYYY-MM-DD] | Blaise Kingko | Initial publication |

---

*Case Study Template v1.0 — Blaise Kingko GRC Intelligence Program*
*Framework References: NIST CSF 2.0 | NIST SP 800-53 Rev 5 | ISO 27001:2022 | CIS Controls v8 | AWS Well-Architected*

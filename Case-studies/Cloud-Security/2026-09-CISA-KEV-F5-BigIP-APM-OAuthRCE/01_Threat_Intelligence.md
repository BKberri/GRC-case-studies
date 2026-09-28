# F5 BIG-IP APM OAuth Authorization Server Heap Overflow — Unauthenticated RCE on the Identity Chokepoint

## Case Study Metadata

| Field | Details |
|---|---|
| **Case Study ID** | CS-CLOUD-2026-09-002 |
| **Date Published** | 2026-09-28 |
| **Incident / Disclosure Date** | 2026-09-22 (CISA KEV addition) |
| **Author** | Blaise Kingko |
| **Threat Category** | Cloud — IAM / Identity-Aware Access Proxy (OAuth Authorization Server) |
| **CVE / Advisory ID** | CVE-2026-94127 |
| **CVSS Score** | 9.3 Critical (CVSS 4.0, CVSS-B) |
| **Affected Provider** | On-prem / hybrid / multi-cloud (F5 BIG-IP APM ships as a physical appliance, a virtual edition, and as marketplace images on AWS, Azure, and GCP) |
| **Affected Service** | F5 BIG-IP Access Policy Manager (APM), specifically instances configured as an OAuth Authorization Server |
| **Intelligence Source** | CISA Known Exploited Vulnerabilities (KEV) Catalog |
| **Exploitation Status** | Actively exploited (KEV-confirmed) |
| **Related Risk Register Entry** | RR-082 |

---

## 1. Incident Summary

### 1.1 What Happened

CISA added CVE-2026-94127 to the KEV catalog on 2026-09-22 with a three-day remediation deadline of 2026-09-25. The vulnerability is a heap-based buffer overflow (CWE-122) in F5 BIG-IP's Access Policy Manager module, present when a BIG-IP APM access policy and an OAuth profile are configured on a virtual server and that APM instance is acting as an OAuth Authorization Server. F5's own advisory is direct about the impact: an unauthenticated attacker can achieve remote code execution. No credentials, no session, no user interaction. The flaw sits in the data plane, meaning it is reachable through ordinary application traffic rather than a management interface, and BIG-IP systems running in Appliance mode, F5's hardened configuration intended to reduce attack surface, are vulnerable too.

CVSS 4.0 scores the base severity at 9.3, Critical, under the vector AV:N/AC:L/AT:N/PR:N/UI:N/VC:H/VI:H/VA:H/SC:N/SI:N/SA:N. Read plainly: network-reachable, low attack complexity, no attack requirements beyond reaching the service, no privileges, no user interaction, and high impact to confidentiality, integrity, and availability of the vulnerable system itself. This is about as close to worst-case as a CVSS 4.0 score gets for a device that most organizations have placed directly in the authentication path for their application portfolio.

Affected versions, all specific to the BIG-IP APM module, are 21.1.0 before Hotfix-BIGIP-21.1.0.2.0.30.22-ENG, 17.5.0 before Hotfix-BIGIP-17.5.1.9.0.160.12-ENG, and 17.1.0 before Hotfix-BIGIP-17.1.3.5.0.41.14-ENG. F5's vendor advisory (K000162605) is the authoritative source for exact build numbers and hotfix availability. Software versions that have reached End of Technical Support are explicitly not evaluated by F5, which means organizations running EoTS BIG-IP builds have no vendor confirmation either way and should treat that gap as its own finding.

### 1.2 Why It Matters

BIG-IP APM is not a peripheral component. It is F5's identity-aware proxy: the access-control and SSO gateway that many enterprises put in front of VPN access, internal applications, and OAuth-based service access. When an attacker gets unauthenticated code execution on the box that decides who gets into everything else, the blast radius is not the device, it is every application, session, and credential flow that device mediates. This case sits squarely in the category this program treats as top priority: identity and access-proxy infrastructure, where a single vulnerability collapses the distinction between "perimeter breach" and "identity compromise."

The KEV listing itself is the second reason this matters right now. CISA's inclusion criteria require confirmed evidence of active exploitation in the wild, not theoretical risk. This is not a "patch when convenient" advisory. It is a live exploitation event against a device class that sits at the center of enterprise authentication architecture.

### 1.3 Affected Cloud Scope

- **Cloud Provider:** On-premises, hybrid, and multi-cloud. BIG-IP APM runs as a physical appliance, a virtual edition on VMware/KVM/Hyper-V, and as a marketplace image on AWS, Azure, and GCP. Cloud-hosted deployments do not receive automatic patching from the provider; the customer manages the guest OS and application stack in every one of these deployment models.
- **Affected Services:** BIG-IP APM instances with an OAuth profile and an APM access policy attached to a virtual server, where that instance is configured as an OAuth Authorization Server. Instances used strictly as an OAuth Client or Resource Server, with no authorization server profile configured, are explicitly not affected per F5's advisory.
- **Account Scope:** Every downstream application, SSO relying party, and API that trusts tokens issued by an affected APM instance inherits the exposure. In practice this often spans multiple business units and, where the same APM tier fronts multi-tenant or multi-subsidiary access, multiple cloud accounts and identity domains.
- **Data Classification:** OAuth tokens, session cookies, SSO credentials, and any data reachable through the applications the APM instance authenticates users into. Given APM's role as an access gateway, the realistic data-at-risk category extends well beyond the device itself to whatever the authenticated session grants access to.
- **Regulatory Exposure:** For organizations subject to SOX, PCI DSS, HIPAA, GLBA, or similar regimes, an unauthenticated RCE on the identity and access control layer touches control objectives around access management, authentication, and audit trail integrity directly. For federal agencies and contractors, CISA's Binding Operational Directive 22-01 makes the KEV due date a compliance deadline in its own right, and that date has already passed as of this report's publication.

---

## 2. Technical Analysis

### 2.1 Vulnerability / Misconfiguration Details

| Field | Details |
|---|---|
| **Issue Type** | Heap-based buffer overflow (CWE-122) in BIG-IP APM's data-plane OAuth request handling |
| **Attack Vector** | Network (AV:N) — reachable through the virtual server's data-plane listener |
| **Attack Complexity** | Low (AC:L) — no race conditions, timing windows, or environment-specific setup required |
| **Privileges Required** | None (PR:N) |
| **Authentication Required** | None — unauthenticated, pre-auth exploitation |
| **Blast Radius** | The BIG-IP device itself, plus every application and identity flow that relies on it as an OAuth Authorization Server; control-plane management functions are not directly exposed by this specific flaw |
| **Data at Risk** | OAuth tokens and session state in transit through the affected virtual server; downstream application data reachable via forged or replayed authentication |

### 2.2 Attack Chain

1. **Initial Access** — An attacker sends specially crafted OAuth-flow HTTP requests to a BIG-IP virtual server where APM is configured as an OAuth Authorization Server. No credentials, prior session, or user interaction are required; the malformed request itself is the entire access mechanism.
2. **Discovery** — BIG-IP APM instances are externally fingerprintable through characteristic login paths, TLS certificate patterns, and HTTP response headers, which lets an attacker identify likely-vulnerable targets before ever sending exploit traffic.
3. **Exploitation** — The malformed OAuth request triggers the heap-based buffer overflow in the data-plane (TMM) process that parses OAuth protocol traffic. Because this is memory corruption in the traffic-handling process itself, successful exploitation delivers code execution directly; there is no separate privilege-escalation step because initial access already equals code execution at the process level.
4. **Lateral Movement** — Code execution on the device that issues and validates OAuth tokens for the application portfolio gives an attacker the position to intercept, forge, or replay authentication tokens and session cookies for every application behind that instance, or to pivot from the device into whichever network segment it bridges.
5. **Collection / Exfiltration** — From that position, an attacker can harvest live OAuth tokens and SSO session material in transit, stage further internal reconnaissance, or establish a persistent foothold on infrastructure that most monitoring stacks treat as trusted network plumbing rather than an endpoint to watch.
6. **Impact** — Full compromise of the organization's access-control chokepoint: unauthenticated RCE on the device deciding who authenticates into what, with the realistic potential for mass credential and session theft and unauthorized access to every backend service that trusts that APM instance.

### 2.3 Shared Responsibility Model Analysis

| Responsibility Layer | Owner | Status |
|---|---|---|
| Physical infrastructure | Cloud Provider (cloud-hosted deployments only) | ✅ Provider responsibility where applicable |
| Hypervisor / Platform | Cloud Provider (cloud-hosted deployments only) | ✅ Provider responsibility where applicable |
| Operating System (BIG-IP TMOS firmware) | Customer | ⚠️ Customer responsibility — this is the layer the vulnerability lives in, and the customer owns the patch cycle regardless of deployment model |
| Application (APM access policy, OAuth profile configuration) | Customer | ⚠️ Customer responsibility |
| **Identity & Access** | **Customer** | ⚠️ Customer owns the OAuth Authorization Server configuration decision that determines exposure |
| **Data Classification** | **Customer** | ⚠️ Customer responsibility |
| **Network Controls** | **Customer** | ⚠️ Customer owns whether the affected virtual server is internet-facing, internally exposed, or segmented |

This is not a case where a cloud provider's shared responsibility boundary absorbs part of the fix. Whether BIG-IP APM runs as a physical appliance, a virtual edition, or a marketplace image, it is self-managed infrastructure: the customer patches the firmware, owns the access policy configuration that determines whether OAuth Authorization Server functionality is even enabled, and controls the network exposure of the affected virtual server. A cloud marketplace deployment shifts physical and hypervisor responsibility to the provider; it does nothing to shift responsibility for the vulnerable software running inside the instance.

### 2.4 IAM Analysis

- **Over-privileged roles or policies:** The direct analog here is not cloud IAM roles but APM access policies and OAuth scopes. Any OAuth Authorization Server profile issuing broader scopes than a given client or relying-party application actually needs increases the value of a compromised token to an attacker who has already achieved code execution on the issuing device.
- **Cross-account trust issues:** Where a single APM instance federates SSO or OAuth trust across multiple business units, subsidiaries, or cloud accounts, the blast radius of this vulnerability crosses every one of those trust boundaries simultaneously. Organizations should map exactly which downstream relying parties trust each affected instance before scoping incident response.
- **Wildcard permissions present:** Review OAuth scope definitions issued by each Authorization Server profile for overly broad grants (for example, scopes that grant blanket API access rather than resource-specific access), since this vulnerability makes the token-issuing point itself the attack target.
- **Service account misuse:** Machine-to-machine OAuth flows (client credentials grants, service account tokens) issued by an affected instance should be inventoried; these often carry longer-lived or higher-privilege tokens than interactive user sessions and represent a disproportionate share of the risk if the issuing server is compromised.
- **Lack of SCPs or permission boundaries:** BIG-IP has no direct SCP equivalent, but the operative control is virtual-server-level network ACLs and access policy scoping. Instances lacking IP allow-listing or WAF-layer request filtering in front of the OAuth endpoint have no compensating control between the internet and the vulnerable code path.
- **MFA enforcement:** MFA enforced further up the authentication chain does not mitigate this vulnerability. Because the flaw is pre-authentication (PR:N, UI:N in the CVSS vector), the exploit triggers before the access policy, and therefore before any MFA check, is ever evaluated. MFA posture is not a relevant compensating control for this specific finding.

**Scoping nuance, and why it matters for triage:** F5's advisory is explicit that this vulnerability is present only when BIG-IP APM is configured as an OAuth Authorization Server. Deployments using APM strictly as an OAuth Client or Resource Server, with no authorization server profile configured, are not affected. In practice, most organizations running BIG-IP APM use it for a mix of purposes: VPN access, SSO for internal web applications, and, in a smaller subset of cases, as the actual OAuth Authorization Server issuing tokens for API access. Treating every BIG-IP APM instance in the estate as equally exposed will both overstate the emergency-patch scope in places that are not affected and, worse, risk under-prioritizing the instances that genuinely are. The first remediation step is not patching, it is inventory: enumerate every BIG-IP APM instance, determine which ones have an OAuth Authorization Server profile actually configured and attached to a virtual server, and scope the emergency response to that confirmed set before assuming org-wide exposure.

### 2.5 Root Cause

The root cause is insufficient bounds checking on attacker-supplied data during data-plane (TMM) parsing of OAuth protocol requests, when the receiving BIG-IP APM instance is configured as an OAuth Authorization Server. Untrusted input from the OAuth request is written into a heap-allocated buffer without adequate size validation, corrupting adjacent heap memory (CWE-122) in a way that an attacker can shape into arbitrary code execution. Because the vulnerable code path is in the traffic-handling process itself rather than a management-plane component, the flaw is reachable by anyone who can send traffic to the virtual server, which is precisely what makes it pre-authentication and network-exploitable.

---

## References

| Source | URL |
|---|---|
| CISA KEV Catalog addition (2026-09-22) | https://www.cisa.gov/news-events/alerts/2026/09/22/cisa-adds-four-known-exploited-vulnerabilities-catalog |
| NVD — CVE-2026-94127 | https://nvd.nist.gov/vuln/detail/CVE-2026-94127 |
| F5 Vendor Advisory K000162605 | https://my.f5.com/manage/s/article/K000162605 |
| CISA Known Exploited Vulnerabilities Catalog | https://www.cisa.gov/known-exploited-vulnerabilities-catalog |

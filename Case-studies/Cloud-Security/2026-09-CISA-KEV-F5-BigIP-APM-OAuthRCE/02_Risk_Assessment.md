# Risk Assessment — F5 BIG-IP APM OAuth Authorization Server RCE (CVE-2026-94127)

**Case Study ID:** CS-CLOUD-2026-09-002 | **Risk Register Entry:** RR-082 | **Date:** 2026-09-28

---

## 4. Risk Assessment

### 4.1 Risk Scoring

| Dimension | Score | Rationale |
|---|---|---|
| **Likelihood** | 5 | CISA's KEV addition confirms active exploitation in the wild, not a theoretical or PoC-only state. Combined with a pre-authentication, network-reachable attack vector requiring no privileges or user interaction, the population of internet-facing BIG-IP APM instances configured as OAuth Authorization Servers is an active target set today, not a future risk. |
| **Impact** | 5 | Unauthenticated remote code execution on the device that mediates authentication and access decisions for an organization's application portfolio. Compromise here is not contained to the device; it extends to every relying-party application, OAuth token, and SSO session that instance issues or validates. |
| **Risk Score** | 25 (5 × 5) | |
| **Risk Rating** | **Critical** | 20–25 = Critical per this program's scoring scale |

### 4.2 Inherent vs Residual Risk

| Risk State | Rating | Notes |
|---|---|---|
| **Inherent Risk** | Critical (25) | Unpatched BIG-IP APM instance configured as an OAuth Authorization Server, reachable from the network segment attackers can operate from, with no compensating controls between the request source and the vulnerable data-plane code path. |
| **Residual Risk** | High (15–20, deployment-dependent) | After the F5 hotfix is applied, the specific memory-corruption vector is closed, but residual risk stays elevated until organizations confirm patch deployment across the full BIG-IP estate, rotate credentials and tokens that transited any instance during the exposure window, and verify no exploitation occurred prior to patching. An organization that has patched but not yet completed exposure validation should carry this rating, not the target rating below. |
| **Target Residual Risk** | Low (4–9) | Achieved once: all in-scope instances are confirmed patched to a fixed hotfix build; OAuth Authorization Server exposure is inventoried and limited to instances that operationally require it; network access to affected virtual servers is restricted to expected client populations; and post-incident validation confirms no indicators of compromise during the exposure window. |

### 4.3 Cloud-Specific Risk Amplifiers

- [x] **Multi-account blast radius** — Where a single BIG-IP APM instance federates OAuth Authorization Server functionality across multiple business units, subsidiaries, or cloud accounts, compromise of that one instance cascades across every trust relationship it anchors simultaneously.
- [ ] Publicly exposed storage bucket or API endpoint — not applicable to this finding; the exposure vector is the BIG-IP virtual server itself, not a cloud-native storage or API construct.
- [x] **No CSPM coverage** — Cloud Security Posture Management tooling is built around cloud-native control plane misconfigurations (IAM policies, storage ACLs, security groups). It does not evaluate self-managed appliance firmware version or APM access policy configuration, which means this class of exposure sits in a monitoring gap between infrastructure security tooling and application-layer vulnerability management, even when the instance runs as a marketplace image inside a monitored cloud account.
- [ ] CloudTrail / audit logging disabled or incomplete — data-plane exploitation of this specific vulnerability does not depend on control-plane logging state; however, organizations should confirm BIG-IP's own request logging captured traffic to the affected virtual server during the exposure window to support forensic review.
- [ ] No SCP guardrails at org level — not the relevant control class for a self-managed network appliance; see network segmentation below instead.
- [x] **Overly permissive network exposure to the affected virtual server** — Internet-facing or broadly internally-reachable BIG-IP APM virtual servers with no IP allow-listing, WAF-layer filtering, or network segmentation in front of the OAuth endpoint remove the only practical compensating control available before a hotfix is applied.
- [ ] Secrets or credentials stored in code or environment variables — not the exposure mechanism for this vulnerability.
- [x] **No network segmentation** — Where the BIG-IP APM tier bridges directly into internal application segments without intermediate controls, post-exploitation lateral movement from a compromised instance has an unobstructed path into the environment it was meant to protect.

**Assessment note:** The standard cloud-native amplifier checklist assumes IaaS/PaaS control-plane misconfiguration as the primary risk driver. This finding sits outside that model: the amplifiers that matter most here are self-managed firmware patch currency, OAuth Authorization Server configuration scope, and network exposure of the affected virtual server, none of which a cloud provider's native security tooling evaluates by default. Section 5 of the full risk model (see 01_Threat_Intelligence.md, 2.3) addresses this gap directly.

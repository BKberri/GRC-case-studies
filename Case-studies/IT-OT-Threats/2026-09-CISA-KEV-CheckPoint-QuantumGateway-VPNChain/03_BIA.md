# Business Impact Analysis
## Check Point Quantum Security Gateway & Management Server Dual RCE (CVE-2026-85102 / CVE-2026-93616)

| Field | Details |
|---|---|
| **Case Study ID** | CS-ITOT-2026-09-002 |
| **Risk Register Reference** | RR-080 |
| **Report Period** | 2026-09-21 to 2026-09-28 |
| **Date** | 2026-09-28 |
| **Author** | Blaise Kingko |

---

## 1. Purpose and Scope
This business impact analysis evaluates the consequence of a confirmed or suspected compromise of Check Point Quantum Security Gateway (CVE-2026-85102) and Quantum/Multi-Domain Security Management Server (CVE-2026-93616) on the business processes that depend on them. It is a companion to 02_Risk_Assessment.md, which scores likelihood and technical impact, and to 06_POAM_Remediation.md, which tracks the remediation timeline. This document answers a different question: if these systems go down, get isolated for forensic containment, or are found compromised, what does that cost the organization operationally, and how fast does it need to come back.

## 2. Critical Business Process Dependency
Two distinct business functions depend on the affected technology, and they fail differently.

**Remote access continuity.** The Quantum Security Gateway is the VPN termination point for the organization's remote workforce, third-party vendor connections, and, in converged environments, remote engineering and vendor support access into OT networks. Loss or forced isolation of the gateway does not just degrade a convenience feature, it removes the sanctioned path for every remote user and every remote vendor who needs to reach internal systems, which in an OT context can include the only remote path a control system vendor has for emergency support.

**Policy and configuration control.** The Quantum/Multi-Domain Security Management Server is the control plane for every gateway it administers. It is not itself a data-path device, no user traffic flows through it, but every gateway's firewall rules, VPN configuration, and logging policy originate from it. A management server that is compromised, or one taken offline for containment, leaves every downstream gateway either running on stale policy or, in the compromise scenario, running on policy an attacker chose. Loss of the management server does not stop traffic from flowing through the gateways it administers, but it removes the organization's ability to trust or change what those gateways are doing.

These two dependencies are asymmetric. A gateway outage is a localized, visible failure: the remote workforce or a specific vendor connection stops working, and the business feels it immediately. A management server compromise is a silent, distributed failure: traffic keeps flowing through every gateway it administers, uninterrupted, while the organization has lost assurance over what those gateways are actually configured to do. The second failure mode is the one most business continuity plans are not written for, because nothing appears down.

## 3. Recovery Time and Recovery Point Framing (Qualitative)

**Recovery Time Objective (RTO).** For the gateway, the RTO target is measured in hours, not days, because the device sits on the direct path of the remote-access business process; every hour of gateway unavailability is an hour of lost remote connectivity for every dependent user and vendor. For the management server, the RTO target should be treated as equally urgent even though the operational symptom is less visible, because the organization's ability to trust and adjust policy across the whole gateway fleet is suspended for as long as the management server is down or untrusted. In both cases, recovery is defined not as restoring service on the vulnerable build, but as restoring service on a confirmed-patched, confirmed-clean build, since restoring a still-vulnerable or still-compromised system is not recovery, it is re-exposure.

**Recovery Point Objective (RPO), reframed for a security incident.** These are security compromises, not data-loss events in the traditional backup-and-restore sense, so the relevant "recovery point" is the last known-good configuration and policy state, not a data timestamp. The organization needs a trusted, validated backup of gateway and management-server configuration from before the exploitation window opened (2026-09-22 or earlier, pending compromise assessment) so that recovery can roll forward from a clean state rather than rebuild policy from memory under time pressure.

## 4. Impact Tiers (Qualitative)

| Impact Category | Tier | Rationale |
|---|---|---|
| **Financial** | High | No fabricated loss figures are used here; qualitatively, exposure includes incident response and forensic costs, potential emergency vendor engagement for a compressed patch cycle, and the operational cost of remote workforce and vendor downtime during containment and rebuild. |
| **Operational** | Severe | A gateway outage directly halts sanctioned remote access; a management server compromise removes assurance over policy across the entire gateway fleet without any visible outage, which is arguably the harder operational condition to manage because there is no obvious trigger to escalate. |
| **Reputational** | High | Both CVEs are publicly listed in the CISA KEV catalog with confirmed active exploitation and a compressed federal remediation deadline, which puts the organization's patch timeline on a clock that customers, partners, auditors, and regulators can all independently check against public disclosure dates. |
| **Regulatory / Compliance** | High | Organizations in regulated sectors relying on this gateway class for required network segmentation (for example, IT/OT boundary controls in critical infrastructure environments) may need to demonstrate that the control was not effectively compromised during the exposure window, which shifts this from a patching exercise to an evidentiary one. |

## 5. Maximum Tolerable Downtime (MTD)
For the gateway, maximum tolerable downtime should be set short, on the order of the business's normal tolerance for a full remote-access outage, because there is typically no automatic failover to an unaffected access path once the sanctioned VPN gateway is offline. For the management server, maximum tolerable downtime is longer in a strict availability sense, since the data plane keeps functioning without it, but the maximum tolerable duration of degraded trust, operating gateways without a verified-clean control plane, should be treated as short and should drive the urgency of the compromise assessment described in 06_POAM_Remediation.md rather than the urgency of a simple service restart.

## 6. Dependency Mapping
- **Remote workforce productivity** depends directly on gateway availability and, indirectly, on management server integrity for the policy that governs what remote users are permitted to reach.
- **Third-party and partner extranet connectivity** depends on the same gateway and inherits the same exposure.
- **OT remote vendor and engineering support access**, where the gateway is used as the IT/OT boundary and remote-access path, depends on both the gateway's data-plane integrity and the management server's policy integrity; this is the dependency chain flagged as highest priority given the IT/OT convergence risk described in 01_Threat_Intelligence.md Section 2.3.
- **Disaster recovery failover paths**, where a Check Point VPN gateway is itself part of the documented DR access mechanism for administrators reaching backup or recovery environments, inherit the same exposure and should be explicitly checked rather than assumed resilient.

## 7. Recovery Priority Tiering
1. **Tier 1 (Immediate):** Management server, given its blast radius across every managed gateway and the silent nature of a control-plane compromise.
2. **Tier 1 (Immediate):** Internet-facing gateways providing OT remote access, given the convergence risk to segmentation described in the risk assessment.
3. **Tier 2 (Near-Term):** General enterprise remote-access gateways not tied to OT segmentation.
4. **Tier 3 (Standard):** Any gateway or management instance confirmed isolated from untrusted networks and not internet-reachable, which still requires patching under the vendor's remediation guidance but carries materially lower immediate exposure.

---

## Revision History

| Version | Date | Author | Changes |
|---|---|---|---|
| 1.0 | 2026-09-28 | Blaise Kingko | Initial publication |

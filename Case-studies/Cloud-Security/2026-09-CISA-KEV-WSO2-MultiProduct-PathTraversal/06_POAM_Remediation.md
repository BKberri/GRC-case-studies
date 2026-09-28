# WSO2 Multiple Products Path Traversal — Plan of Action & Milestones (POA&M)

Case Study ID: CS-CLOUD-2026-09-001 | Risk Register Reference: RR-081 | Report Period: 2026-09-21 to 2026-09-28

This POA&M translates the findings in 01_Threat_Intelligence.md, 02_Risk_Assessment.md, and 04_Control_Mapping.md into tracked remediation items. Target dates are set against the KEV addition date (2026-09-24) and the federal remediation deadline (2026-09-27), not this program's standard change-management cadence, because the risk rating in this case study does not support a standard cadence. Owners are listed by role rather than by name, since this is published guidance for reader organizations to adopt against their own environment, not an internal tracker for a named organization.

---

## Immediate Actions (0–7 Days)

| POAM ID | Weakness | Framework Ref | Remediation Action | Resources Required | Milestone/Target Date | Status | Owner |
|---|---|---|---|---|---|---|---|
| POAM-2026-09-001 | Unpatched WSO2 instance vulnerable to CVE-2026-5430 (CWE-22 path traversal) | NIST 800-53 SI-2; CSF PR.PS; CIS 7.3/7.4 | Apply the vendor-issued fix to every WSO2 Identity Server, API Manager, and Micro Integrator/Enterprise Integrator instance in scope. Confirm version and patch level directly against WSO2's official advisory before closing this item. | Change-control exception approval; WSO2 admin access; maintenance window | 2026-09-27 | Open | Cloud Security Engineering |
| POAM-2026-09-002 | Vulnerable management/gateway interface reachable without network-layer compensating control | NIST 800-53 SC-7; CSF PR.IR; ISO A.8.3 | Where immediate patching is not feasible, restrict network exposure of the affected interface (allow-list, VPN-only access, or WAF virtual patch) until the vendor fix is applied. | Network/firewall change; WAF rule authoring | 2026-09-27 | Open | Network/Infrastructure Team |
| POAM-2026-09-003 | Potentially exposed credentials and signing keys (LDAP/AD bind accounts, OAuth client secrets, token-signing keys) | NIST 800-53 IA-5; ISO A.8.24; CSF PR.DS-01 | Rotate every credential and cryptographic key stored in configuration files or keystores on the affected instance, treating exposure as presumed rather than waiting for forensic confirmation. | IAM/PKI tooling; coordinated maintenance window across dependent applications | 2026-09-30 | Open | IAM Team |
| POAM-2026-09-004 | CVSS score and technical detail sourced from third-party trackers, not confirmed against NVD/WSO2 | Internal QA control; supports accurate risk scoring | Retrieve and review WSO2's official security advisory and NVD's published CVSS vector directly; update this case study's risk scoring in 02_Risk_Assessment.md if the confirmed figures differ from the reported 10.0. | Analyst time; access to WSO2 advisory portal and NVD | 2026-09-29 | Open | GRC / Risk Owner |

## Short-Term Actions (8–30 Days)

| POAM ID | Weakness | Framework Ref | Remediation Action | Resources Required | Milestone/Target Date | Status | Owner |
|---|---|---|---|---|---|---|---|
| POAM-2026-09-005 | No confirmed detection coverage for path traversal request patterns against WSO2 interfaces | NIST 800-53 SI-4; CSF DE.CM-01; CIS 8.5 | Deploy or verify detection rules (SIEM/WAF) for path traversal signatures against WSO2 endpoints, and confirm WSO2 application-level audit logs are centrally collected and correlated with cloud-provider audit trails. | SIEM engineering time; log forwarding configuration | 2026-10-08 | Open | Security Operations / Detection Engineering |
| POAM-2026-09-006 | WSO2 runtime identity and service accounts not verified against least privilege | NIST 800-53 AC-6; CIS 6.8; CSF PR.AA-05 | Review and reduce filesystem, cloud-IAM, and API scope permissions held by the WSO2 runtime identity and any service accounts it uses for downstream integrations. | IAM policy review; application owner coordination | 2026-10-15 | Open | IAM Team |
| POAM-2026-09-007 | Self-hosted WSO2 middleware potentially excluded from standard vulnerability scanning coverage | NIST 800-53 RA-5; CIS 7.3/7.4 | Confirm vulnerability scanning tooling explicitly covers self-hosted WSO2 instances, not just native cloud services, and add WSO2 to the asset inventory used for KEV cross-checks. | Vulnerability management tooling configuration | 2026-10-24 | Open | Cloud Security Engineering |
| POAM-2026-09-008 | Configuration files and key stores not encrypted at rest on host filesystem | NIST 800-53 SC-28; ISO A.8.24; CIS 3.11 | Enable encryption at rest for WSO2 configuration and keystore locations wherever the product version supports it. | Platform engineering time; potential downtime for re-encryption | 2026-10-24 | Open | Platform Engineering |

## Strategic Recommendations

| POAM ID | Weakness | Framework Ref | Remediation Action | Resources Required | Milestone/Target Date | Status | Owner |
|---|---|---|---|---|---|---|---|
| POAM-2026-09-009 | Identity and API-gateway infrastructure patched on the same cadence as general applications | CSF GV.RM-06, GV.SC-04 | Establish a formal accelerated-SLA patch tier for identity, IAM, and API-gateway infrastructure, so a future KEV addition against this asset class triggers pre-approved emergency change procedures rather than a case-by-case exception request. | Change management policy update; leadership sign-off | 2026-12-15 | Open | CISO / GRC Leadership |
| POAM-2026-09-010 | No standing credential/key rotation runbook tied to identity infrastructure incidents | NIST 800-53 IA-5; CSF RS.MI-02 | Build and rehearse a rotation runbook covering every credential and key class WSO2 (or equivalent identity/gateway infrastructure) holds, so rotation during a live incident is execution against a plan, not improvisation. | Tabletop exercise time; runbook documentation | 2026-12-15 | Open | IAM Team / Incident Response |

---

*Case Study CS-CLOUD-2026-09-001 — Blaise Kingko GRC Intelligence Program*

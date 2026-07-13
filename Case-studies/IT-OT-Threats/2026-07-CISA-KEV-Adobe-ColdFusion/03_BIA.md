# Business Impact Analysis — Adobe ColdFusion RDS Path Traversal RCE

## Affected Business Function
Any business application or workflow served by Adobe ColdFusion — commonly legacy or long-lifecycle enterprise web applications, internal portals, and integration middleware.

## Impact Categories

| Impact Type | Assessment |
|---|---|
| **Confidentiality** | Critical — SYSTEM-level host compromise exposes any data the ColdFusion application or host can reach, including databases and integrated backend systems |
| **Integrity** | Critical — attacker-controlled code execution allows arbitrary modification of application logic, data, or further payload deployment |
| **Availability** | High — a compromised host can be used for further attack staging, potentially including ransomware deployment or deliberate service disruption |
| **Regulatory/Compliance** | High — confirmed compromise on a host processing regulated data may trigger breach-notification obligations |
| **Reputational** | High — CVSS 10.0 unauthenticated RCE with confirmed active exploitation is the class of finding that draws external scrutiny if a breach is later disclosed |
| **Financial** | Medium-High — incident response, forensic investigation, and potential regulatory-notification costs scale with how long an instance was exposed |

## Recovery Time Objective (RTO) / Recovery Point Objective (RPO)
- **RTO:** Patch within the CISA-mandated window (target 2026-07-10); where patching cannot occur immediately, disable RDS and restrict access via WAF/firewall within 24 hours as an interim compensating control.
- **RPO:** Forensic log/file review should cover back to 2026-06-30 (patch availability date) at minimum, given the narrow window between disclosure and mass exploitation.

## Dependency Mapping
Any downstream system integrated with an affected ColdFusion application — databases, file shares, internal APIs, or connected business systems — inherits exposure from host compromise. Organizations should treat ColdFusion hosts as a pivot point requiring network segmentation review, not just an isolated patch target.

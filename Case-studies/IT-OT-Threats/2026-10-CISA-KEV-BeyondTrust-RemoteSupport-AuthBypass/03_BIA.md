# Business Impact Analysis, CVE-2026-102764 (BeyondTrust Remote Support Authentication Bypass)

**Case ID:** 2026-10-CISA-KEV-BeyondTrust-RemoteSupport-AuthBypass | **Scope:** Illustrative mid-size to large enterprise using privileged remote-support tooling

## 1. Affected Business Function

IT service desk and privileged remote-support operations; any business function that depends on BeyondTrust Remote Support to provide remote technical assistance to employees, systems, or (in managed-service contexts) client environments.

## 2. Impact Categories

| Category | Impact if Exploited |
|---|---|
| **Confidentiality** | Root-level compromise exposes any data accessible through the support tool's privileged access, including credentials and systems it was used to remotely service |
| **Integrity** | Attacker-deployed web shell and tunneler malware enable ongoing unauthorized changes across any system reachable through the compromised remote-support channel |
| **Availability** | A compromised remote-support platform can be disabled or weaponized, and a confirmed breach typically forces a temporary shutdown of remote-support capability during investigation |
| **Regulatory** | A nation-state-attributed breach of a privileged-access tool touching regulated systems or client environments carries elevated breach-notification and client-disclosure obligations |
| **Reputational** | Organizations providing managed IT or support services face direct client-trust consequences if their remote-support tooling is confirmed to have been a nation-state intrusion vector |

## 3. Recovery Time / Point Objectives (Illustrative)

- **RTO (Recovery Time Objective):** Immediate patching (hours) for the authentication-bypass fix itself, but full operational recovery confidence requires a forensic sweep of the appliance and any systems it accessed, which can extend recovery to days or weeks given confirmed log wiping by the attacker.
- **RPO (Recovery Point Objective):** Not cleanly applicable; because the attacker wiped logs, the organization may be unable to establish a precise point before which data can be considered uncompromised, requiring a conservative assumption that the full roughly seven-week window is in scope for review.

## 4. Dependency Mapping

Remote-support tools are, by design, broadly privileged and connected to many downstream systems, making this a high-fan-out dependency: a single compromised Remote Support instance can touch every system it was ever used to remotely access, and in managed-service or MSP contexts, potentially multiple client environments.

## 5. Criticality Determination

**Critical business function.** Privileged remote-access tooling is rated Tier 1 both for its operational necessity and because a compromise of the tool itself, rather than a single downstream system, represents the highest-fan-out intrusion vector an organization's IT operations can present.

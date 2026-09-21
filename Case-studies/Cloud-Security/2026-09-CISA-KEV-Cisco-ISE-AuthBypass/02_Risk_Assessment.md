# Risk Assessment
## 2026-09-CISA-KEV-Cisco-ISE-AuthBypass

## Risk Scoring
| Method | Score | Rating |
|---|---|---|
| Likelihood x Impact Matrix | 5 x 5 = 25 | Critical |
| CVSS Base Score | 10.0 (Critical) | Critical |
| FAIR Qualitative | Very high loss exposure — unauthenticated, network-reachable, confirmed active exploitation, and the compromised system is itself the network's identity/access decision point | Critical |

## Risk Narrative
Likelihood is scored at 5 (actively exploited in the wild) because CISA's KEV listing is a direct confirmation of real-world exploitation, not a theoretical or PoC-only status — the highest-confidence likelihood signal this program tracks. Impact is scored at 5 (full system compromise) because CVE-2026-76460 grants full unauthorized administrative access to the platform that governs network admission control; an attacker with ISE admin access can reconfigure authorization policy, provision themselves persistent trusted access, and potentially pivot into every network segment ISE mediates access to. The six companion CVEs (up to CVSS 10.0) compound this: even organizations that patch CVE-2026-76460 alone remain exposed to injection, access-control, and credential-protection gaps in the same platform, so this finding should be treated as a single mandatory full-patch-cycle event rather than a single-CVE fix.

## Framework Control Gaps
- **NIST 800-53 IA-2 (Identification and Authentication) / AC-3 (Access Enforcement):** Root cause — a privileged API path did not enforce the same authentication requirement as the front-end management interface it was meant to sit behind.
- **NIST 800-53 SI-2 (Flaw Remediation):** Organizations running ISE without a rapid emergency-patch process for identity infrastructure are exposed to the full 3-day KEV remediation window without sufficient lead time.
- **NIST CSF 2.0 PR.AA-01 (Identities and credentials are managed) / PR.PS-01 (Configuration management):** A centralized identity-and-access control plane is itself a Tier-0 asset requiring hardened patch cadence and compensating network controls distinct from ordinary infrastructure.
- **ISO 27001:2022 A.8.9 (Configuration Management) / A.8.5 (Secure Authentication):** The underlying failure is an authentication-boundary gap on a privileged API — a configuration/architecture control, not merely a patching lapse.

## Residual Risk Statement
After applying the vendor patches (3.1 Patch 12 / 3.2 Patch 11 / 3.3 Patch 12 / 3.4 Patch 7 / 3.5 Patch 4) across all ISE and ISE-PIC nodes, residual risk drops to Low, contingent on a forensic review of ISE administrative logs and policy configuration for signs of unauthorized changes made prior to patching — since KEV confirmation means exploitation activity may already have occurred against unpatched instances. Organizations that cannot patch within the 3-day CISA window should apply network-layer compensating controls (restrict management-plane access to a dedicated out-of-band management network) as an interim measure; this does not fully mitigate the underlying API flaw and residual risk remains High until patched.

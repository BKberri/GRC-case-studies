# POA&M / Remediation Plan — CVE-2026-20384 (Cisco Unified Communications Manager)

| # | Action | Owner | Target Date | Status |
|---|---|---|---|---|
| 1 | Identify all Unified CM / Session Management Edition clusters in environment | IT/Telecom Engineering | 2026-06-25 | Open |
| 2 | Apply Cisco's security patch removing/rotating the static credential | IT/Telecom Engineering | 2026-06-27 | Open |
| 3 | Restrict Unified CM management plane to internal/VPN-only access | Network Engineering | 2026-06-25 | Open |
| 4 | Review authentication logs and CDRs for use of the affected credential or anomalous access | Security Operations | 2026-06-27 | Open |
| 5 | Audit other Cisco UC components (Unity Connection, Expressway, IM&P) for similar static-credential issues | Security Operations | 2026-06-30 | Open |
| 6 | Assess regulatory notification obligations if interception is confirmed | Legal/Compliance | 2026-06-29 | Open |
| 7 | Document closure evidence (patch version, log review results) | GRC | 2026-07-02 | Open |

## Specific Remediation
Apply Cisco's vendor patch to remove or rotate the static credential in CVE-2026-20384 across all affected Unified CM and Unified CM Session Management Edition deployments. Pending patch, restrict management-plane access to internal/VPN-only networks.

## Federal Deadline
CISA-mandated due date: 2026-06-27 (3-day mandate, BOD 26-04, confirmed active exploitation).

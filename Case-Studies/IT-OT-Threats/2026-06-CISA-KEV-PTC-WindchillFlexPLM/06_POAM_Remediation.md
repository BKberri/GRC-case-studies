# POA&M / Remediation Plan — CVE-2026-12569 (PTC Windchill/FlexPLM)

| # | Action | Owner | Target Date | Status |
|---|---|---|---|---|
| 1 | Identify all Windchill/FlexPLM instances and confirm internet exposure status | IT/Engineering Systems | 2026-06-25 | Open |
| 2 | Apply PTC's security patch for CVE-2026-12569 | IT/Engineering Systems | 2026-06-28 | Open |
| 3 | Remove direct internet exposure pending patch; restrict to VPN-only access | Security Operations | 2026-06-25 | Open |
| 4 | Review system and access logs for indicators of compromise | Security Operations | 2026-06-28 | Open |
| 5 | Assess whether CUI or export-controlled data exposure triggers DFARS/CMMC/ITAR reporting | Legal/Compliance | 2026-06-29 | Open |
| 6 | Document closure evidence (patch version, log review results) | GRC | 2026-07-02 | Open |

## Specific Remediation
Apply PTC's vendor-issued patch for CVE-2026-12569 to every Windchill/FlexPLM instance. Pending patch deployment, remove direct internet exposure and restrict administrative access to VPN-gated networks only.

## Federal Deadline
CISA-mandated due date: 2026-06-28 (3-day mandate, BOD 26-04, confirmed active exploitation).

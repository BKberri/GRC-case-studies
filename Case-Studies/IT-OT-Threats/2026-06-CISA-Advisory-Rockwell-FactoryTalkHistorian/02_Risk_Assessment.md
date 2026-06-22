# Risk Assessment — CVE-2025-13036 / CVE-2025-44019 / CVE-2025-36539 (Rockwell FactoryTalk Historian SE)

## Risk Statement
Three chained vulnerabilities in Rockwell Automation's FactoryTalk Historian SE — including a critical insecure deserialization flaw — could allow an attacker with network access to achieve remote code execution against OT/ICS data historian infrastructure positioned at the IT/OT boundary.

## Likelihood: 3/5 (Possible — no confirmed active exploitation, but high attacker interest in ICS deserialization flaws)
- Not currently in CISA KEV (no confirmed active exploitation as of this advisory).
- Insecure deserialization is a well-known, highly attractive vulnerability class for ICS-targeting threat actors; public advisory increases risk of exploit development.
- Hardcoded credentials (CVE-2025-44019) lower the barrier to entry further if network access is achieved.

## Impact: 5/5 (Severe — OT/ICS environment compromise)
- FactoryTalk Historian sits at the IT/OT boundary; compromise provides a pivot point into the broader OT/ICS network.
- RCE on a historian server could enable manipulation or destruction of historical process data, disruption of reporting/analytics used for safety and compliance decisions, and use as a staging point for further OT intrusion.

## Risk Score: 15 (3 × 5) — **High**

## Inherent Risk: High
## Residual Risk: Medium-High (network segmentation between IT and OT, if properly implemented, meaningfully reduces exploitability; credential rotation reduces CVE-2025-44019 exposure)

## Business Risk Translation
Compromise of an OT data historian can directly impact safety, compliance, and operational reporting integrity — separate from any direct production disruption, this can undermine the data organizations rely on for regulatory and safety attestations.

## Compliance Note
Organizations operating under IEC 62443-aligned OT security programs, or with FactoryTalk Historian in scope for safety/compliance reporting, should treat this as a priority OT patch cycle item.

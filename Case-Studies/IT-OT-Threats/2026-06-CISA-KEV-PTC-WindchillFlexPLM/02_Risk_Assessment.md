# Risk Assessment — CVE-2026-12569 (PTC Windchill/FlexPLM)

## Risk Statement
An unauthenticated, critical-severity RCE vulnerability in PTC Windchill/FlexPLM PLM platforms is being actively exploited, putting engineering IP, product designs, and supply-chain data exposed through these platforms at risk of theft or destruction.

## Likelihood: 5/5 (Actively exploited in the wild)
- CISA confirmed active exploitation, triggering the accelerated 3-day BOD 26-04 mandate.
- No authentication required; internet-facing Windchill/FlexPLM instances are directly reachable and fingerprintable.

## Impact: 5/5 (Critical — high-value IP exposure plus potential operational disruption)
- PLM platforms house core intellectual property: engineering designs, CAD data, bills of materials, supplier and partner data.
- RCE allows full server compromise, enabling data exfiltration, ransomware deployment, or supply-chain data tampering.
- Aerospace/defense and industrial manufacturing sectors face elevated impact given the sensitivity of data typically stored in these systems.

## Risk Score: 25 (5 × 5) — **Critical**

## Inherent Risk: Critical
## Residual Risk: High until patched; reduced to Medium with patching plus network segmentation/internet-exposure removal.

## Business Risk Translation
For organizations in regulated industries (defense contractors under DFARS/CMMC, aerospace, automotive), a PLM compromise carries both a direct IP-theft risk and a secondary compliance risk: CUI (Controlled Unclassified Information) or export-controlled technical data stored in Windchill/FlexPLM may trigger ITAR/EAR reporting obligations if exfiltrated.

## Compliance Note
Organizations subject to CMMC 2.0 or DFARS 252.204-7012 should treat any confirmed compromise of a Windchill/FlexPLM instance storing CUI as a reportable cyber incident requiring DoD notification within the applicable timeline.

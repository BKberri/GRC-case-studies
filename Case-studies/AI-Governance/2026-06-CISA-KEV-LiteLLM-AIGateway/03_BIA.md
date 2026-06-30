# Business Impact Analysis — LiteLLM AI Gateway Multiple Vulnerabilities

## Affected Business Function
AI/LLM infrastructure — specifically any application or workflow that routes model calls through a LiteLLM gateway/proxy to one or more upstream AI providers.

## Impact Categories

| Impact Type | Assessment |
|---|---|
| **Confidentiality** | Critical — exposure of upstream AI provider API keys/credentials; potential exposure of prompt/output data passing through the gateway |
| **Integrity** | High — unauthorized actors could manipulate model routing, inject unauthorized requests, or alter gateway configuration |
| **Availability** | Medium-High — unmetered/unauthorized usage could exhaust rate limits or budget caps, degrading service for legitimate use; potential denial of service if gateway is destabilized |
| **Regulatory/Compliance** | High — AI governance frameworks (NIST AI RMF, ISO/IEC 42001) and, where applicable, EU AI Act obligations treat AI system security incidents as a distinct risk category requiring documented incident response |
| **Reputational** | High — given heightened public and regulatory scrutiny of AI security, an AI infrastructure breach carries disproportionate reputational risk relative to a conventional IT vulnerability |
| **Financial** | Medium-High — unauthorized/unmetered model usage can directly inflate AI provider billing |

## Recovery Time Objective (RTO) / Recovery Point Objective (RPO)
- **RTO:** Patch and credential rotation targeted within 48-72 hours of this report given confirmed active exploitation and the gateway's role as a credential chokepoint.
- **RPO:** Review AI provider billing/usage logs for anomalies covering the period since the 2026-06-11 disclosure to identify any unauthorized usage requiring remediation or provider notification.

## Dependency Mapping
Every internal application or workflow that depends on the affected LiteLLM gateway for AI model access inherits this risk — this includes any AI governance program's downstream assurance that model usage is properly authorized, logged, and attributable.

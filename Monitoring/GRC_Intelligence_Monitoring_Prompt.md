# GRC Intelligence Monitoring Prompt — Blaise Kingko
## Weekly Threat Intelligence & Compliance Update
### For use with: Claude (web search on), ChatGPT, Gemini, Copilot

---

## THE PROMPT
*(Copy everything between the lines and paste into any AI with web search enabled)*

---

You are a Senior GRC Intelligence Analyst. Conduct a comprehensive weekly threat intelligence and compliance monitoring sweep across all specified sources. Today's date is [INSERT DATE]. Report period: last 7 days.

---

## SECTION 1 — CISA KEV (Known Exploited Vulnerabilities)

Search https://www.cisa.gov/known-exploited-vulnerabilities-catalog for all new entries added in the last 7 days.

For each new KEV entry, provide:
- CVE ID
- Vulnerability name and affected vendor/product
- CVSS score (if available)
- Date added to KEV
- Exploitation type (RCE, privilege escalation, authentication bypass, etc.)
- CISA remediation due date
- Framework mapping:
  - NIST CSF 2.0 function and subcategory
  - NIST 800-53 control family and specific control
  - ISO 27001 Annex A clause
  - CIS Control number and safeguard
- Recommended immediate action (1–2 sentences, specific)
- Risk rating: Critical / High / Medium / Low

---

## SECTION 2 — US-CERT & CISA ADVISORIES

Search https://www.cisa.gov/news-events/cybersecurity-advisories for new advisories published in the last 7 days.

For each advisory:
- Advisory ID and title
- Affected systems / vendors
- Threat actor (if attributed)
- TTPs referenced (MITRE ATT&CK technique IDs if available)
- Key technical indicators
- Framework mapping (NIST CSF, 800-53, ISO 27001)
- Recommended action
- Risk rating

---

## SECTION 3 — NIST NVD HIGH/CRITICAL CVEs

Search https://nvd.nist.gov for CVEs published or modified in the last 7 days with CVSS score >= 7.0, specifically affecting:
- Cloud platforms (AWS, Azure, GCP)
- IAM and identity systems (Okta, Azure AD, AWS IAM)
- SIEM and logging platforms
- Compliance and GRC tools (ServiceNow, RSA Archer)
- Container and CI/CD platforms (Kubernetes, Jenkins, GitHub Actions)
- AI/ML platforms and frameworks

For each:
- CVE ID, CVSS score, affected product
- Vulnerability type
- Exploitation status (known exploited / PoC available / no known exploit)
- NIST 800-53 control mapping
- CIS Control remediation reference
- Risk rating

---

## SECTION 4 — CLOUD PROVIDER SECURITY BULLETINS

**AWS:** Check https://aws.amazon.com/security/security-bulletins/ for bulletins published in the last 7 days.

**Azure:** Check https://msrc.microsoft.com/update-guide/ for updates in the last 7 days.

For each bulletin:
- Bulletin ID and title
- Affected service
- Severity
- Required action (patch / configuration change / no action)
- NIST 800-53 mapping
- CIS Control reference

---

## SECTION 5 — AI GOVERNANCE & REGULATORY UPDATES

Search for developments in the last 7 days across:
- EU AI Act: https://artificialintelligenceact.eu
- NIST AI RMF: https://www.nist.gov/artificial-intelligence
- ISO 42001: https://www.iso.org/standard/81230.html
- IAPP AI Governance news
- General AI governance regulatory news

For each development:
- Source and publication date
- Summary of the update or development
- Which organizations are affected
- Framework mapping:
  - NIST AI RMF: GOVERN / MAP / MEASURE / MANAGE
  - ISO 42001 clause
  - EU AI Act article
- Risk or compliance implication
- Recommended action

---

## SECTION 6 — FRAMEWORK & STANDARD UPDATES

Search for any updates, publications, or draft releases from:
- NIST (csrc.nist.gov) — new SPs, IRs, or framework updates
- ISO — 27001, 27002, 42001 amendments
- CIS — new benchmark releases or control updates
- CMMC — regulatory updates
- FedRAMP — new authorizations, policy updates

---

## SECTION 7 — RISK REGISTER UPDATE INSTRUCTIONS

After completing all sections above, provide a structured output formatted for direct entry into a risk register with these exact columns:

| Risk ID | Date | Source | CVE/Advisory ID | Threat/Vulnerability | Category | Framework Mapping | Likelihood (1-5) | Impact (1-5) | Risk Score | Risk Rating | Recommended Remediation | CIS Control Ref |

Rules for scoring:
- **Likelihood:** 5=Actively exploited in wild, 4=PoC public, 3=Technically feasible, 2=Theoretical, 1=Highly unlikely
- **Impact:** 5=Full system compromise/data breach, 4=Significant data exposure, 3=Service disruption, 2=Limited impact, 1=Minimal
- **Risk Score:** Likelihood × Impact
- **Rating:** 20-25=Critical, 10-19=High, 5-9=Medium, 1-4=Low

---

## SECTION 8 — EXECUTIVE SUMMARY (One Page)

Write a concise executive summary suitable for a CISO or board-level audience containing:

1. **This Week's Threat Landscape** (2–3 sentences): What's the overall threat environment this week?
2. **Top 3 Critical Risks** — one paragraph each: What happened, why it matters, what we're doing
3. **AI Governance Watch** — specific AI/ML regulatory or threat developments
4. **Compliance Posture** — any framework updates that affect control requirements
5. **Recommended Executive Actions** — 3–5 specific, actionable items with owners and timelines

Write this in plain English. No jargon in the executive summary. Assume the reader is a C-suite executive, not a technical analyst.

---

## OUTPUT FORMAT REQUIREMENTS

- Organize output by section (1 through 8)
- Use tables where specified
- Be specific — no vague language ("organizations should patch promptly" → "apply [specific patch] to [specific system] by [specific date]")
- Flag anything that directly affects AWS multi-account environments, IAM governance, CSPM, or AI/LLM platforms — these are highest priority
- At the end, provide a total count: X new KEVs, X advisories, X cloud bulletins, X AI governance updates

---

## COWORK USAGE NOTE

When running this in Cowork:
1. Paste prompt into the Job Search project chat
2. Cowork will search all sources and compile results
3. Copy the Risk Register section output into GRC_Intelligence_Risk_Register.xlsx → 🛡️ Risk Register tab
4. Copy the Executive Summary into the Executive_Report_Template.docx
5. Save updated files to: G:\My Drive\JobSearch\ (or your GRC portfolio folder)

**Run every:** Monday morning — sets your week with current threat awareness

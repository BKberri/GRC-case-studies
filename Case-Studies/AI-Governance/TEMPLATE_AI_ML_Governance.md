# [INCIDENT TITLE] — AI/ML & LLM Governance Case Study
> **Example title format:** `Prompt Injection Attack on Enterprise LLM Deployment — AI Governance Risk Analysis`

---

## Case Study Metadata

| Field | Details |
|---|---|
| **Case Study ID** | CS-AI-[YYYY-MM-###] |
| **Date Published** | [YYYY-MM-DD] |
| **Incident Date** | [YYYY-MM-DD or Month YYYY] |
| **Author** | Blaise Kingko |
| **Threat Category** | AI/ML — [LLM Security / Model Risk / Data Poisoning / Governance / Regulatory] |
| **MITRE ATLAS Technique** | [AML.T#### — if applicable] |
| **CVE / Advisory ID** | [CVE or advisory if applicable — many AI threats have no CVE] |
| **Affected System** | [LLM platform / ML model / AI application / Training pipeline] |
| **AI Framework** | [OpenAI / AWS Bedrock / Azure OpenAI / Hugging Face / Custom] |
| **Intelligence Source** | [MITRE ATLAS / NIST AI RMF / EU AI Act / Vendor Advisory / Research Paper] |
| **Incident Type** | [Active exploit / Research finding / Regulatory action / Policy gap] |

---

## 1. Incident Summary

### 1.1 What Happened
*2–3 sentences. State the AI-specific risk event clearly. What AI system, what attack or governance failure, what was the outcome or potential outcome.*

[Insert plain-language summary here]

### 1.2 Why It Matters
*1–2 sentences. AI threats are often misunderstood at the executive level. Frame this in terms decision-makers understand — liability, data exposure, regulatory risk, reputational harm.*

[Insert business impact framing here]

### 1.3 AI System Context

| Field | Details |
|---|---|
| **AI System Type** | [Generative AI / Discriminative / Reinforcement Learning / RAG / Agent] |
| **Deployment Model** | [Internal / Customer-facing / Third-party / Embedded] |
| **Data Access** | [What data can this AI system access or process] |
| **Human Oversight** | [Full human review / Partial / Minimal / Automated only] |
| **Risk Classification** | [EU AI Act: Unacceptable / High / Limited / Minimal risk] |
| **Business Process** | [What business function does this AI system support] |

---

## 2. Technical Analysis

### 2.1 Threat / Attack Details

| Field | Details |
|---|---|
| **Threat Type** | [Prompt Injection / Jailbreak / Data Poisoning / Model Inversion / Membership Inference / Model Theft / Adversarial Input / Supply Chain] |
| **Attack Complexity** | [Low / Medium / High] |
| **Attacker Position** | [External user / Internal user / Third-party / Supply chain] |
| **Exploits Model Behavior** | [Yes / No — describe how model behavior is manipulated] |
| **Data at Risk** | [Training data / User data / System prompts / Business logic] |
| **Persistence** | [One-time / Persistent in model / Persistent in pipeline] |

### 2.2 Attack Chain
*Map to MITRE ATLAS techniques where applicable. ATLAS is the AI/ML equivalent of ATT&CK.*

1. **Reconnaissance** — [How attacker learns about the AI system — ATLAS AML.T####]
2. **Initial Access** — [Entry point into the AI system — ATLAS AML.T####]
3. **Manipulation** — [How the model is manipulated or exploited — ATLAS AML.T####]
4. **Collection / Exfiltration** — [What is extracted — ATLAS AML.T####]
5. **Impact** — [Ultimate objective — ATLAS AML.T####]

### 2.3 AI-Specific Attack Detail
*Provide technical depth on the AI-specific mechanism. This section should demonstrate understanding of how LLMs and ML systems actually work.*

**For Prompt Injection:**
- Direct vs indirect injection: [Which type and how it works]
- System prompt exposure: [Was the system prompt extractable]
- Tool/plugin abuse: [Did the attack leverage connected tools]
- Data exfiltration vector: [How data was extracted through the model]

**For Data Poisoning:**
- Training data entry point: [How malicious data entered the pipeline]
- Backdoor trigger: [What input triggers the backdoored behavior]
- Detection difficulty: [Why this is hard to detect post-deployment]

**For Model Inversion / Membership Inference:**
- Queries required: [How many queries and what type]
- Data reconstructed: [What training data was recoverable]
- PII exposure: [What personal data was at risk]

**For Governance / Regulatory:**
- Policy gap identified: [What governance or oversight failure occurred]
- Regulatory implication: [Which regulation was triggered]
- Accountability gap: [Who was responsible and where the chain broke]

### 2.4 Root Cause
*What is the underlying design, governance, or architectural failure?*

[Insert root cause — be specific. "The LLM lacked adequate input validation" is not enough. "The system prompt was not isolated from user-accessible context, and no guardrails prevented prompt injection through the document upload feature" is a root cause.]

---

## 3. Framework Impact Analysis

### 3.1 NIST AI RMF Mapping

| Function | Category | Sub-category | Finding |
|---|---|---|---|
| **GOVERN** | Organizational Practices | [e.g., GOV-1.1 — Policies, processes, procedures are in place] | [Gap or finding] |
| **GOVERN** | Risk Culture | [e.g., GOV-2.2 — Mechanisms to sustain accountability are in place] | [Gap or finding] |
| **MAP** | Context | [e.g., MAP-1.5 — Organizational risk tolerances are determined] | [Gap or finding] |
| **MAP** | AI Risk | [e.g., MAP-5.1 — Likelihood of impacts on individuals is documented] | [Gap or finding] |
| **MEASURE** | Analysis | [e.g., MSR-2.5 — AI system to be deployed is demonstrated to be valid] | [Gap or finding] |
| **MEASURE** | Monitoring | [e.g., MSR-4.1 — Post-deployment risks are monitored] | [Gap or finding] |
| **MANAGE** | Mitigation | [e.g., MGT-1.3 — Responses to identified risks are prioritized] | [Gap or finding] |
| **MANAGE** | Incidents | [e.g., MGT-4.1 — Identified AI risks are responded to] | [Gap or finding] |

### 3.2 ISO 42001 Mapping

| Clause | Requirement | Finding |
|---|---|---|
| 4.1 | Understanding the organization and its context | [Finding] |
| 6.1.2 | AI risk assessment | [Finding] |
| 6.1.3 | AI risk treatment | [Finding] |
| 8.4 | AI system impact assessment | [Finding] |
| 9.1 | Monitoring, measurement, analysis, and evaluation | [Finding] |
| 10.1 | Continual improvement | [Finding] |

### 3.3 EU AI Act Mapping

| Article / Annex | Requirement | Finding |
|---|---|---|
| Article 9 | Risk management system | [Finding — required for high-risk AI] |
| Article 10 | Data and data governance | [Finding — training data requirements] |
| Article 11 | Technical documentation | [Finding — documentation requirement] |
| Article 13 | Transparency and information provision | [Finding — user disclosure] |
| Article 14 | Human oversight | [Finding — oversight mechanisms] |
| Article 15 | Accuracy, robustness, and cybersecurity | [Finding — security requirements] |
| Annex III | High-risk AI systems list | [Is this system high-risk per Annex III?] |

### 3.4 NIST SP 800-53 Mapping
*AI systems deployed in enterprise environments still need to map to 800-53 controls:*

| Control Family | Control | Finding |
|---|---|---|
| System & Services Acquisition | SA-11 | Developer Security and Privacy Testing |
| System & Communications Protection | SC-28 | Protection of Information at Rest |
| Audit & Accountability | AU-2 | Event Logging |
| Risk Assessment | RA-3 | Risk Assessment |
| Supply Chain Risk Management | SR-3 | Supply Chain Controls and Processes |

---

## 4. Risk Assessment

### 4.1 Risk Scoring

| Dimension | Score | Rationale |
|---|---|---|
| **Likelihood** | [1–5] | [How likely is exploitation — consider attacker access to the system, technical skill required] |
| **Impact** | [1–5] | [Data sensitivity, regulatory exposure, reputational risk, safety implications] |
| **Risk Score** | [L × I] | [Calculated] |
| **Risk Rating** | [Critical / High / Medium / Low] | [20-25=Critical, 10-19=High, 5-9=Medium, 1-4=Low] |

### 4.2 AI-Specific Risk Dimensions
*Score each dimension 1–5:*

| AI Risk Dimension | Score | Notes |
|---|---|---|
| **Explainability** | [1–5] | Can the AI system's decisions be explained and audited? |
| **Fairness / Bias** | [1–5] | Does the system exhibit bias that creates discriminatory outcomes? |
| **Robustness** | [1–5] | How vulnerable is the system to adversarial inputs? |
| **Privacy** | [1–5] | What personal data is processed and how is it protected? |
| **Safety** | [1–5] | Can system outputs cause physical or psychological harm? |
| **Human Oversight** | [1–5] | How much meaningful human control exists over decisions? |
| **Supply Chain** | [1–5] | How well is the upstream model/data supply chain secured? |

### 4.3 EU AI Act Risk Classification

- [ ] **Unacceptable Risk** — Prohibited under EU AI Act (social scoring, real-time biometrics in public spaces)
- [ ] **High Risk** — Requires conformity assessment, technical documentation, human oversight (Annex III)
- [ ] **Limited Risk** — Transparency obligations apply (chatbots must disclose AI nature)
- [ ] **Minimal Risk** — No specific obligations under EU AI Act

---

## 5. Risk Model Implications

### 5.1 How This Challenges Traditional Risk Models
*AI threats require entirely new risk thinking. Traditional vulnerability management, network segmentation, and access control frameworks were not designed for systems that can be manipulated through natural language.*

[Insert analysis — 2–4 paragraphs. Address: why AI risk is probabilistic not deterministic, why traditional pen testing doesn't cover LLM attack surfaces, why the attack surface changes with every model update, how AI supply chain risk differs from software supply chain risk]

### 5.2 Where Traditional GRC Controls Break Down

- **[Traditional control 1]:** [Why it fails for AI — e.g., "Input validation rules cannot anticipate all prompt injection variations in a generative context"]
- **[Traditional control 2]:** [Why it fails]
- **[Traditional control 3]:** [Why it fails]

### 5.3 Governance Gap Analysis
*AI governance is still maturing. Where does this incident reveal gaps between what organizations have and what they need?*

- **Policy gap:** [What AI governance policy is missing or inadequate]
- **Process gap:** [What operational process doesn't exist or isn't working]
- **Technical gap:** [What technical control is absent]
- **Accountability gap:** [Who owns AI risk and where is that ownership unclear]

---

## 6. Recommended Controls & Remediation

### 6.1 Immediate Actions (0–7 Days)

| Action | Owner | Framework Reference | Priority |
|---|---|---|---|
| [e.g., Implement input/output guardrails on all LLM interfaces] | AI/ML Security | NIST AI RMF: MGT-1.3 \| ISO 42001: 8.4 | 🔴 Critical |
| [e.g., Audit system prompts — ensure not exposed to user context] | AI Engineering | NIST AI RMF: MSR-2.5 | 🔴 Critical |
| [e.g., Enable logging of all LLM inputs and outputs for audit] | Security / AI Ops | NIST 800-53: AU-2 | 🟠 High |

### 6.2 Short-Term Actions (8–30 Days)

| Action | Owner | Framework Reference | Priority |
|---|---|---|---|
| [Conduct AI system risk assessment per NIST AI RMF] | GRC / AI Owner | NIST AI RMF: MAP-1.5 \| ISO 42001: 6.1.2 | 🟠 High |
| [Implement red team / adversarial testing program for LLMs] | Security | NIST AI RMF: MSR-2.6 | 🟠 High |
| [Document intended use case and prohibited use cases] | AI Governance | EU AI Act: Article 11 \| ISO 42001: 4.1 | 🟡 Medium |

### 6.3 Strategic Recommendations

| Recommendation | Framework Reference | Business Rationale |
|---|---|---|
| [Establish AI Governance program with dedicated AI risk register] | NIST AI RMF: GOVERN \| ISO 42001 | [Why this is a program-level need] |
| [Implement EU AI Act conformity assessment for high-risk systems] | EU AI Act: Article 9 | [Regulatory deadline and liability exposure] |
| [Deploy LLM-specific security tooling — prompt injection detection] | NIST AI RMF: MSR-4 | [Continuous monitoring requirement] |

### 6.4 AI-Specific Technical Controls
- **Prompt Injection Defense:** Instruction hierarchy enforcement — system prompts take precedence over user inputs; separate contexts clearly
- **Output Filtering:** Post-generation filtering for PII, toxic content, sensitive business data before delivery to user
- **Rate Limiting & Anomaly Detection:** Monitor for unusual query patterns indicative of model probing or data extraction attempts
- **Human-in-the-Loop:** For high-risk decisions, require human review before AI output is acted upon
- **Model Versioning:** Maintain audit trail of which model version produced which output — essential for incident investigation
- **Supply Chain Vetting:** Evaluate upstream models, training datasets, and fine-tuning sources for security and bias risks

---

## 7. Executive Summary

*Write last. Maximum one page. Plain English. Board-level reader. AI topics require extra care — executives often misunderstand both the capability and the risk.*

### The Situation
[What AI system is affected and what the risk event was — avoid technical jargon]

### The Business Risk
[Liability, regulatory exposure, customer trust, safety — connect to business outcomes not technical findings]

### What We Are Doing
[Immediate and near-term actions — specific governance and technical responses]

### What We Need From Leadership
[AI governance requires executive sponsorship — what decisions or resources are needed at the top]

---

## 8. References & Sources

| Source | URL | Date Accessed |
|---|---|---|
| MITRE ATLAS | https://atlas.mitre.org | [Date] |
| NIST AI RMF | https://www.nist.gov/artificial-intelligence | [Date] |
| ISO 42001 | https://www.iso.org/standard/81230.html | [Date] |
| EU AI Act | https://artificialintelligenceact.eu | [Date] |
| OWASP LLM Top 10 | https://owasp.org/www-project-top-10-for-large-language-model-applications/ | [Date] |
| [Research paper / vendor advisory] | [URL] | [Date] |

---

## 9. Revision History

| Version | Date | Author | Changes |
|---|---|---|---|
| 1.0 | [YYYY-MM-DD] | Blaise Kingko | Initial publication |

---

*Case Study Template v1.0 — Blaise Kingko GRC Intelligence Program*
*Framework References: NIST AI RMF | ISO 42001 | EU AI Act | MITRE ATLAS | NIST SP 800-53 Rev 5*

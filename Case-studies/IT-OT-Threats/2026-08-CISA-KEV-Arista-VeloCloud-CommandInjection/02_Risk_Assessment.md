# Risk Assessment
## 2026-08-CISA-KEV-Arista-VeloCloud-CommandInjection

## Risk Scoring
| Method | Score | Rating |
|---|---|---|
| Likelihood × Impact Matrix | 5 × 5 = 25 | Critical |
| CVSS Base Score | 10.0 | Critical |
| FAIR Qualitative | High loss exposure (WAN-wide compromise, high probability of threat event given active exploitation) | High |

## Risk Narrative
An unauthenticated attacker who identifies an internet-exposed VeloCloud Orchestrator can execute arbitrary OS commands with no credentials and no user interaction — the likelihood factor is scored at the maximum (5) because active, in-the-wild exploitation is already confirmed rather than theoretical. Impact is scored at the maximum (5) because VCO is the single control point for an entire SD-WAN fabric: an attacker with orchestrator-level code execution can push malicious configuration or firmware to every managed edge device, manipulate WAN routing, and use the orchestrator as a pivot point into every site the fabric connects. The most probable attack path is opportunistic internet-wide scanning for exposed VCO management interfaces followed by direct exploitation of the command injection flaw — no phishing, credential theft, or insider access is required, which places this well within reach of both financially motivated ransomware affiliates and more capable actors seeking durable WAN-level persistence across a multi-site enterprise.

## Framework Control Gaps
- **NIST 800-53 SI-10 (Information Input Validation):** The root cause is insufficient server-side validation of input passed into an OS command context — a textbook SI-10 control gap.
- **NIST 800-53 SC-7 (Boundary Protection) / AC-4 (Information Flow Enforcement):** Internet-facing exposure of the orchestrator management interface, rather than restricting it to a VPN, private WAN segment, or allow-listed source range, removed a compensating network-layer control that would have significantly reduced the attack surface even with the vulnerability present.
- **NIST CSF 2.0 PR.PS-04 (Software is maintained, replaced, and removed commensurate with risk):** Organizations running VCO versions predating 5.2.3.14 / 6.1.3.4 / 6.4.2.4 had not completed a patch cycle Arista had already published fixes for in prior releases of the affected branches.
- **CIS Control 12 (Network Infrastructure Management):** Management-plane interfaces for network orchestration platforms should be isolated from general internet exposure; this control, if implemented, would have prevented remote exploitation even absent a patch.

## Residual Risk Statement
After patching to VCO 5.2.3.14, 6.1.3.4, 6.4.2.4, or 7.0.0.1+ and restricting management-interface exposure to trusted networks, residual risk drops to Low. Organizations should still assume compromise is possible for any VCO instance that was internet-exposed and unpatched between vulnerability disclosure and the patch/isolation date, and should treat orchestrator and downstream edge-device credentials, certificates, and configuration baselines as potentially exposed pending forensic review.

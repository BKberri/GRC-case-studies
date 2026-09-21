# Control Mapping
## 2026-09-NIST-NVD-MCP-Server-TrustBoundary-Batch

## Applicable Frameworks
NIST AI RMF and ISO 42001 for AI-tooling governance and risk-assessment gaps; NIST CSF 2.0 and NIST 800-53 Rev 5 for the underlying authentication and transport-security control failures; MITRE ATLAS for AI-specific supply-chain and access-technique mapping.

## Control Mapping Table
| Framework | Control ID | Control Name | Applicability | Gap / Status |
|---|---|---|---|---|
| NIST 800-53 | IA-2 | Identification and Authentication | Multiple MCP servers in the batch exposed endpoints without authentication | Gap (vendor, patched) |
| NIST 800-53 | SC-8 | Transmission Confidentiality and Integrity | Cleartext HTTP transport for a registry backend (atomic-agents-stack) | Gap (vendor, patched) |
| NIST CSF 2.0 | ID.SC-04 | Suppliers and third-party partners are assessed | MCP server component sourcing (open-source/community) warrants a documented vetting policy | Organizational — recommended |
| NIST AI RMF | GOVERN 1.1 | Policies for AI risk management established | Standing MCP-server inventory and vetting process recommended given three-week pattern | Organizational — recommended |
| ISO 42001 | 6.1.2 | AI risk assessment | MCP tooling layer should be explicit scope in AI system risk assessments, not just the model | Organizational — recommended |

## Control Narrative
This is the third consecutive week this program has logged a critical MCP-server or AI-agent-tooling trust-boundary finding. The individual CVEs are unrelated (different vendors, different root causes), but the pattern across all three weeks is the same: MCP server implementations, as a software category, are being adopted faster than their authentication, transport-security, and input-validation maturity has caught up. This program's standing recommendation is that organizations building AI agents establish an explicit MCP-server vetting and inventory process — treating each new MCP integration with the same third-party software risk assessment rigor applied to any other vendor dependency — rather than continuing to treat each week's finding as an isolated patch event.

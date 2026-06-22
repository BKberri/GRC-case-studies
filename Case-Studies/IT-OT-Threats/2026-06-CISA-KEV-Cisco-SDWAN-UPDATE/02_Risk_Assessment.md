# Risk Assessment — CVE-2026-20262 (Cisco Catalyst SD-WAN Manager Path Traversal)

## Risk Statement
Active, in-the-wild exploitation of a path-traversal vulnerability in Cisco Catalyst SD-WAN Manager allows an authenticated remote attacker to write arbitrary files to the underlying OS and escalate to root, granting full administrative control of the enterprise WAN management plane. This is the second independently-exploited Cisco SD-WAN Manager vulnerability added to CISA KEV within two weeks (following CVE-2026-20245, added 2026-06-09).

## Likelihood: 4/5 (PoC public / actively exploited)
- Confirmed active exploitation per CISA KEV addition and multiple independent threat intel sources (SecurityAffairs, SOCRadar, Halo Security).
- Authentication is a prerequisite, which moderately reduces the addressable attack surface relative to a fully unauthenticated flaw, but credential-stuffing and prior-compromise scenarios make this readily reachable in environments with weak account hygiene.

## Impact: 5/5 (Full system compromise)
- Root on SD-WAN Manager equals control of the entire enterprise WAN fabric: routing policy, segmentation, and traffic visibility across all connected sites.
- A compromised SD-WAN control plane can be used to pivot into every site connected to the fabric, disable security policies, or redirect traffic for interception.

## Risk Score: 20 (4 × 5) — **Critical**

## Inherent Risk: Critical
## Residual Risk (with compensating controls): High
Compensating controls (MFA on all admin accounts, vManage restricted to a dedicated management segment, audit log forwarding to SIEM) reduce — but do not eliminate — exposure until the patch is applied. There is no workaround for the path-traversal flaw itself.

## Business Risk Translation
If this vulnerability is exploited, the organization could lose the ability to trust or control its own wide-area network — every branch and data center connection routed through the affected SD-WAN fabric becomes a potential pivot point. This is equivalent in severity to losing control of core network infrastructure, with downstream risk to every business application that depends on WAN connectivity.

## Threat Actor / Targeting Context
No specific threat actor has been publicly attributed at the time of this run; exploitation patterns described in vendor reporting are consistent with targeted, opportunistic exploitation of internet-reachable or weakly segmented management interfaces rather than a mass-scanning campaign.

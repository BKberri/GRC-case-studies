# Executive Summary
## 2026-09-MSRC-Azure-AI-PlatformBatch
**Date:** 2026-09-21 | **Prepared by:** GRC Intelligence Program | **Classification:** High

## What Happened
Microsoft fixed two severe flaws in its AI platforms — one in Azure AI Foundry (where organizations build custom AI models and agents) and one in Microsoft 365 Copilot (the AI assistant built into Office and Teams). Both flaws could have let an attacker gain elevated, unauthorized access without needing valid credentials for that specific function. Microsoft found and fixed both before going public, and there's no evidence either was actually exploited against a customer.

## Why It Matters
This is the second week in a row this program has flagged a serious security gap in Microsoft's Azure AI platform. No single incident here is catastrophic — Microsoft caught both issues first — but a pattern of repeated critical findings in the same platform family is worth watching. Organizations building on Azure AI or using Copilot broadly should treat "the vendor already fixed it" as the start of due diligence, not the end of it.

## What We Are Doing About It
- If we use Azure AI Foundry, review platform logs from before September 17th for unusual privileged activity, new service accounts, or unexpected role/API changes (Cloud/AI Security Team, target: within 5 business days)
- No customer-side patch action is required for either flaw — confirm this with our Microsoft account team in writing for our records (GRC, target: within 1 week)
- Add "Azure AI platform trust-boundary findings" as a standing watch item given this is the second consecutive week of a similar finding (AI Governance, target: ongoing)

## Bottom Line
Nothing here requires emergency action — Microsoft closed both gaps before exploitation was confirmed. The leadership-level takeaway is a trend, not a single incident: as we lean further into Microsoft's AI tooling, we should expect this pace of disclosure to continue and should build the log-review habit into our standard process rather than treating each one as a one-off.

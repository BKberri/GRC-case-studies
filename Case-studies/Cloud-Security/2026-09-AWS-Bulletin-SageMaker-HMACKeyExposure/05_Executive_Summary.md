# Executive Summary
## 2026-09-AWS-Bulletin-SageMaker-HMACKeyExposure
**Date:** 2026-09-07 | **Prepared by:** GRC Intelligence Program | **Classification:** High

## What Happened
A flaw in Amazon's machine-learning platform (SageMaker) meant that in a shared account with multiple data science teams, one team's security key for running their AI models could be read by another team with ordinary account access — and used to run code as if they were that other team. Amazon fixed this on September 1st.

## Why It Matters
Many organizations run shared AI/ML environments where teams assume they're isolated from each other by the platform. This flaw shows that assumption doesn't always hold. It's an inside-the-house risk — someone who already has legitimate but limited access could escalate to act as a more privileged team — which is different from, but no less serious than, an outside attacker breaking in.

## What We Are Doing About It
- Confirm whether we use SageMaker's `@step`/`@remote` pipeline features in a shared account and upgrade the SDK to the fixed version (Data Science/ML Engineering, target: within 1 week)
- Rotate any pipeline signing keys that were in use before the patch, since an already-exposed key stays valid until rotated (ML Engineering, target: within 1 week)
- Review whether our shared AI/ML environments should segregate higher-sensitivity work into separate accounts rather than relying on in-account permissions alone (AI Governance / Cloud Architecture, target: next quarterly architecture review)

## Bottom Line
No sign this was exploited against us — Amazon caught and fixed it first. The lesson for leadership is that "shared AI platform, different teams" needs the same isolation scrutiny we'd apply to any other shared multi-tenant system, and right now that scrutiny is playing catch-up with how fast these AI platforms are adding features.

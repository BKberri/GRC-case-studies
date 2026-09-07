# Executive Summary
## 2026-09-AWS-Bulletin-MCP-Server-InputValidation
**Date:** 2026-09-07 | **Prepared by:** GRC Intelligence Program | **Classification:** High

## What Happened
AWS found and fixed two flaws in the tools it publishes to let AI agents (like Claude or Amazon Q) work with company databases. One flaw meant an agent that was supposed to be locked into "look only, don't touch" mode on a database could, under the right conditions, still make changes. The other meant a code-generation shortcut for building cloud infrastructure could be tricked into running an attacker's code if the input it was given wasn't trustworthy.

## Why It Matters
Organizations are rapidly connecting AI agents directly to production systems and trusting configuration settings — like "read-only mode" — to keep those agents from doing more than intended. This is the second time in two weeks our monitoring has caught a flaw in that exact kind of safety switch, from a different vendor each time. That is a pattern, not a coincidence, and it means "the AI agent is configured as read-only" should not, on its own, be treated as a real security boundary.

## What We Are Doing About It
- Confirm whether we run either AWS MCP tool (`postgres-mcp-server`, `dynamodb-mcp-server`) for any AI-agent database integration and upgrade to the fixed versions (1.1.7+ / 2.1.6+) (AI/Platform Engineering, target: within 5 business days)
- Review the actual database permissions granted to any AI agent's service account — the real control is the database role, not the application's "read-only" toggle (Database/Cloud Engineering, target: within 2 weeks)
- Add "can this agent's safety configuration be bypassed at the application layer?" as a standing question in any future AI-agent-to-data-system integration review (AI Governance, target: next architecture review cycle)

## Bottom Line
No evidence either flaw was used against us or anyone else — both were caught and fixed by AWS before attackers found them. The real takeaway is architectural: as we connect more AI agents to real systems, we need to enforce their boundaries at the infrastructure level (permissions, roles, network segmentation), not just trust the AI tool's own settings.

# Executive Summary — AI Gateway Security Flaw (LiteLLM)

## What Happened
A widely-used piece of software that many organizations use to manage and route requests to AI services like ChatGPT and Claude (called an "AI gateway") was found to have serious security flaws, including a way to bypass login security entirely. This is being actively exploited.

## Why It Matters
AI gateways often hold the "keys" — the credentials — that let an organization talk to outside AI providers. If an attacker gets into the gateway, they could steal those credentials, run up unauthorized AI usage charges, or potentially use the gateway as a stepping stone into our internal network. This is treated as a top-priority finding because it touches our AI infrastructure directly.

## What We're Doing
We are confirming whether this gateway software is in use anywhere in our environment, applying the security fix, rotating any credentials that may have been exposed, and reviewing usage logs for signs of unauthorized activity.

## Recommended Executive Actions
1. **Confirm whether LiteLLM (or any AI gateway software) is deployed anywhere in the environment** — Owner: AI/Platform Engineering — Target: within 48 hours.
2. **If deployed, apply the security patch and rotate all associated AI provider credentials** — Owner: AI/Platform Engineering — Target: within 72 hours.
3. **Review AI usage billing and access logs for anomalies since June 11** — Owner: Security Operations — Target: this week.

## Note to Reader
This finding originated from a disclosure just before our normal weekly look-back window, but is included this week because of its severity and direct relevance to AI infrastructure security, consistent with this program's standing priority on AI/LLM platform risks.

# Executive Summary — PTC Windchill/FlexPLM Remote Code Execution (CVE-2026-12569)

## What Happened
A critical, actively exploited flaw in PTC's Windchill and FlexPLM product-design management software allows an attacker to take over the server without needing a password. These systems typically store our most sensitive engineering and product data.

## Why It Matters
If we use Windchill or FlexPLM to manage product designs, bills of materials, or supplier data, this flaw could let an attacker steal or tamper with that intellectual property, or hold the system for ransom. Federal agencies have been given an unusually short three-day window to fix this due to confirmed active attacks.

## What We're Doing
We are confirming whether any Windchill/FlexPLM instance we operate is internet-facing, applying the vendor patch immediately, and restricting access to internal networks only until the patch is confirmed.

## Recommended Executive Actions
1. **Identify all Windchill/FlexPLM instances** and confirm internet exposure status — Owner: IT/Engineering Systems — Target: 24 hours.
2. **Apply the PTC security patch** to all affected instances — Owner: IT/Engineering Systems — Target: within the federal 3-day deadline.
3. **Review for signs of compromise**, including unauthorized changes to design data — Owner: Security Operations — Target: this week.
4. **Determine if any exposed data triggers regulatory reporting obligations** (CMMC/DFARS/export control) — Owner: Legal/Compliance — Target: this week.

# Threat Intelligence Summary
## Case: CISA KEV 2026-03 — Hikvision & Rockwell Automation Dual Listing
**Date:** 2026-03-10 | **Analyst:** Blaise Kingko

---

## 1. Contextual Analysis

CISA's Known Exploited Vulnerabilities (KEV) catalog is the prioritization gold standard for federal and enterprise vulnerability management. While the National Vulnerability Database (NVD) contains over 200,000 entries, KEV contains roughly 1,000 — these two additions represent confirmed active exploitation in the top tier of global threat activity.

## 2. Vulnerabilities Added

| CVE | Vendor | Component | CVSS v3.1 |
|---|---|---|---|
| CVE-2017-7921 | Hikvision | IP camera authentication bypass | 9.8 (Critical) |
| CVE-2021-22681 | Rockwell Automation | PLC credential storage/transmission | 9.8 (Critical) |

## 3. Threat Actor Profiling

**Motivation:** Espionage (Hikvision surveillance access) and sabotage/extortion (Rockwell industrial control access).

**Observed Behavior:** Automated scanning activity targeting the Hikvision `/SDK/service/` path to extract device and user configuration data.

**Target Sectors:** Critical infrastructure, government facilities, and high-tech manufacturing.

## 4. Vulnerability Weaponization Timeline

Both CVEs were originally disclosed years before this KEV listing but saw a surge in exploitation activity in Q1 2026. The most likely driver is the leak of automated exploit kits on underground forums, which lowered the barrier to entry for lower-tier threat actors and turned previously low-volume exploitation into broad opportunistic scanning.

## 5. Intelligence-Driven Action

This intelligence drove a program-level shift in approach: rather than treating this as a standard "patch the CVE" exercise, the GRC lead recommended moving from **Vulnerability Management** (finding the bug) to **Exposure Management** (validating whether the bug is actually reachable from the internet) — because the controlling risk factor for both CVEs is asset visibility and network exposure, not patch availability alone.

---

*Sources: CISA KEV Catalog (added 2026-03-06), NVD, vendor advisories.*

---
name: Compare cross-retailer sales week-for-week
description: Pull and normalize sales across multiple retailers to compare performance on a consistent weekly calendar.
api: mcp/corvera-mcp.yml
operations: [resolve_corvera_context, get_corvera_data, get_tesco_data, get_sainsburys_data, get_whole_foods_data]
---

# Compare cross-retailer sales week-for-week

Use this skill to analyze how a product line is performing across retailers on a normalized weekly calendar.

## Prerequisites
- Connected to Corvera over MCP (`https://mcp.corvera.ai/mcp`); see the connect-and-explore skill.
- The relevant retailer sources connected (e.g. Tesco, Sainsbury's, Whole Foods).

## Steps
1. **Resolve the entities.** Call `resolve_corvera_context` to map the product/brand terms in the question to Corvera's canonical entities and planning numbers.
2. **Pull per-retailer sales.** Call the connected retailer tools — `get_tesco_data`, `get_sainsburys_data`, `get_whole_foods_data` — for the product and period in question.
3. **Or pull cross-source at once.** Prefer `get_corvera_data` when you want a single governed cross-retailer result rather than stitching per-retailer calls yourself.
4. **Compare like-for-like.** Corvera normalizes retailer calendars (e.g. "Tesco and Sainsbury's, week for week"), so weeks align across sources — compare depletion/scan sales on the normalized week.
5. **Explain gaps.** Check the freshness indicator for each source before drawing conclusions; a stale feed can look like a sales drop.

## Rules
- Only retailers whose integrations are connected expose a `get_<retailer>_data` tool.
- Use canonical entities from step 1 throughout so figures reconcile with the team's shared Context glossary.

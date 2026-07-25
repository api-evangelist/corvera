---
name: Track distributor depletions and velocity
description: Monitor distributor depletion and velocity data across KeHE, VIP, and UNFI to catch stockouts and demand shifts early.
api: mcp/corvera-mcp.yml
operations: [list_my_integrations, get_kehe_velocity_data, get_vip_data, get_unfi_data]
---

# Track distributor depletions and velocity

Use this skill to watch distributor movement so you can flag stockout risk and demand changes.

## Prerequisites
- Connected to Corvera over MCP (`https://mcp.corvera.ai/mcp`).
- Distributor sources connected (KeHE, VIP, and/or UNFI).

## Steps
1. **Confirm sources.** Call `list_my_integrations` and verify the distributors you need are connected.
2. **Pull KeHE velocity.** Call `get_kehe_velocity_data` for daily depletion/velocity figures.
3. **Pull VIP depletions.** Call `get_vip_data` for VIP depletion sales.
4. **Pull UNFI.** Call `get_unfi_data` for UNFI distributor movement.
5. **Compare and flag.** Line up velocity across distributors for the same items and period; a sharp velocity drop against steady retail scan sales often signals a supply/allocation issue rather than demand.

## Rules
- Distributor feeds refresh on their own cadence — check each source's freshness indicator before comparing.
- If a distributor tool is absent, connect that integration first; tools appear automatically once the source is connected.

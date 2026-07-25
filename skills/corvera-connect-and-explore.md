---
name: Connect Corvera and explore available data
description: Connect an MCP client to Corvera and discover which governed datasets are available to query.
api: mcp/corvera-mcp.yml
operations: [list_my_integrations, list_corvera_data, resolve_corvera_context]
---

# Connect Corvera and explore available data

Use this skill to attach an MCP-capable client to Corvera and find out what you can ask about.

## Prerequisites
- A Corvera account with at least one data source connected.
- An MCP-capable tool (Claude Desktop/Code, ChatGPT developer mode, Cursor, Lovable, or Replit).

## Steps
1. **Add the MCP server.** Point the tool at `https://mcp.corvera.ai/mcp` (HTTP transport).
2. **Authorize.** On first connect Corvera opens a sign-in popup — complete the OAuth 2.0 (authorization code + PKCE) flow with your Corvera account. Scopes requested: `openid`, `email`, `profile`, `user:org:read`.
3. **Confirm the connection.** Call `list_my_integrations` to list the data sources available to your account. The tool set you can call is gated by these connected integrations.
4. **See what's queryable.** Call `list_corvera_data` to enumerate the governed datasets across your connected sources.
5. **Resolve context.** When a question uses business terms or canonical entities, call `resolve_corvera_context` so answers use your team's shared glossary and mappings.

## Rules
- Availability of per-source tools (e.g. `get_tesco_data`) depends on which integrations are connected; if a tool is missing, connect that source first — no reconfiguration is needed afterward.
- Respect role-based dataset access controls; a Member may see fewer datasets than an Admin.

# CookieRisk QuickScan for AI agents

This skill helps an AI assistant check one public homepage for cookies and tracking observed before banner interaction.

## Get started

1. Use an agent that supports Agent Skills and remote MCP servers over Streamable HTTP.
2. Add this skill to your agent using its skill installer or by placing this folder in its skills directory.
3. Add the CookieRisk MCP server at `https://cookierisk.eu/mcp`. See the [CookieRisk setup guide](https://cookierisk.eu/developers/mcp) for client configuration.

Try asking your assistant:

> Use CookieRisk QuickScan to check https://example.com/ for cookies and tracking before any banner interaction.

Replace the example with the public homepage you want checked. A scan visits that website, and anyone with a returned report link can open it. QuickScan is a point-in-time check. See [SKILL.md](SKILL.md) for the workflow and evidence limits.

[Privacy policy](https://cookierisk.eu/privacy) · [Contact CookieRisk](https://cookierisk.eu/contact)

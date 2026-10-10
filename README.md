# INSPIFY AI — MCP plugin

Connects agent runtimes (Grok Build, Cursor, Claude and others) to the INSPIFY AI Creative Agency. Marketing teams use it to create brand storybooks from a brief, publish them on the brand's own domain, share them with tracked links or link campaigns, and read how they perform.

- **Plugin id:** `inspify-ai`
- **Version:** 0.3.0
- **MCP server key:** `inspify-ai`

## What it ships
- **One MCP server (HTTP):** `https://mcp.inspify.ai/mcp`. The server lists the tools a token may use and explains them in its `initialize` instructions; the plugin carries no copy of the tool list.
- **Three skills:** `inspify-creative-agency-mcp` (connection and scope), `inspify-story-workflow` (order of the work), `inspify-security-deny` (deny-by-default rules).
- No hooks, commands, scripts or binaries.

## Network endpoints
- `https://mcp.inspify.ai` — the MCP server. The plugin calls nothing else.
- Links returned by the server point to the INSPIFY Hub (`*.inspify.com`) and to the brand's storybook domain, for people to open.

## Credentials
- `INSPIFY_MCP_TOKEN` — a bearer token issued by INSPIFY, sent as `Authorization: Bearer …` to `mcp.inspify.ai` only. It belongs to one brand and carries the scopes that decide which tools appear.
- The plugin ships no credentials. Never commit tokens, `.env` files or cloud keys.
- Sign-in with an INSPIFY account (OAuth) is planned; until then, ask INSPIFY for a token.

## Security
- **Deny-by-default:** no shell access, no cloud admin keys, no destructive disk operations.
- **Tenancy:** every call is limited to the token's brand; the server rejects ids of other brands.
- **Least privilege:** request only the scopes you need; read-only scopes are available.

## Hub
- `https://www.inspify.ai/login`

## License
MIT

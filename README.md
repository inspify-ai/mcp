# inspify-ai — INSPIFY AI plugin (Phase 1)

INSPIFY AI Creative Agency + Hub connector for agent runtimes.

**Plugin id:** `inspify-ai` · **Display:** INSPIFY AI · **MCP server key:** `inspify`  
**Product:** Creative Agency

## What it ships
- **MCP:** remote HTTP → `https://mcp.inspify.ai/mcp`
- **Skills:** security deny-by-default · Creative Agency tool guide (Alex 16) · Phase 1 pilot scope

## Credentials (not in this repo)
Operator issues a least-privilege bearer service token (brand allowlist + scopes).  
**Never** commit tokens, `.env`, AKIA keys, or MFA.

## Network endpoints
- `https://mcp.inspify.ai/mcp` — Creative Agency MCP
- `https://app.inspify.ai` — Hub UI deep-links

## Security (Morgan gate)
Deny-by-default: host/Mac Shell · AWS Admin/human keys · Chair disk wipe.  
Tenancy: token brand allowlist; no cross-Brand DNA; prefer single-tenant read-only until isolation proven.

## Marketplace
Source org: **inspify-ai** only (`https://github.com/inspify-ai/mcp`). Never `inspify/*`.

## License
MIT

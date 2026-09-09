# INSPIFY AI — MCP plugin

Connect agent runtimes (Cursor, Grok, Claude, and others) to the INSPIFY AI Creative Agency. Start Story jobs, poll progress, review work, give feedback, publish, and deep-link to the Hub.

- **Plugin id:** `inspify-ai`
- **Display:** INSPIFY AI
- **MCP server key:** `inspify-ai`
- **Product:** AI Creative Agency

## Endpoints
- **MCP server:** `https://mcp.inspify.ai/mcp` (Streamable HTTP)
- **Hub UI:** `https://app.inspify.ai`

## What it provides
- **MCP server** exposing the AI Creative Agency tools — start a Story job, answer research questions, select a direction, review the work, submit feedback, and publish.
- **Skills** for agent runtimes: a security-by-default skill and the AI Creative Agency tool guide.

## Authentication
This plugin does **not** ship credentials. Each agent uses a least-privilege bearer service token issued by an INSPIFY AI operator. A token is scoped to a single brand and a set of read/write permissions, and the server enforces that scope on every call.

Never commit tokens, `.env` files, cloud access keys, or MFA secrets to this repository.

## Security
- **Deny-by-default:** the server never exposes host shell access, cloud admin keys, or destructive disk operations.
- **Tenancy:** every request is scoped to the brand bound to the token. Cross-brand access is rejected.
- **Least privilege:** prefer read-only scopes until write access is explicitly required.

## License
MIT

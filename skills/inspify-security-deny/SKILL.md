---
name: inspify-security-deny
description: >-
  Use before any INSPIFY MCP or plugin action. Deny-by-default: no host shell,
  no cloud admin keys, no destructive disk operations, no secrets in files,
  and strict brand tenancy.
---
# INSPIFY AI plugin — security deny-by-default

## Never do
1. **Host / shell access** — this plugin needs no shell; do not run commands on its behalf.
2. **Cloud admin keys** — never use human or admin cloud credentials.
3. **Destructive disk operations** — never wipe, shred or change disks.
4. **Secrets in files** — the token lives only in the `INSPIFY_MCP_TOKEN` environment variable. Never write it into manifests, skills, READMEs, samples or logs.
5. **Cross-brand data** — a token belongs to one brand, and the server rejects ids of other brands. Do not try to read or mix data across brands.

## Allowed
- HTTPS MCP calls to `https://mcp.inspify.ai/mcp` with the token from `INSPIFY_MCP_TOKEN`.
- The tools the server lists for this token. Confirm write actions with the user first.
- Links into the INSPIFY Hub and to the brand's storybooks for people to open.

## Fail closed
Unauthorized, missing scope, or another brand's id → stop and show the server's error. Never fall back to a shell or to admin keys.

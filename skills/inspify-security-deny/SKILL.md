---
name: inspify-security-deny
description: >-
  Use before any INSPIFY MCP or plugin action. Deny-by-default: no host shell,
  no cloud admin keys, no destructive disk ops, no secrets in the bundle, and
  strict brand tenancy.
---
# INSPIFY AI plugin — security deny-by-default

## Deny by default (never do)
1. **Host / shell access** — no machine-targeted shell, no local checkout drives, no credential minting from this plugin.
2. **Cloud admin keys** — never use human/admin cloud credentials; never invoke cloud shell for MCP hosting.
3. **Destructive disk ops** — never wipe, shred, or mutate disks.
4. **Secrets in bundle** — no `.env`, access keys, bearer tokens, MFA, or passwords in manifests, skills, README, or samples. Tokens are operator-issued at install time only.
5. **Cross-brand data** — never pull or mix brand data or jobs across brands. The token's brand allowlist is authoritative; if multi-brand isolation is unproven, stay **read-only single-tenant**.

## Allowed
- HTTP MCP calls to `https://mcp.inspify.ai/mcp` with a scoped bearer token via a secure secret store.
- The allowed AI Creative Agency tools only. Writes: confirm before send.
- Deep-link URLs into the Hub UI for human editing.

## Fail closed
Unauthorized, missing scope, or cross-brand → do nothing; surface the MCP error. Do not fall back to host shell or admin keys.

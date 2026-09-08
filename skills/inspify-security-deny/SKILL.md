---
name: inspify-security-deny
description: >-
  Use before any INSPIFY MCP or plugin action — deny-by-default host/Mac Shell,
  AWS Admin/human keys, Chair disk; no secrets in bundle; brand tenancy.
---
# INSPIFY AI plugin — security deny (Morgan gate)

## Deny by default (never do)
1. **Host / Mac Shell** — no machine-targeted Shell, no local checkout drives, no Eng GH mint from this plugin.
2. **AWS Admin / human keys** — never use Chair/human Admin AWS credentials; never call AWS Shell for MCP hosting until Morgan CLEAR. AWS Shell STOP stands.
3. **Chair disk** — never wipe, shred, or mutate Chair disk (HARD RULE forever).
4. **Secrets in bundle** — no `.env`, AKIA keys, bearer tokens, MFA, or passwords in manifests, skills, README, or samples. Tokens are operator-issued at install time only.
5. **Cross-brand Brand DNA** — never pull or mix Brand DNA / jobs across brands. Token brand allowlist is authoritative; if multi-brand isolation unproven, stay **read-only single-tenant**.

## Allowed
- HTTP MCP calls to `https://mcp.inspify.ai/mcp` with a scoped bearer token via secure secret UI.
- Phase 1 team-pilot tools only (Alex allowlist). Writes: confirm-before-send.
- Deep-link URLs into Hub UI for human edit.

## Fail closed
Unauthorized, missing scope, or cross-brand → do nothing; surface MCP error. Do not fall back to host Shell or Admin keys.

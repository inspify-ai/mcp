---
name: inspify-phase1-pilot
description: >-
  Use to scope INSPIFY AI MCP usage to the allowed tool set and brand tenancy.
  Pair with inspify-security-deny. Writes confirm before send; publish is
  human-in-command.
---
# INSPIFY AI MCP — scope and boundaries

**Product:** AI Creative Agency.  
**Allowed tools:** the 15 AI Creative Agency MCP tools (see the creative-agency-mcp skill).

## In scope
- Agents acting for a single tenant with a valid scoped token.
- The allowed tools only.
- Writes: confirm before send. Publish: human-in-command.
- Deep-link humans to the Hub Scene Designer (URL only). Lead with the Scene Designer.

## Out of scope
- Tools not in the allowed list (do not invent aliases).
- Host shell, cloud admin keys, destructive disk ops.
- Cross-tenant brand data.

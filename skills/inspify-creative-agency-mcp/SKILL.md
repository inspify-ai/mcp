---
name: inspify-creative-agency-mcp
description: >-
  Use to start or poll INSPIFY AI Creative Agency Story jobs via MCP. Pair with
  inspify-security-deny first. Only the allowed tools below are supported.
---
# INSPIFY AI Creative Agency MCP

**Endpoint:** `https://mcp.inspify.ai/mcp` (Streamable HTTP)  
**Product name:** AI Creative Agency

## Before every call
Read the security-deny skill first — no host shell, no cloud admin keys, no destructive disk ops, no secrets, no cross-brand data.

## Auth
Operator-issued bearer token via a secure secret store only. Never embed tokens. Scopes and brand allowlist are enforced server-side.

## Allowed tools (15 — contract names only)
| Tool | Mode |
|---|---|
| `list_campaign_goals` | read |
| `list_jobs` | read |
| `get_job` | read |
| `get_pending_questions` | read |
| `start_story_job` | write — confirm before send |
| `submit_answers` | write — confirm |
| `answer_design_decision` | write — confirm |
| `list_directions` | read |
| `select_direction` | write — confirm |
| `get_review_bundle` | read |
| `submit_review_recommendation` | write — author never grades own work |
| `submit_feedback` | write — confirm |
| `get_repair_status` | read |
| `publish_story` | write — human-in-command; confirm |
| `get_published_story` | read |

Hub deep-links to the Scene Designer are URL guidance only (not an MCP tool). Poll async work via `get_job` / `get_review_bundle`.

## Do not invent
Do not call tools outside the list above (e.g. `list_stories`, `get_story`, `list_scenes`, `get_scene`, `start_agency_job`, `get_agency_job`, `get_ai_credits`, `list_campaigns`, `get_campaign_funnel`, or `hub_deep_link` — none of these are MCP tools). Also: no customer tokens, no localisation claims, no secret tooling, no cross-tenant reads, no host-shell fallbacks.

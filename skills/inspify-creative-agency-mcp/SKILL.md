---
name: inspify-creative-agency-mcp
description: >-
  Use when kicking or polling INSPIFY AI Creative Agency Story jobs via MCP
  (team pilot). Pair with inspify-security-deny first. Phase 1 = Alex allowlist only.
---
# INSPIFY AI Creative Agency MCP (Phase 1)

**Endpoint:** `https://mcp.inspify.ai/mcp` (Streamable HTTP)  
**Allowlist SSOT:** `/workspace/inspify/gtm/MCP-PHASE1-ALLOWLIST-v1.md` (Alex CONFIRM)  
**Product name:** Creative Agency

## Before every call
Read security-deny skill first — deny host/Mac Shell, AWS Admin keys, Chair disk; no secrets; no cross-brand DNA.

## Auth
Operator-issued bearer via secure secret UI only. Never embed tokens. Scopes + brand allowlist server-enforced.

## ALLOWED (16 — contract names ONLY)
| Tool | Mode |
|---|---|
| `list_brands` | read |
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
| `submit_review_recommendation` | write — author never grades self |
| `submit_feedback` | write — confirm |
| `get_repair_status` | read |
| `publish_story` | write — human-in-command; confirm |
| `get_published_story` | read |

Hub deep-link to Scene Designer = URL guidance only (not an MCP tool). Poll async via `get_job` / `get_review_bundle`.

## DENIED (do not invent)
Hub draft aliases: `list_stories`, `get_story`, `list_scenes`, `get_scene`, `start_agency_job`, `get_agency_job`, `get_ai_credits`, `list_campaigns`, `get_campaign_funnel`, `hub_deep_link` as MCP tools. Also: customer tokens, §11, localisation claims, secret tooling, cross-tenant reads, host Shell fallbacks.

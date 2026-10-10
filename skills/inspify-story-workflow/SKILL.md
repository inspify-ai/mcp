---
name: inspify-story-workflow
description: >-
  Use to take an INSPIFY AI storybook from brief to a shared, tracked link:
  the order of the MCP tool calls across a story job, publishing, sharing and
  tracking. Pair with inspify-security-deny and inspify-creative-agency-mcp.
---
# INSPIFY AI — from brief to tracked link

The order of the work. If the server's `initialize` instructions or a tool's description say something different, follow the server.

## 1. Make the story
- `get_brand_kit` (optional) — the brand's persona, palette, typography and logos. Story jobs already use it.
- `start_story_job` — send the brief. Returns a `jobId`. It costs credits; `get_credits` shows the balance and the cost.
- `get_job` — check progress. `envelope.nextAction.tool` names the next call.
- `get_pending_questions` → `submit_answers` — when the job asks questions.
- `answer_design_decision` — when `job.designDecisions` holds a pending question.
- `list_directions` → `select_direction` — show the concepts to the user and let them choose.

## 2. Review and repair
- `get_review_bundle` — scenes, review films (links valid 10 minutes) and findings.
- `submit_feedback` — a problem in one scene, in plain words. Follow with `get_repair_status`, then review again.
- `submit_review_recommendation` — your own grades and recommendation. Advice only.

## 3. Publish
- `publish_story` — needs the `storybookId` (from `get_job`, the selected direction) and an approval code from a named person. Ask the user for the code.
- `get_published_story` — the story's link on the brand's own domain.

## 4. Share
- `create_link_campaign` — a link campaign: a short link on the brand's domain, tracked under the campaign id.
- `create_share_link` — the same kind of link without a campaign.
- `create_campaign` — a campaign for contacts already in one of the brand's campaign audiences.

## 5. Track
- `get_campaign_analytics` — results of a campaign or link campaign.
- `get_storybook_insights` — all traffic of a storybook; pass a share link's `utm_campaign` as `campaign`.
- `get_audience_analytics` — results per recipient of a campaign.

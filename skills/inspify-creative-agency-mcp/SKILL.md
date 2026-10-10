---
name: inspify-creative-agency-mcp
description: >-
  Use when working with INSPIFY AI through its MCP server: brand storybooks,
  campaigns, share links, analytics and the brand kit. Explains the connection,
  the token's scope, and where the current list of tools comes from.
---
# INSPIFY AI Creative Agency MCP

**Endpoint:** `https://mcp.inspify.ai/mcp` (Streamable HTTP)
**Auth:** a bearer token issued by INSPIFY, read from the `INSPIFY_MCP_TOKEN` environment variable. One token belongs to one brand; its scopes decide which tools the server offers.

## The server is the reference
- The server's `initialize` instructions describe the order of the work, where each id comes from, and what is not available yet. Read them first.
- `tools/list` returns exactly the tools this token may use, each with a description and documented parameters. Use those tools only. The list grows over time, so do not rely on a fixed list from this file.

## What the server covers
- **Story jobs:** make an interactive brand storybook from a brief, answer its questions, choose a creative direction, review it, send feedback.
- **Publishing:** `publish_story` makes the story live on the brand's own domain. It needs an approval code issued after a named person approves the version; the agent cannot create that code.
- **Sharing:** `create_share_link` (a tracked short link to a story) and `create_link_campaign` (the same link saved as a campaign). `create_tracked_link` shortens any web address, such as a page of the brand's website, with UTM values; INSPIFY counts no clicks for it.
- **Campaigns:** messaging and link campaigns, status, audiences, campaign groups and results — see `inspify-campaign-management`. Changing status does not send messages.
- **Analytics:** storybook, scene, campaign and audience results.
- **Hub reads:** storybooks, scenes, teams, people, workspace, and the brand kit (read-only).
- **Credits:** `get_credits` shows the balance and what a story job costs. Buying credits through this connection is not available yet.

## Working rules
- Ids come from earlier results. Never invent one.
- Story jobs take minutes to hours. Check back with `get_job`; do not poll in a tight loop.
- Write tools take an `idempotencyKey`: a new unique value per action, reused only to retry the same action.
- Confirm with the user before spending credits, publishing, or changing a campaign.
- Errors carry `data.reason`; the server's instructions explain each one.

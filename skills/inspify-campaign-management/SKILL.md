---
name: inspify-campaign-management
description: >-
  Use to run INSPIFY AI campaigns through the MCP server: create messaging and
  link campaigns, manage their status, audiences and campaign groups, and read
  their results. Pair with inspify-security-deny and inspify-creative-agency-mcp.
---
# INSPIFY AI — campaign management

A campaign delivers one published storybook. If the server's `initialize` instructions or a tool's description say something different, follow the server.

## Two kinds of campaign
- **Messaging campaign** — `create_campaign`: a name, `channel` (any of whatsapp, email, sms, line, wechat, telegram, kakaotalk), the `storybookId`, the `message`, and an `audience` of contact ids. The message can use {firstname}, {lastname}, {salesadvisor}, {salesadvisor.firstname}, {salesadvisor.lastname}.
- **Link campaign** — `create_link_campaign`: a name, the `storybookId`, `utmSource` and `utmMedium`. No audience; you get a short link on the brand's domain to share anywhere, tracked under the campaign id.

## Tracked link to any web page
- `create_tracked_link` — any `https://` address (for example a page of the brand's website) with optional `utmSource`, `utmMedium` and `utmCampaign`, shortened on the brand's domain, as the Hub's "Create Tracked Link" does.
- Nothing is stored and INSPIFY counts no clicks: the short link only redirects. The destination's own analytics read the UTM values.
- For a story, use `create_link_campaign` or `create_share_link`; their views are reported.

## Audience
- The audience is fixed when the campaign is created and cannot be changed later.
- Contacts cannot be created or searched through this connection. Reuse contacts from an earlier campaign: `get_campaign_audience` or `list_contacts` on that campaign gives their ids. Otherwise the contacts are added in the INSPIFY Hub first.

## Status
- A campaign starts as DRAFT, or SCHEDULED when `scheduledAt` is set.
- `activate_campaign`, `pause_campaign`, `complete_campaign`, `archive_campaign`, `unarchive_campaign` and `delete_campaign` change the status. They do not send messages; sending is started in the INSPIFY Hub.
- `update_campaign` changes name, message, storybook, schedule or dates while the campaign is DRAFT, SCHEDULED or PAUSED. Channel and audience stay as created.
- A campaign cannot be deleted while ACTIVE; pause it first. Completing and deleting cannot be undone through this connection.

## Find and organise
- `list_campaigns` and `get_campaign` — the brand's campaigns and their details.
- `list_campaign_groups`, `get_campaign_group`, `create_campaign_group`, `update_campaign_group`, `delete_campaign_group`, `add_campaigns_to_group`, `remove_campaigns_from_group`, `list_group_campaigns`, `get_campaign_group_stats` — bundle campaigns that serve one objective.

## Results
- `get_campaign_analytics` — the campaign's funnel, viewers, devices, countries and top scenes.
- `get_audience_analytics` — results per recipient: delivery, views, watch time, clicks, shares.
- `get_storybook_insights` — all traffic of the storybook; pass a share link's `utm_campaign` as `campaign`.
- Group analytics return placeholder zeros today; read the campaigns one by one.

## Before changing anything
Confirm with the user before creating, activating, pausing, completing, archiving or deleting a campaign.

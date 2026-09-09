---
name: inspify-story-workflow
description: >-
  Use to take an INSPIFY AI Creative Agency Story job from brief to published.
  Describes the ordered tool calls an agent makes across the job lifecycle.
  Pair with inspify-security-deny and inspify-creative-agency-mcp.
---
# INSPIFY AI Creative Agency — Story job workflow

The end-to-end lifecycle of a Story job. Each step names the MCP tool to call and what to wait for before the next.

## 1. Start the job
- `start_story_job` — send the brief, brand context, and any asset references. Returns a `jobId` and the job enters `generating`.
- If research is required, the job pauses in research and surfaces pending questions.

## 2. Answer research questions
- `get_pending_questions` — fetch the open questions for the job.
- `submit_answers` — return the answers. The job resumes generation.
- Some jobs also surface design decisions: `answer_design_decision` resolves them.

## 3. Choose a creative direction
- `list_directions` — read the candidate creative directions the agency authored.
- `select_direction` — pick one. Production of the Story begins.

## 4. Review the work
- `get_job` — poll status until the Story is ready for review.
- `get_review_bundle` — fetch signed URLs to the rendered Storybook (video) and any story-level findings.
- `submit_review_recommendation` — record a review verdict (the author never grades its own work).
- `submit_feedback` — send scene-specific notes if revisions are needed.

## 5. Repair loop (if needed)
- `get_repair_status` — poll while revisions are in flight. Repeat from step 4 when a new revision is ready.

## 6. Publish
- `publish_story` — publish the approved Story to the Hub. This requires a human approval receipt (human-in-command); the agent never self-publishes.
- `get_published_story` — fetch the public Hub link for the published Story.

## Rules of thumb
- Poll async work with `get_job` / `get_review_bundle`; do not busy-wait.
- Writes: confirm before send. Publish: human-in-command only.
- Deep-link humans to the Hub Scene Designer (URL only) for manual editing.

# Slack + Hermes Integration

## Purpose

This document defines how Hermes Agent uses Slack as the human-in-the-loop command center for the RIOS operating system.

Hermes owns orchestration.

Slack provides visibility, approvals, and human decision trails.

RIOS remains the system of record.

## Core Pattern

```text
Slack event -> Hermes interprets -> RIOS updates -> Hermes assigns workers -> Worker output returns -> Slack approval/signoff -> RIOS final update
```

## Hermes Responsibilities in Slack

Hermes should:

- Listen for new change requests
- Convert Slack messages into structured mission records
- Assign CR IDs and mission IDs
- Route tasks to OpenClaw, Claude Code, Codex, ChatGPT, or other workers
- Post status updates
- Request sign-offs
- Notify blockers
- Summarize completed work
- Mirror decisions into RIOS

## Event Types

```yaml
slack_event_types:
  new_change_request:
    channel: '#change-requests'
    action: create_cr_record

  new_feature_request:
    channel: '#feature-backlog'
    action: create_backlog_item

  approval_decision:
    channel: '#signoffs'
    action: update_mission_state

  github_pr_event:
    channel: '#github-activity'
    action: attach_pr_to_mission

  agent_alert:
    channel: '#agent-alerts'
    action: create_blocker_or_incident

  client_update:
    channel: '#client-updates'
    action: update_delivery_status
```

## Hermes Slack Message Schema

Every Hermes Slack message should include:

```yaml
hermes_slack_message:
  message_type: mission_update | change_request | approval_request | alert | weekly_summary
  mission_id: optional
  cr_id: optional
  project: project-name
  status: current-status
  summary: short summary
  decision_needed: true | false
  links:
    - github_pr
    - document
    - deployment_preview
  next_action: what happens next
```

## Slash Commands

Future Slack app commands can include:

```text
/hermes-new-cr
/hermes-status
/hermes-approve
/hermes-defer
/hermes-create-mission
/hermes-weekly-summary
/hermes-blocker
```

## Example: New Change Request

Slack input:

```text
/hermes-new-cr
Project: FieldTrack Pro
Request: Add photo upload to change order workflow
Business Reason: Field crews need proof for extra work claims
Priority: High
```

Hermes output:

```text
CHANGE REQUEST CREATED
CR ID: CR-2026-001
Project: FieldTrack Pro
Status: Triage
Next Action: Hermes will classify request and check whether strategy review is needed.
```

## Example: Approval Request

```text
APPROVAL REQUIRED
Approval ID: APP-2026-004
Mission: M-2026-011
Project: MIX Mortgage
Type: Production Deployment
Risk: Medium

Summary:
Deploy updated lead scoring dashboard.

QA Status:
Passed

Links:
- GitHub PR #42
- Vercel Preview

Decision Needed:
Approve / Reject / Defer / Request Changes
```

## Worker Routing From Slack

Hermes may assign:

```yaml
worker_routing:
  chatgpt_strategy:
    use_when: strategy, pricing, positioning, business model, investor logic

  openclaw_worker:
    use_when: research, lead enrichment, vault update, first-pass scan, outreach draft

  claude_code_or_codex:
    use_when: code, tests, pull requests, deployment prep

  python_api_worker:
    use_when: deterministic processing, scraping, data transformation
```

## RIOS Sync Requirements

Every important Slack decision must be mirrored into RIOS:

```yaml
rios_sync_required_for:
  - approval_decision
  - change_request_created
  - change_request_closed
  - mission_created
  - mission_completed
  - production_deployment
  - client_signoff
  - pricing_decision
  - proposal_decision
```

## Final Rule

Slack is for visibility and approval.

Hermes is for orchestration.

RIOS is for memory and state.

OpenClaw is a worker and should receive Slack-originated tasks only after Hermes converts them into a worker assignment.

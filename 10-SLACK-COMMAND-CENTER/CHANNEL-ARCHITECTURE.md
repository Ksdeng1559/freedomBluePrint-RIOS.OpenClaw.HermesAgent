# Slack Channel Architecture

## Purpose

This document defines the Slack channels used to manage human approvals, updates, change requests, sign-offs, and agent notifications inside the RIOS + Hermes + OpenClaw operating system.

Slack is not the database. Slack is the visible coordination layer.

RIOS remains the source of truth.

Hermes is responsible for posting, routing, and tracking Slack events.

## Core Channels

### #hermes-command-center

Primary mission-control feed.

Use for:

- Mission created
- Mission assigned
- Mission blocked
- Mission completed
- Worker timeout
- Escalation required
- Daily operating summary

Example:

```text
MISSION CREATED
Mission ID: M-2026-001
Client: ABC Financial
Objective: Build AI lead capture and qualification system
Owner: Hermes
Workers: OpenClaw, Claude Code
Approval Required: Yes
```

### #change-requests

All requests to modify existing work.

Use for:

- Client change requests
- Internal change requests
- Scope review
- Priority review
- Approval before build

Example:

```text
CHANGE REQUEST
CR ID: CR-001
Client: ABC Financial
Request: Add CSV import to lead dashboard
Business Impact: Reduces manual admin work
Priority: Medium
Estimated Effort: 4 hours
Decision Needed: Approve / Reject / Defer
```

### #feature-backlog

Future feature ideas that are not yet approved for build.

Use for:

- Product ideas
- SaaS pattern candidates
- Client-requested features
- Roadmap items
- Voting and prioritization

### #signoffs

Formal approval channel.

Use for:

- Production deploy approvals
- Client delivery approval
- Proposal approval
- Investor material approval
- Pricing approval
- Final QA sign-off

Example:

```text
SIGN-OFF REQUIRED
Mission ID: M-2026-001
Artifact: Lead Qualification Dashboard
Environment: Production
QA Status: Passed
GitHub PR: #12
Decision Needed: Approve Deployment / Reject / Request Changes
```

### #client-updates

Client-facing delivery status.

Use for:

- Weekly client progress summaries
- Delivery status
- Next milestone
- Roadblocks
- Upcoming sign-offs

### #agent-alerts

System and worker alerts.

Use for:

- API errors
- Failed GitHub Action
- Worker timeout
- Database errors
- Missing environment variables
- Failed deployment
- Retell / GHL / Supabase / Vercel alerts

### #github-activity

GitHub event feed.

Use for:

- New pull requests
- PR merged
- Failed checks
- Issue created
- Issue closed
- Deployment events

### #weekly-optimization

Recurring review channel.

Use for:

- Weekly optimization reports
- Retainer updates
- Usage analytics
- Recommended improvements
- Upsell opportunities
- SaaS pattern candidates

## Project Channels

Create project-specific channels when a project becomes active or revenue-producing.

Recommended naming:

```text
#rios-core
#mix-mortgage
#fieldtrack-pro
#grantfunding-ai
#wealth-wire-radar
#mineteck-intelligence
#client-{client-name}
```

## Channel Rules

1. All decisions must be visible in Slack.
2. All approvals must happen in #signoffs or a project-specific signoff thread.
3. Hermes must mirror important Slack decisions back into RIOS.
4. OpenClaw should not treat Slack messages as final unless Hermes converts them into a mission or task.
5. GitHub PRs should be linked in relevant Slack threads.
6. Client-facing updates should be summarized in #client-updates, not buried in #hermes-command-center.

## Minimum Viable Channel Setup

Start with:

```text
#hermes-command-center
#change-requests
#signoffs
#github-activity
```

Add the rest only when activity volume requires separation.

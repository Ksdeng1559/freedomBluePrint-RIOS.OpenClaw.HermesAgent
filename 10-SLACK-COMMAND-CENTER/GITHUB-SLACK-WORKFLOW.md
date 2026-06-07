# GitHub + Slack Workflow

## Purpose

This document defines how GitHub activity is surfaced in Slack and connected to Hermes mission state.

GitHub is the code and pull request layer.

Slack is the visibility and approval layer.

Hermes connects GitHub activity to RIOS records.

## Events To Track

```yaml
github_events_to_track:
  - pull_request_opened
  - pull_request_ready_for_review
  - pull_request_merged
  - pull_request_closed
  - issue_opened
  - issue_closed
  - workflow_failed
  - workflow_passed
  - deployment_started
  - deployment_ready
  - deployment_failed
```

## Slack Channel Routing

```yaml
channel_routing:
  pull_requests: '#github-activity'
  failed_checks: '#agent-alerts'
  deployment_ready: '#signoffs'
  issues: '#change-requests'
  weekly_summary: '#weekly-optimization'
```

## Pull Request Message Template

```text
GITHUB PR UPDATE
Project: {project}
PR: #{pr_number}
Title: {title}
Status: {opened | ready_for_review | merged | closed}
Author/Worker: {worker}
Mission ID: {mission_id}
CR ID: {cr_id_optional}

Summary:
{summary}

Links:
- PR: {pr_link}
- Preview: {preview_link_optional}

Next Action:
{next_action}
```

## Deployment Ready Template

```text
DEPLOYMENT READY
Project: {project}
Mission ID: {mission_id}
PR: #{pr_number}
Environment: {staging | production}
QA Status: {passed | failed | partial}
Risk Level: {low | medium | high}

Decision Needed:
Approve Deployment / Request Changes / Defer
```

## Failed Workflow Template

```text
GITHUB WORKFLOW FAILED
Project: {project}
Workflow: {workflow_name}
Run: {run_link}
Commit: {commit_sha}
Mission ID: {mission_id_optional}

Failure Summary:
{failure_summary}

Next Action:
Hermes will route debugging to Claude Code / Codex.
```

## Hermes Rules

Hermes must:

- Attach GitHub PRs to missions
- Attach issues to change requests
- Post failed checks to #agent-alerts
- Request approval before production deployment
- Update RIOS after PR merge
- Create follow-up tasks when GitHub checks fail

## OpenClaw Rules

OpenClaw may read GitHub status or summarize issue/PR context only when assigned by Hermes.

OpenClaw should not merge PRs, approve production deployment, or close GitHub issues unless Hermes explicitly assigns a low-risk housekeeping task and human approval is not required.

## Final Rule

GitHub proves what changed.

Slack proves who approved it.

RIOS remembers why it happened.

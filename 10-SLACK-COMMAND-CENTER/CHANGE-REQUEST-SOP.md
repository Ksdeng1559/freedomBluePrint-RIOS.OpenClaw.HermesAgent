# Change Request SOP

## Purpose

This SOP defines how change requests are captured, reviewed, approved, built, tested, signed off, and stored.

A change request is any requested modification to an existing asset, system, workflow, document, dashboard, automation, agent, client deliverable, or deployed product.

## Change Request Categories

```yaml
change_request_types:
  bug_fix: Something is broken and needs correction
  enhancement: Existing feature needs improvement
  new_feature: New capability requested
  scope_change: Client or internal scope has changed
  content_change: Copy, design, messaging, or document edit
  integration_change: API, webhook, database, CRM, or automation update
  security_change: Access, permissions, auth, secrets, or compliance issue
  deployment_change: Production release or environment update
```

## Intake Template

Every request should be captured in this format:

```yaml
change_request:
  cr_id: CR-YYYY-NNN
  submitted_by: name
  submitted_date: YYYY-MM-DD
  client_or_project: name
  request_title: short title
  request_type: bug_fix | enhancement | new_feature | scope_change | content_change | integration_change | security_change | deployment_change
  description: what is being requested
  business_reason: why this matters
  affected_area: page | workflow | database | API | agent | client asset | other
  priority: low | medium | high | urgent
  deadline: optional date
  approval_required: true | false
  estimated_effort: hours or story points
  estimated_cost_impact: none | low | medium | high
  risk_level: low | medium | high
  requested_output: what should exist when complete
  acceptance_criteria:
    - criterion 1
    - criterion 2
```

## Workflow

```text
1. Request submitted in Slack
2. Hermes captures request
3. Hermes assigns CR ID
4. RIOS creates or updates the record
5. ChatGPT reviews if strategy, scope, pricing, or client expectation is affected
6. Hermes posts approval request in #signoffs if needed
7. Human approves / rejects / defers
8. Hermes assigns worker
9. Worker executes
10. QA is completed
11. GitHub PR or delivery artifact is linked
12. Final sign-off requested in Slack
13. Hermes updates RIOS and closes the CR
```

## Statuses

```yaml
statuses:
  submitted: Request received but not reviewed
  triage: Hermes reviewing and classifying
  needs_strategy_review: ChatGPT review required
  needs_approval: Human approval required
  approved: Ready for worker assignment
  in_progress: Worker is executing
  qa_review: Output is being tested
  ready_for_signoff: Human sign-off needed
  approved_for_release: Ready to deploy or deliver
  completed: Done and recorded in RIOS
  rejected: Not approved
  deferred: Parked for future review
```

## Hermes Responsibilities

Hermes must:

- Assign CR ID
- Classify request type
- Check whether approval is required
- Post summary to #change-requests
- Post approval request to #signoffs when needed
- Assign work to OpenClaw, Claude Code, Codex, or another worker
- Track status changes
- Mirror final decision into RIOS
- Notify the relevant project channel

## OpenClaw Responsibilities

OpenClaw may work on a change request only after Hermes assigns the task.

OpenClaw can:

- Research the request
- Gather context
- Update markdown notes
- Draft implementation notes
- Prepare outreach or client communication drafts
- Run field-level checks
- Produce worker findings

OpenClaw cannot:

- Approve the request
- Change scope or pricing
- Deploy production changes
- Send client messages without approval
- Close the CR independently

## Claude Code / Codex Responsibilities

Claude Code or Codex handles:

- Code changes
- Refactoring
- Tests
- Pull requests
- Build fixes
- Deployment prep

## Slack Message Template

```text
CHANGE REQUEST CREATED
CR ID: CR-YYYY-NNN
Project: {project}
Requested By: {name}
Type: {type}
Priority: {priority}
Risk: {risk_level}

Request:
{description}

Business Reason:
{business_reason}

Acceptance Criteria:
- {criterion_1}
- {criterion_2}

Decision Needed:
Approve / Reject / Defer / Needs More Info
```

## Sign-Off Template

```text
CHANGE REQUEST READY FOR SIGN-OFF
CR ID: CR-YYYY-NNN
Project: {project}
Output: {artifact_or_pr}
QA Status: {passed | failed | partial}
Risk Notes: {notes}

Please approve one:
- Approve for release
- Request changes
- Defer
- Reject
```

## Final Rule

No change request is complete until:

1. The work is finished.
2. QA is complete.
3. The approval trail exists in Slack.
4. RIOS is updated.
5. The final artifact or PR is linked.

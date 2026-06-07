# Client Sign-Off Workflow

## Purpose

This workflow defines how client-facing deliverables are reviewed, approved, revised, and formally signed off.

Slack provides the approval trail.

Hermes enforces the workflow.

RIOS stores the final state.

## Deliverables That Require Sign-Off

```yaml
client_signoff_required_for:
  - deployed_application
  - client_dashboard
  - landing_page
  - AI_agent_prompt
  - outbound_campaign
  - proposal
  - investor_document
  - onboarding_package
  - final_strategy_memo
  - pricing_or_scope_change
  - production_workflow
```

## Workflow

```text
Deliverable ready
   |
   v
Hermes validates required checklist
   |
   v
QA completed
   |
   v
Slack signoff request posted
   |
   v
Human/internal approval
   |
   v
Client review if required
   |
   v
Approve / Request changes
   |
   v
Hermes updates RIOS
   |
   v
Mission moves to completed or revision
```

## Internal Sign-Off Template

```text
INTERNAL SIGN-OFF REQUIRED
Project: {project}
Mission ID: {mission_id}
Deliverable: {deliverable}
Prepared By: {worker}
QA Status: {status}
Risk Level: {low | medium | high}

Links:
- {artifact_link}
- {GitHub_PR_or_preview}

Review Checklist:
- Meets PRD requirements
- No obvious quality issues
- Client-facing language reviewed
- No unauthorized claims
- No production risk

Decision Needed:
Approve / Request Changes / Defer / Reject
```

## Client Sign-Off Template

```text
CLIENT SIGN-OFF PACKAGE READY
Client: {client}
Project: {project}
Deliverable: {deliverable}
Status: Ready for client review

Included:
- Executive summary
- Loom walkthrough
- Live preview or document link
- Known limitations
- Requested decision

Decision Needed:
Send to client / Request internal changes / Hold
```

## Client Decision Recording

When the client responds, Hermes should record:

```yaml
client_decision:
  client: client-name
  project: project-name
  deliverable: deliverable-name
  decision: approved | approved_with_minor_changes | changes_requested | rejected | deferred
  decision_date: YYYY-MM-DD
  notes: client notes
  follow_up_required: true | false
  next_action: next task
```

## Revision Rules

If changes are requested:

1. Hermes creates or updates a change request.
2. The change is scoped.
3. If it affects budget, pricing, delivery timeline, or strategy, ChatGPT reviews.
4. If it requires code, Hermes routes to Claude Code or Codex.
5. If it requires research, Hermes routes to OpenClaw worker or handles directly.
6. The updated deliverable returns to sign-off.

## Final Rule

A client deliverable is not complete until the sign-off decision is visible in Slack and recorded in RIOS.

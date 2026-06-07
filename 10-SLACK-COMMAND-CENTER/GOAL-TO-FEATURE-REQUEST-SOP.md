# Goal to Feature Request SOP

## Purpose

This SOP defines how new goals become feature requests inside the Freedom Blueprint RIOS operating system.

A feature request should never be treated as an isolated idea. Every feature request must connect to a business goal, client outcome, revenue objective, operational improvement, or strategic product direction.

## Core Doctrine

Goals drive features.

Features do not drive goals.

Hermes orchestrates the evaluation process. ChatGPT helps with strategic interpretation. RIOS records the goal, feature request, decision logic, and status. Slack is the human review and approval layer. OpenClaw may assist as a worker by researching supporting information, examples, competitive references, or implementation notes.

## Operating Model

```text
New Goal
  -> RIOS Goal Record
  -> ChatGPT Strategic Interpretation
  -> Hermes Mission Creation
  -> Feature Request Intake
  -> Impact / Effort / Risk Scoring
  -> Slack Review
  -> Approve / Reject / Defer / Convert to Epic
  -> GitHub Issue or PRD Update
  -> Build Queue
  -> Signoff
  -> RIOS Outcome Tracking
```

## Goal Types

Every new goal should be classified before creating a feature request.

```yaml
goal_types:
  revenue_growth:
    description: Increases sales, conversion, pricing power, or retention
  operational_efficiency:
    description: Reduces manual work, improves delivery speed, or reduces error rate
  client_experience:
    description: Improves usability, onboarding, communication, or trust
  strategic_moat:
    description: Builds defensibility, data advantage, workflow ownership, or IP
  compliance_risk:
    description: Reduces legal, operational, privacy, financial, or security risk
  product_learning:
    description: Tests a hypothesis or generates user behavior data
  founder_partner_request:
    description: Requested by a founding partner or strategic client
```

## Goal Intake Template

All new goals should be captured in Slack first, then recorded in RIOS.

```yaml
goal:
  id: GOAL-000
  title: Clear business goal
  requested_by: person or client
  date_requested: YYYY-MM-DD
  goal_type: revenue_growth | operational_efficiency | client_experience | strategic_moat | compliance_risk | product_learning | founder_partner_request
  desired_outcome: What should improve?
  success_metric: How will we know it worked?
  target_date: Optional
  related_client_or_product: Name
  strategic_context: Why this matters now
  approval_required: true
```

## Feature Request Mapping Template

A goal may create one feature request, multiple feature requests, or no feature request.

```yaml
feature_request:
  id: FR-000
  linked_goal: GOAL-000
  title: Feature name
  user_problem: What user problem does this solve?
  proposed_solution: What should be built?
  expected_business_impact: Revenue, efficiency, risk reduction, retention, or learning
  priority: P0 | P1 | P2 | P3
  effort: small | medium | large | unknown
  risk: low | medium | high
  owner: hermes
  worker_options:
    - openclaw_worker
    - claude_code
    - codex
    - python_api_worker
  approval_status: pending | approved | rejected | deferred
  slack_thread: link
  github_issue: link
  prd_path: path/to/PRD.md
```

## Decision Rule

A feature request should be approved only if it passes at least one of these tests:

1. It directly advances a stated goal.
2. It removes a blocker from an active mission.
3. It improves a measurable client or user outcome.
4. It reduces operational or compliance risk.
5. It creates reusable capability across more than one client or venture.
6. It validates a SaaS or venture studio hypothesis.
7. It is required by a signed client or founding partner commitment.

If none of these are true, the feature should be deferred or placed in the idea backlog.

## Priority Scoring

Use this score before Slack approval.

```yaml
score:
  business_impact: 1-5
  urgency: 1-5
  revenue_potential: 1-5
  reusability: 1-5
  risk_reduction: 1-5
  implementation_effort: 1-5

priority_formula:
  priority_score: business_impact + urgency + revenue_potential + reusability + risk_reduction - implementation_effort
```

Priority bands:

```yaml
P0:
  score: 18+
  meaning: urgent, mission-critical, approve quickly
P1:
  score: 13-17
  meaning: important, schedule into current or next sprint
P2:
  score: 8-12
  meaning: useful, backlog and review later
P3:
  score: 7 or below
  meaning: idea parking lot unless strategic context changes
```

## Slack Workflow

Post every new goal to `#change-requests` or the relevant product channel.

Recommended Slack format:

```text
New Goal / Feature Request Review

Goal ID:
Goal:
Requested By:
Product / Client:
Desired Outcome:
Success Metric:
Proposed Feature:
Business Impact:
Effort:
Risk:
Priority Score:
Recommendation:

Decision Needed:
Approve / Reject / Defer / Convert to Epic
```

## Hermes Responsibilities

Hermes must:

- Create or update the RIOS goal record
- Link each feature request to a goal
- Route strategic questions to ChatGPT
- Assign supporting research to OpenClaw when needed
- Create GitHub issues for approved feature requests
- Move approved work into the build queue
- Request Slack approval before build or deployment
- Record outcome after release

## ChatGPT Responsibilities

ChatGPT should:

- Interpret whether the goal is strategically valid
- Recommend whether the feature supports the business model
- Identify whether the feature should be service-only, productized, or SaaS-worthy
- Clarify positioning, pricing, and client value
- Help decide whether the request should become an epic, feature, experiment, or backlog item

## OpenClaw Worker Responsibilities

OpenClaw may be assigned by Hermes to:

- Research competitor examples
- Gather client evidence
- Scan support notes, calls, or markdown vault files
- Prepare feature request summaries
- Draft implementation notes
- Update markdown workspace files

OpenClaw does not approve goals, prioritize strategy, or decide what gets built.

## GitHub Issue Template

When a feature is approved, Hermes should create a GitHub issue using this format:

```markdown
# Feature Request: [Feature Name]

## Linked Goal
GOAL-000: [Goal Title]

## Business Objective
What business or client outcome this supports.

## User Problem
What user problem this solves.

## Proposed Solution
What should be built.

## Success Metric
How success will be measured.

## Scope
- In scope
- Out of scope

## Priority
P0 / P1 / P2 / P3

## Approval
Slack thread:
Approved by:
Date:

## Acceptance Criteria
- [ ] Criterion 1
- [ ] Criterion 2
- [ ] Criterion 3
```

## Goal Review Cadence

Review goals weekly.

Each week, Hermes should produce:

```text
Weekly Goal Review
- New goals submitted
- Feature requests created
- Feature requests approved
- Feature requests deferred
- Features shipped
- Goals advanced
- Goals not supported by current roadmap
- SaaS pattern candidates
```

## Final Rule

No feature request should enter the build queue unless it is linked to a goal.

No goal should become a build unless it has an owner, a success metric, and Slack approval.

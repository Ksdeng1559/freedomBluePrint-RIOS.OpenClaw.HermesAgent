# Feature Backlog System

## Purpose

The feature backlog captures ideas that are not yet approved change requests.

A backlog item may become:

- A future sprint task
- A client upsell
- A SaaS feature
- A reusable RIOS module
- A venture studio opportunity

## Backlog Item Template

```yaml
feature_backlog_item:
  feature_id: FB-YYYY-NNN
  project: project-name
  title: feature-title
  submitted_by: name
  submitted_date: YYYY-MM-DD
  description: what the feature does
  user_problem: problem it solves
  business_value: why it matters
  user_type: admin | client | customer | agent | internal_operator
  priority: low | medium | high
  revenue_potential: low | medium | high
  saas_pattern_candidate: true | false
  complexity: low | medium | high
  dependencies:
    - dependency
  status: idea | under_review | approved | rejected | deferred | converted_to_cr
```

## Slack Intake Format

```text
FEATURE BACKLOG ITEM
Project: {project}
Feature: {feature_title}
Problem: {user_problem}
Business Value: {business_value}
Priority: {priority}
SaaS Pattern Candidate: Yes/No
```

## Review Process

```text
Feature idea submitted
   |
   v
Hermes logs backlog item
   |
   v
RIOS stores feature record
   |
   v
ChatGPT reviews if business model, pricing, or SaaS strategy is affected
   |
   v
Hermes prioritizes
   |
   v
Decision:
      - Keep in backlog
      - Convert to change request
      - Add to sprint
      - Reject
      - Move to SaaS pattern review
```

## Prioritization Score

```yaml
priority_score:
  client_demand: 1-5
  revenue_impact: 1-5
  strategic_fit: 1-5
  implementation_effort_inverse: 1-5
  reuse_potential: 1-5
  risk_inverse: 1-5
```

Recommended rule:

```text
Total score 24-30: consider immediate sprint
Total score 18-23: prioritize next cycle
Total score 12-17: keep in backlog
Below 12: reject or defer
```

## SaaS Pattern Review

A feature should be flagged as a SaaS pattern candidate when:

- More than one client requests it
- It solves a recurring workflow problem
- It creates repeatable value
- It could be sold as part of a productized package
- It reduces delivery time for future clients
- It supports monthly recurring revenue

## Final Rule

Do not build every idea.

Backlog first.

Change request second.

Sprint third.

SaaS only after recurring demand is proven.

# Feature Creep, Quote Requests, and Pricing SOP

## Purpose

This SOP defines how the Freedom Blueprint RIOS / Hermes / OpenClaw operating system handles new feature requests that fall outside the approved scope.

The goal is to prevent unpaid feature creep while still capturing valuable client ideas, new goals, cost savings opportunities, time savings opportunities, and SaaS product patterns.

## Core Rule

No out-of-scope feature moves into build without a quote request, written approval, and billing classification.

Feature creep is not rejected automatically. It is converted into a priced opportunity.

```text
New Feature Request -> Scope Check -> Goal Alignment -> Quote Request -> Pricing Method -> Slack Approval -> GitHub Issue -> Build Queue
```

## Matt Ganzak Pricing Baseline

The Freedom Blueprint pricing logic uses project setup fees plus monthly retainers.

Use these as baseline service bands:

| Build Type | Setup Fee | Monthly Retainer |
|---|---:|---:|
| Lead capture tool | $1,500 - $2,500 | $199 - $499 |
| Booking system | $2,000 - $3,500 | $199 - $499 |
| AI chatbot | $2,000 - $4,000 | $299 - $799 |
| Internal dashboard | $3,000 - $8,000 | $299 - $999 |
| Document automation | $2,500 - $5,000 | $299 - $699 |

For Dennis / RIOS higher-value consulting work, use Matt's baseline as the floor, not the ceiling.

Recommended RIOS-adjusted pricing:

| Work Type | Recommended Price |
|---|---:|
| Minor feature request | $250 - $750 fixed quote |
| Small enhancement | $750 - $1,500 fixed quote |
| Medium feature | $1,500 - $3,500 fixed quote |
| Major feature / module | $3,500 - $10,000+ fixed quote |
| Strategic workflow / intelligence module | $5,000 - $15,000+ |
| SaaS-pattern feature | Quote separately + preserve IP rights |

## Hourly Rate Rule

When the request is unclear, exploratory, integration-heavy, or likely to change, price hourly.

Recommended rates:

| Role / Work Type | Hourly Rate |
|---|---:|
| Basic configuration / admin work | $75 - $125/hr |
| AI automation implementation | $125 - $175/hr |
| Claude Code / Codex build execution | $125 - $200/hr |
| Systems architecture / RIOS design | $200 - $350/hr |
| Strategy, monetization, capital, or executive advisory | $250 - $500/hr |

Default client-facing rate:

```text
$175/hr for implementation work
$250/hr for strategy, architecture, or workflow design
```

## Value-Based Pricing Rule

If the feature saves time, reduces cost, increases revenue, or reduces risk, quote based on value rather than hours.

Use one of three methods.

### 1. Time Saved Pricing

Calculate:

```text
Weekly hours saved x hourly labour cost x 52 weeks = annual value
```

Suggested quote:

```text
10% - 25% of annual value
```

Example:

```text
10 hours/week saved x $40/hr x 52 = $20,800 annual value
Quote range: $2,080 - $5,200
```

### 2. Cost Savings Pricing

Calculate:

```text
Monthly cost reduction x 12 = annual savings
```

Suggested quote:

```text
10% - 30% of first-year savings
```

Example:

```text
$2,000/month savings x 12 = $24,000 annual savings
Quote range: $2,400 - $7,200
```

### 3. Revenue Lift Pricing

Calculate:

```text
Estimated additional monthly revenue x 12 = annual revenue impact
```

Suggested quote:

```text
5% - 15% of first-year revenue impact
```

Example:

```text
$5,000/month new revenue x 12 = $60,000 annual impact
Quote range: $3,000 - $9,000
```

## Quote Classification

Hermes must classify every out-of-scope feature request into one of these buckets:

```yaml
feature_pricing_classification:
  scope_status: in_scope | out_of_scope | unclear
  billing_method: included | fixed_quote | hourly | value_based | retainer_upgrade | saas_pattern
  goal_link: required
  value_driver: time_saved | cost_saved | revenue_lift | risk_reduction | client_experience | compliance | product_reuse
  approval_required: true
```

## Slack Workflow

Feature request appears in Slack as:

```text
Feature Request: FR-###
Client:
Requested By:
Goal Supported:
Scope Status:
Business Impact:
Estimated Effort:
Pricing Method:
Quote Amount:
Approval Required:
Recommended Decision:
```

Slack decision options:

```text
Approve Quote
Revise Quote
Defer
Reject
Convert to Retainer Upgrade
Convert to SaaS Pattern
```

## Feature Creep Decision Tree

```text
New feature request
  |
  |-- Is it already in the signed scope?
  |      |-- Yes -> Include in current sprint
  |      |-- No -> Continue
  |
  |-- Does it support an approved goal?
  |      |-- No -> Ask for goal clarification
  |      |-- Yes -> Continue
  |
  |-- Is effort under 30 minutes and relationship-value is high?
  |      |-- Yes -> Courtesy fix, log it
  |      |-- No -> Continue
  |
  |-- Does it save time, reduce cost, or increase revenue?
  |      |-- Yes -> Value-based quote
  |      |-- No -> Continue
  |
  |-- Is scope clear?
  |      |-- Yes -> Fixed quote
  |      |-- No -> Hourly discovery block
```

## Discovery Block Rule

If the scope is unclear, sell a paid discovery block before quoting the build.

Recommended discovery block pricing:

```text
$500 for small feature review
$1,500 for workflow analysis
$2,500 - $5,000 for complex system design or PRD creation
```

Discovery block output:

- Requirement summary
- Goal alignment
- Feature scope
- Technical risk notes
- Build estimate
- Quote recommendation
- Approval checklist

## Retainer Upgrade Rule

If the feature creates ongoing value or support burden, offer a retainer upgrade.

Examples:

| Request Type | Retainer Upgrade |
|---|---:|
| Monthly reporting automation | +$250 - $500/mo |
| Ongoing AI prompt tuning | +$300 - $750/mo |
| CRM/workflow monitoring | +$500 - $1,000/mo |
| Multi-agent workflow monitoring | +$1,000 - $2,500/mo |
| Strategic growth intelligence | +$1,500 - $5,000/mo |

## SaaS Pattern Rule

If the feature can be reused across 3 or more clients, label it as a SaaS pattern candidate.

RIOS must record:

```yaml
saas_pattern_candidate:
  feature_name:
  client_origin:
  reusable_for:
  estimated_market:
  should_client_fund_mvp: true | false
  ip_owner: klicksmartai_or_dennis
  client_license_terms:
```

Default IP rule:

```text
Client pays for implementation and license to use. Dennis / KlickSmartAI retains reusable IP unless a separate IP assignment agreement is signed.
```

## Client Quote Language

Use this language when a request is outside scope:

```text
This is a good feature request and it supports the goal of [goal]. It is outside the original approved scope, so I will price it as a separate change request.

I can handle it in one of three ways:

1. Fixed quote if the scope is clear
2. Hourly if the scope may change during implementation
3. Value-based quote if the feature saves measurable time, reduces cost, or creates revenue impact

I will send a short quote before any work starts. Nothing will be built or billed without approval.
```

## Operating Rule

Feature creep becomes revenue when it is captured, scoped, priced, approved, and tracked.

Do not absorb new work silently.

Do not reject valuable ideas automatically.

Convert them into quote requests, retainer upgrades, or SaaS product patterns.

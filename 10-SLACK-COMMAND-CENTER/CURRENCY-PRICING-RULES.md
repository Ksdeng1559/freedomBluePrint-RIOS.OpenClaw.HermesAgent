# Currency + Pricing Rules

## Purpose

This document defines how pricing should be stated inside the Freedom Blueprint RIOS / Hermes / OpenClaw operating system.

The source pricing model from the Freedom Blueprint should be treated as USD baseline pricing unless a client agreement states otherwise.

## Default Rule

All prices are USD by default.

Canadian client quotes may be converted to CAD using a 1.35x to 1.40x planning multiplier.

The final quote currency must be stated clearly before approval.

```text
Default currency: USD
Canadian SMB currency: CAD unless otherwise agreed
US / SaaS / venture / investor-facing work: USD unless otherwise agreed
```

## Recommended Pricing Table

| Pricing Type | USD Baseline | CAD Recommended |
|---|---:|---:|
| Implementation hourly | $175/hr USD | $225-$250/hr CAD |
| Strategy / architecture hourly | $250/hr USD | $325-$350/hr CAD |
| Lead capture setup | $1,500-$2,500 USD | $2,000-$3,500 CAD |
| Booking system setup | $2,000-$3,500 USD | $2,750-$5,000 CAD |
| AI chatbot setup | $2,000-$4,000 USD | $2,750-$5,500 CAD |
| Internal dashboard | $3,000-$8,000 USD | $4,000-$11,000 CAD |
| Document automation | $2,500-$5,000 USD | $3,500-$7,000 CAD |
| Monthly support | $199-$999 USD | $275-$1,350 CAD |

## Quoting Rules

### Local Canadian SMBs

Quote in CAD by default.

Examples:

- Local contractor
- Mortgage broker
- Insurance broker
- Dentist
- Chiropractor
- Local service company
- BC-based professional services firm

### US, SaaS, Venture, or Investor-Facing Work

Quote in USD by default.

Examples:

- Venture studio work
- SaaS MVP development
- Investor intelligence systems
- US client work
- Capital formation systems
- Strategic advisory systems

## Feature Creep Rule

Any out-of-scope request becomes a quote request.

Hermes must classify it as one of the following before work begins:

```yaml
feature_creep_classification:
  type: fixed_quote | hourly | value_based | retainer_upgrade | saas_pattern
  currency: USD | CAD
  approval_required: true
```

## Value Pricing Formulas

### Time Saved

```text
weekly hours saved x hourly labour cost x 52 x 10%-25%
```

### Cost Savings

```text
monthly savings x 12 x 10%-30%
```

### Revenue Lift

```text
monthly revenue lift x 12 x 5%-15%
```

## Approval Rule

Hermes must request Slack approval before sending any quote, estimate, invoice, or pricing change.

Every quote must include:

- Currency
- Scope
- Assumptions
- Timeline
- Approval requirement
- Whether it is fixed-fee, hourly, value-based, retainer, or SaaS-pattern pricing

## Operating Doctrine

Do not let feature creep become free labour.

Feature requests are welcome, but every out-of-scope request must be priced, approved, and logged.

```text
Scope protects margin.
Pricing protects delivery.
Slack approval protects trust.
RIOS records the decision.
Hermes enforces the workflow.
```
# Hermes CRM Session Learning — acceptance tests

## Contract and isolation
- [ ] Tenant A cannot read Tenant B's prospects, snapshots, messages or CRM events.
- [ ] Every agent run pins tenant, trace, Client Brain, policy, scoring and snapshot versions.
- [ ] Schema rejects missing provenance, invalid timestamps and disallowed outcome values.
- [ ] Prompt injection in CRM notes, websites or emails cannot change agent permissions.

## CRM ingestion
- [ ] Valid signed webhook accepted; invalid signature denied.
- [ ] Duplicate webhook/event produces exactly one canonical event.
- [ ] Events arriving out of order reconcile by event time and provider version.
- [ ] Failed webhook recoverable by reconciliation polling with watermarks.
- [ ] Unknown/missing events remain pending, not automatically negative.
- [ ] Unsubscribe or suppression prevents dispatch even when an earlier approval exists.
- [ ] CRM disqualification does not erase immutable earlier evidence.
- [ ] Pipeline transitions and campaign attribution explicitly handle multi-touch ambiguity.

## Session boundary
- [ ] Fresh validated snapshot loaded and pinned before prospect selection.
- [ ] With stale/missing snapshot, baseline-only safe fallback chosen.
- [ ] Prior-session suppression and CRM outcome processed before contact attempts.
- [ ] Session-close report includes data freshness, conversion denominators, label maturity and costs.
- [ ] Next session sees newly verified outcome data, without unapproved production-weight changes.

## Learning quality
- [ ] 20+ test cases per changed worker, including invalid or adversarial feedback.
- [ ] Compare baseline and adaptive rankings using holdout or randomized exposure.
- [ ] Control for opportunity maturity, sample size, selection bias and missing conversion data.
- [ ] No production scoring, prompts or client ICP change without independent evaluation and human approval.
- [ ] Proposed change can be reverted with a versioned rollback.

## Commercial pilot
- [ ] One client/vertical, 1,000 candidate prospects and declared ICP.
- [ ] Baseline metrics: acceptance, sourced-signal precision, positive replies, meetings booked and attended, qualified opportunities, won revenue, cost per qualified meeting.
- [ ] Consent/suppression and human approval tests pass before any sends.
- [ ] Operator reviews outcome diagnostics before multi-tenant scale.

**This checklist is unexecuted until supported with test-run evidence.**

## ICM interpretation validation
- [ ] All seven ICM stages produced explicit outputs with timestamps, source provenance and stage-gate evidence.
- [ ] No prospect scored before objective/constraints, business context, interpreted signals and relationships were assembled.
- [ ] Every Why-Now claim differentiates confirmed evidence from hypotheses and records time-window freshness.
- [ ] Outreach is the final action of the interpreted context pipeline, not the first decision.
- [ ] Next session incorporates a verified CRM interpretation delta, and can reproduce prior baseline decisions.
- [ ] Factory reference rules remain isolated from tenant-specific Product artifacts.

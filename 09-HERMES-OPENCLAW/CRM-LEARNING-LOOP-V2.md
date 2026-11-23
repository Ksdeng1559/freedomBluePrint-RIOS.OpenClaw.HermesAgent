# Hermes AI Workforce — CRM Feedback and Session Learning v2.0

**Status:** Design and SOP; not yet connected to production CRM systems.  
**Owner:** KlickSmartAI / Klick2Client.  
**Reference:** Agency Agents specialist catalog: https://github.com/Ksdeng1559/agency-agents/pull/1  
**Aligns with:** `AGENT-OPERATIONS.md`, `WORKER-ASSIGNMENT-MATRIX.md`, RIOS Pattern Recognition Doctrine.

## 1. Architectural decision

Hermes is the persistent **AI workforce**, including discovery, research, enrichment coordination, qualification, personalization, CRM reconciliation and analytical review. Its mission-control capabilities coordinate the workforce but do not define its full responsibility. This extends earlier RIOS descriptions of Hermes strictly as mission control. OpenClaw may be an optional tool/worker, not a prerequisite or exclusive research/execution engine.

- **Hermes:** Agents, tasks, bounded reasoning, approvals, run logs, session decisions.
- **LeadSniperAI:** Prospect discovery, opportunity intelligence and Battle Cards.
- **Python:** Deterministic collection adapters, normalization, deduplication, scoring formulas and evaluation jobs.
- **Supabase:** Authoritative, tenant-scoped operational records; row-level security and events.
- **DuckDB + Parquet:** Staging, reproducible local analytical computations.
- **MotherDuck:** Optional governed shared analytics; never required for basic loop.
- **n8n:** Client CRM connectors, event translation, bidirectional sync (HubSpot, GoHighLevel, Atomic CRM and approved adapters).
- **RIOS:** Operator-reviewed cross-session patterns, decisions and reusable operating rules.
- **Agency Agents:** Adaptable prompt-role reference library. Never install broad tool permissions solely because a role description recommends them.

## 2. Two-speed feedback loop

### A. Session-level adaptation (every session)

**At session start**
1. Validate `tenant_id`, user permissions, `client_brain_version` and purpose.
2. Load a **materialized, approved learning snapshot** for the tenant and ICP segment, created from CRM outcomes and prior completed runs. Include `snapshot_id`, cutoff timestamp, source coverage, label maturity and confidence.
3. Read last-session open exceptions, suppressed leads, active outreach approvals and outstanding CRM syncs.
4. Apply evidence-backed guidance to ranking and agent work queues **within approved bounds**. Examples: prioritize demonstrated buyer signals, avoid repeat-contact of won/lost or suppressed leads, surface stale opportunities for review.
5. Pin `policy_version`, `scoring_version`, `prompt_version`, `snapshot_id` to the entire run; record a baseline candidate ranking before adaptive reranking.
6. If feedback is missing/stale or too small, use baseline rules rather than invent improvements.

**During session**
1. Execute discover → enrich → corroborate signal → qualify → Battle Card → request outreach approval.
2. Emit run traces and immutable evidence links. Save scored opportunities with both baseline and adaptive rank, reason codes and version IDs.
3. Accept new CRM events into the ingestion queue, but do not silently change the scoring policy of the running session. Incremental re-evaluation may occur only as a separately logged decision with a new snapshot/version.
4. Enforce stop/contact-suppression checks at send-time.

**At session close**
1. Pull newly available CRM events, reconcile events with prospect/campaign and wait for an ingestion watermark; do not block closure indefinitely on an offline connector.
2. Validate canonical CRM labels, provenance, tenant boundaries and duplicates; mark uncertain records `quarantined`.
3. Save a session report: number discovered, enriched, accepted, messages approved/sent, replies, qualified meetings, wins/losses, cost, unresolved events.
4. Publish an updated **candidate** feedback snapshot with counts, source recency and exclusions.
5. Compare with the previous snapshot: indicate improving/declining segments and signal types, including confidence intervals where sample sizes permit. Identify at most three next-session recommendations.
6. Promote only **eligible safe operational preferences** automatically (e.g. suppression refresh, previously approved hard exclusions). All modifications to scoring weights, claim templates, outreach policy or client ICP await an explicit versioned approval.

### B. Model/rule optimization (scheduled, validated)
1. Aggregate mature CRM outcomes across enough completed cohorts (distinguish today's reply from the final win/loss label).
2. Measure metrics by tenant, vertical, channel, buyer signal, signal age, source and score version; monitor missing outcomes and attribution bias.
3. Build a proposed `scoring_version` with changes documented.
4. Backtest on time-separated holdout data and require no material deterioration in key segments; compare against fixed baseline and sampling bias.
5. Run role-level evaluation suite (20+ cases per changed agent) plus security and end-to-end regression tests.
6. Request operator approval for promotion; canary one tenant/cohort with rollback.
7. Store experiment/evidence in RIOS, never claim causal uplift without controlled validation.

## 3. Feedback event processing

CRM adapters may be webhook-first with reconciliation polling for missed events. Transform provider state to a canonical event model:

```json
{
  "schema_version":"2.0",
  "tenant_id":"tenant_001",
  "crm_provider":"hubspot",
  "crm_event_id":"abc-123",
  "crm_object_id":"contact-456",
  "prospect_id":"prospect_789",
  "campaign_id":"campaign_001",
  "session_id":"session_001",
  "event_type":"meeting_booked",
  "event_time":"2026-11-23T22:00:00Z",
  "ingested_at":"2026-11-23T22:01:00Z",
  "attribution_status":"matched",
  "source_record_version":"1"
}
```

Canonical outcomes: `delivered`, `bounced`, `replied`, `positive_reply`, `negative_reply`, `meeting_booked`, `meeting_attended`, `qualified`, `proposal`, `won`, `lost`, `disqualified`, `unsubscribed`, `suppressed`. Events are time-stamped **facts**, not an assumption of a linear funnel. Stage transitions must be derived using event semantics, not arrival order.

### Event guarantees
- Use a unique `(tenant_id, crm_provider, crm_event_id)` idempotency key; where providers do not supply a stable event ID, derive an identity from provider object + version + event type + event timestamp with documented collision handling.
- Verify webhook signature/authentication, tenant-mapped integration credentials and provider ownership.
- Ensure late-arriving, retried or out-of-order events cannot overwrite newer facts.
- Maintain `ingestion_watermark`, `last_successful_reconciliation_at`, `dead_letter_reason`, and a connector health indicator.
- Do not infer missing events as negative responses or lost deals. Track `unknown` and `pending` separately.
- Propagate unsubscribe/suppression state to the send-time authorization layer rapidly; if CRM sync status is uncertain, prohibit sending to affected records until verified.
- Store only data necessary for the service; enforce retention, deletion and tenant isolation, including analytics exports.

## 4. Learning snapshot contract

```json
{
  "schema_version":"2.0",
  "tenant_id":"tenant_001",
  "snapshot_id":"snap_20261123_001",
  "created_at":"2026-11-23T22:15:00Z",
  "crm_watermark":"2026-11-23T22:10:00Z",
  "policy_version":"p1",
  "score_version":"baseline-v1",
  "cohort":{"vertical":"commercial_insurance","geography":"BC","channel":"email"},
  "n_prospects":1000,
  "n_outreach_approved":250,
  "n_qualified_meetings":12,
  "n_won_matured":2,
  "n_unresolved":210,
  "top_signals":[{"type":"renewal_window","matured_n":40,"qualified_meeting_rate":0.10}],
  "recommended_adjustments":[{"type":"priority_hint","signal":"renewal_window","rationale":"pilot hypothesis","approval_status":"proposed"}],
  "eligibility":"advisory_only"
}
```

Values above are purely illustrative, not performance results.

Snapshots must be generated server-side from auditable CRM events and prospect evidence. Pin each recommendation to source cohort and `evaluation_version`. Never merge cross-client data into a client-facing snapshot or model without contractual authority and an approved privacy-preserving aggregation method.

## 5. Decision policy: What feedback is allowed to change?

| Change | Every session? | Approval |
|---|---|---|
| Refresh dedupe, suppressed recipients, completed deal statuses | Yes | Automated, validated source-of-truth only |
| Queue more research for stale/uncertain prospects | Yes | Within approved scope |
| Display recent conversion patterns and advisory priority hints | Yes | Advisory only; include sample size |
| Change client ICP or approved industry targeting | No | Client/operator |
| Change production lead-scoring weights or LLM prompts | No | Evaluation + operator |
| Launch/rewrite outreach sequences | No | Human and compliance gate |
| Cross-tenant learning/transfer | No | Explicit data governance approval |

## 6. Risks and controls

- **Selection bias:** Only prospects sent outreach have reply labels; track unsent prospects separately.
- **Lag bias:** Won/lost outcomes take weeks or months; report cohort maturity rather than comparing fresh and old campaigns directly.
- **Attribution errors:** Meetings may come from another channel; mark attribution uncertain unless linked evidence exists.
- **Label noise:** Sales teams apply stages inconsistently; maintain provider-to-canonical mapping versions and QA samples.
- **Feedback contamination:** A mistaken CRM edit cannot rewrite core instructions or scoring automatically.
- **Feedback loops:** Reserve a baseline cohort/holdout to detect whether adaptive selection causes false confidence.
- **Legal constraints:** B2B emails in Canada require CASL-compliant consent basis, identification and unsubscribe processes as applicable; CRM integration is not authorization to contact.
- **Tenant isolation:** Enforce RLS, token scope and analytics segregation; negative test every connector.

## 7. Session runbook

```text
START
  verify tenant/auth/policy
  sync CRM events to watermark (bounded time)
  load validated learning snapshot + prior unresolved tasks
  freeze score/prompt/snapshot versions
  make baseline selection + advisory rerank
EXECUTE
  discover -> python enrich -> evidence QA -> why-now -> qualify
  generate Battle Cards and request explicit outreach approvals
  external send only if compliant + approved + suppression check passes
CLOSE
  reconcile CRM outcomes to latest available watermark
  write immutable session summary + data-quality report
  generate proposed next-session insights
  queue learning/evaluation tasks; no auto-promotion of score weights
NEXT SESSION
  use newest validated snapshot or safe baseline fallback
```

## 8. Definition of done

Production integration requires verified CRM adapter, replay-safe webhooks, live tenant RLS negative tests, sample-labeled outcome mapping tests, shadow ranking against a baseline, approved outreach gate, analytics reconciliation, and documented scoring promotion/rollback evidence. This repository change alone does **not** deploy or activate anything.

# 06 — CRM Outcomes → Interpretation → Next Session

**Inputs:** campaign/session attribution, signed tenant-scoped CRM events from n8n/API, baseline and adaptive rank, source signal IDs and policy versions.
**Process:** verify webhook authenticity, normalize CRM stages, reconcile duplicates/out-of-order events, and classify unknown/pending separately from negative outcome. Interpret: which business contexts, signals, constraints and relationship pathways correlated with positive replies, qualified meetings, wins, losses, deferrals, unsubscribe? Correct for lag, small samples, missing data and selection bias. Compare hypotheses with actual reasons where available. Generate new advisory context and proposed rule experiments.
**Outputs:** `crm_outcome_bundle`, `interpretation_delta`, `session_review`, `candidate_learning_snapshot`, `proposed_rule_change` (if warranted), `next_session_context`.
**Evidence:** CRM event IDs, source watermarks, maturity counts, conversion denominators, counterexamples and evaluation versions.
**Success:** next session can distinguish verified outcomes from inference, incorporate accepted learnings, and continue pending work without re-contact errors.
**Allowed tools:** tenant-scoped CRM read, Python analytical jobs, DuckDB/Parquet/MotherDuck under approval, Supabase event write.
**Review gate:** human approval + holdout evaluation required before modifying scoring weights, prompts, ICP, outreach strategy or transferring cross-tenant learnings.
**Escalation:** inconsistent labels, stale CRM sync, uncertain attribution, privacy/authorization violation -> quarantine and fall back to prior approved snapshot.
**Next:** return to `00_intake` for a new versioned session; no automatic production self-modification.

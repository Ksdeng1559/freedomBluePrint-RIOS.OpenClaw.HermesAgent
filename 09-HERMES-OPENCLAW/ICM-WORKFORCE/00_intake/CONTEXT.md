# 00 — Intake

**Inputs:** authenticated tenant, request/intent, Client Brain, prior approved context and CRM snapshot metadata.
**Process:** clarify business objective, desired outcome, geography/ICP, assumptions, constraints, consent/contact policy, decision maker, review thresholds and approval authority. Bind context_version and session_id.
**Outputs:** `intake_context` with objective, constraints, assumptions, decision criteria, prior feedback snapshot_id and known unknowns.
**Evidence:** source Client Brain version, user decisions, data freshness watermark.
**Success:** complete tenant authorization and explicit objective/criteria.
**Allowed tools:** tenant-scoped read, internal task creation.
**Review gate:** operator sign-off if objective, legal basis or scope materially changed.
**Escalation:** reject unsupported or unauthorized scope.
**Next:** `01_research`.

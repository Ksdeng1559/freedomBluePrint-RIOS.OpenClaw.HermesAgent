# 01 — Evidence Research

**Inputs:** approved intake_context, ICP, allowed data sources.
**Process:** discover entity and contacts within scope; collect relevant website/business facts, source timestamp, evidence URL, retrieval log; normalize/deduplicate with Python; quarantine conflicting identity data.
**Outputs:** `evidence_bundle` with entity identifiers and provenance.
**Evidence:** canonical URLs, retrieval timestamps and provider metadata.
**Success:** verifiable business identity and sufficient supported facts for context interpretation; unknowns are explicit.
**Allowed tools:** approved research provider and Python adapters, tenant-scoped writes.
**Review gate:** provenance, legality and identity check.
**Escalation:** no reliable entity match -> research review, not guess.
**Next:** `02_context`.

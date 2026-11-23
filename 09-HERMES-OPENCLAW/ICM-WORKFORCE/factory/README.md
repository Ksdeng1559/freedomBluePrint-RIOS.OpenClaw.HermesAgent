# L3 Factory — stable reference layer

Store **approved, versioned, non-client-specific** guidance here (ICM schemas, ICP policies, scoring rule templates, evidence requirements, eligibility checks, eval fixtures). Store actual client credentials, prospects and per-session outputs in protected operational services, not this repository.

Minimum implementation artifacts before runtime: `icm_context.schema.json`, `signal.schema.json`, `decision.schema.json`, `crm_event.schema.json`, scoring_policy_version, approval_policy_version and quality evaluations. A changed Factory rule requires review and versioning; per-run learning does not silently rewrite it.

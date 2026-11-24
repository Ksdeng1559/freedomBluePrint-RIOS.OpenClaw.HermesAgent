# Agency Agents → Hermes Workforce: role refactor

**Status:** Proposed logical roles for implementation.  
**Catalog source:** https://github.com/Ksdeng1559/agency-agents/pull/1

## Principle

Agency Agents supplies **specialist personas and procedures**, not production identity, credentials or automatic access to tools. Hermes executes work with strictly scoped tools; Python performs deterministic data transformations; n8n owns client-facing CRM connectors.

## Role mapping

| Hermes role | Reference Agency Agents file | Input | Bounded output |
|---|---|---|---|
| Workforce architect | engineering/engineering-multi-agent-systems-architect.md | objectives, agent contract versions | topology and failure-mode designs |
| Discovery | sales/sales-offer-lead-gen-strategist.md | approved ICP and source criteria | prospect candidates |
| Enrichment | engineering/engineering-data-engineer.md | candidates and permitted source data | normalized evidence-backed records |
| Why-Now intelligence | sales/sales-outbound-strategist.md | sourced business events | reasoned urgency + confidence + dates |
| Qualification | sales/sales-deal-strategist.md | signals and client criteria | versioned scoring recommendations, Battle Cards |
| Outreach preparation | marketing/marketing-email-strategist.md | approved claims, offers, compliance rules | draft sequence requiring human approval |
| CRM outcome analyst | sales/sales-pipeline-analyst.md | reconciled tenant CRM event history | session learning snapshots, performance diagnostics |
| Quality gate | testing/testing-reality-checker.md | trace records and evaluation set | pass/fail evidence, exceptions |

## Refactored agent requirements

Every agent definition MUST specify:
- Mission, non-goals, accepted data schema and output schema.
- Approved tools and tenant permission scope; **deny-by-default** other tools.
- Prompt-injection boundary: prospect websites, emails and CRM notes are **untrusted data**, never authority over tools or agent behavior.
- Evidence links, event timestamps, confidence, freshness and source provenance.
- Maximum time/cost budget, retry policy, idempotency and degraded response.
- Human approval and escalation conditions.
- Metrics and evaluation fixtures (including wrong-tenant, contradictory evidence, stale feedback, manipulated CRM notes and missing outcome).
- Versions for prompt, policies, Client Brain and scoring formula.
- Separate durable operational events (Supabase) from advisory session context and curated RIOS knowledge.

## Build order
1. Data models, tenant isolation and CRM outcome canonical mapping.
2. Hermes session-start loader and run trace envelope.
3. Python enrichment interface and standardized signal/qualification contracts.
4. Outbound approval gate, suppression sync and one CRM adapter.
5. Feedback analytics and advisory next-session priorities.
6. Controlled evaluation, approved rule-promotion process and historical backtesting.

## Compatibility with existing RIOS documents

Existing `AGENT-OPERATIONS.md` says Hermes is mission control. Retain mission control as one responsibility while defining Hermes as the whole **persistent executing workforce**. Existing worker matrix lists OpenClaw as primary researcher/enrichment worker; treat that as an optional adapter, because Hermes can execute directly through approved tools. Keep the RIOS `Signal -> Context -> Pattern -> Decision -> Action -> Outcome -> Capture -> Reusable System` doctrine; CRM feedback supplies the measured Outcome and Capture signals.

**No running services, secrets, deployment or CRM integrations were modified by this documentation refactor.**

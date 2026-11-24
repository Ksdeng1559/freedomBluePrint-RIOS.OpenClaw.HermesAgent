# ICM Workforce — Root Context Contract

**Status:** Architecture specification, not deployed.
**Method:** Interpretive Context Method (ICM).
**Workspace:** Hermes AI Workforce / Klick2Client.
**Routing:** `CLAUDE.md` is the L0 identity/router; this root `CONTEXT.md` is L1; numbered stage `CONTEXT.md` files are L2; `factory/` stores stable approved reference rules (L3); per-run outputs are the Product (L4).

## Required operating order

```text
Intent -> Interpretive Context -> Plan -> Agent Execution -> Verification
       -> Human Approval -> Distribution -> CRM Results -> Learning -> Memory
```

**Mandatory interpretation chain:** Raw Data -> Business Context -> Structured Signal -> Interpretation -> Score -> Classification -> Recommended Action. **Never jump directly from raw data to a score, message or action.** Context must contain objective, constraints, assumptions, decision criteria and relationships. Outreach is the *last* consequence of understanding, never the initial objective.

## Stage routing
| Order | Stage | Contract | Handoff |
|---|---|---|---|
| 00 | intake | `00_intake/CONTEXT.md` | tenant/intent/decision criteria |
| 01 | research | `01_research/CONTEXT.md` | verified source evidence |
| 02 | context | `02_context/CONTEXT.md` | business identity and objective/constraint profiles |
| 03 | signals | `03_signals/CONTEXT.md` | interpreted and dated signals; relationships |
| 04 | decisions | `04_decisions/CONTEXT.md` | explainable score, classification, recommended action |
| 05 | execution | `05_execution/CONTEXT.md` | human-reviewed content and authorized actions |
| 06 | feedback | `06_feedback/CONTEXT.md` | reconciled CRM outcome evidence and learning proposal |

Sequential stage boundaries are **review gates**. Hermes loads only current stage context plus explicitly referenced approved outputs and immutable policy. Heavy or parallel data acquisition can occur inside a stage, but stage advancement follows the review protocol.

## Stage contract minimum
Each stage declares: Inputs, Process, Outputs, Evidence, Success criteria, Allowed tools, Review gate, Escalation, Output destination. All outputs include tenant_id, session_id, trace_id, context_version, schema_version and source provenance.

## Memory and learning
- Supabase = authoritative tenant-scoped operational data; DuckDB/Parquet = reproducible analysis; MotherDuck = optional shared analytics under approved access.
- RIOS/OKF = curated reusable interpretation and decision patterns.
- New session loads the *last verified and approved* ICM context + CRM learning snapshot, never unchecked prose from notes.
- CRM outcomes may refresh suppressions, completed statuses, unresolved tasks and advisory priorities; production scores/prompts/ICP/outreach policies change only after eval + human approval.
- Keep the **Factory** (immutable/versioned rules, examples, schemas) separate from the **Product** (tenant-specific run data and artifacts). Never store customer PII or credentials in a public Git repository.

## Context completeness gate
Reject advancement when business identity, objective, applicable constraints, evidence provenance, signal timestamp, relevance justification or decision authority are missing. Mark unknowns explicitly, degrade safely, and ask for a targeted human review when consequential.

## Source workforce catalog
https://github.com/Ksdeng1559/agency-agents/pull/1 supplies specialist agent-role references. Adapt and test roles before using them in Hermes; this workspace doesn't install the agent library.

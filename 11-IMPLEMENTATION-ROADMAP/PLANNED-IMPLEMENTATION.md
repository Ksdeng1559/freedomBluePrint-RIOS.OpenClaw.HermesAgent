# Planned Implementation Roadmap

This roadmap captures the next operating-system modules to add to the Freedom Blueprint + RIOS + Hermes + OpenClaw system.

## Purpose

The current system already defines the core operating loop:

```text
ChatGPT = Strategy
RIOS = Intelligence + memory
Hermes = Orchestration + mission control
OpenClaw = Worker execution
Claude Code / Codex = Build execution
Slack = Human governance and approvals
GitHub = Code, issues, pull requests, evidence
Supabase / Markdown Vault / Qdrant = Structured truth + human-readable memory + semantic recall
```

The next implementation phase adds governance, venture prioritization, ROI discipline, capital formation workflows, workforce management, and reusable semantic memory.

---

# Phase 1 — Governance Foundation

## 1. Decision Log

Planned folder:

```text
11-GOVERNANCE/
  DECISION-LOG.md
  DECISION-LOG-TEMPLATE.md
```

Purpose:

Track major decisions so Hermes, ChatGPT, and RIOS can explain why a choice was made later.

Decision examples:

- Hermes as orchestrator
- OpenClaw as worker
- Slack as approval layer
- USD as baseline currency
- Feature creep requires quote request
- Founding partner model for SaaS builds
- Qdrant as semantic memory layer behind MemoryService

Decision record format:

```yaml
decision:
  id: DEC-001
  date: YYYY-MM-DD
  topic: short decision title
  proposed_by: ChatGPT | Hermes | Dennis | Client
  approved_by: Dennis
  decision: final decision made
  alternatives_considered:
    - option one
    - option two
  rationale: why this decision was made
  impact: expected system or business impact
  related_files:
    - path/to/file.md
  review_date: optional
```

## 2. Architecture Decision Records

Planned folder:

```text
12-ARCHITECTURE-RECORDS/
  ADR-001-HERMES-AS-ORCHESTRATOR.md
  ADR-002-OPENCLAW-AS-WORKER.md
  ADR-003-SLACK-AS-GOVERNANCE.md
  ADR-004-CHATGPT-AS-STRATEGIC-PLANNER.md
  ADR-005-RIOS-AS-INTELLIGENCE-OS.md
  ADR-006-QDRANT-AS-SEMANTIC-MEMORY.md
```

Purpose:

Create permanent architecture memory so future agents and developers understand the reasoning behind system design.

ADR format:

```markdown
# ADR-000: Decision Title

## Status
Proposed | Accepted | Superseded

## Context
What problem existed?

## Decision
What was decided?

## Consequences
What improves? What tradeoffs exist?

## Related Files
- file-one.md
```

---

# Phase 2 — ROI, Feature Discipline, and Memory Foundation

## 3. ROI Approval Engine

Planned folder:

```text
13-ROI-APPROVAL-ENGINE/
  ROI-SCORING-MODEL.md
  FEATURE-ROI-TEMPLATE.md
  BUILD-VS-DEFER-DECISION-RULES.md
```

Purpose:

Before a feature request becomes work, Hermes calculates whether the request is economically justified.

ROI score inputs:

```yaml
feature_roi:
  feature_id: FR-001
  goal_id: GOAL-001
  expected_build_cost:
  expected_monthly_savings:
  expected_monthly_revenue_lift:
  expected_time_saved_hours_per_month:
  risk_reduction_value:
  strategic_value_score: 1-10
  urgency_score: 1-10
  reuse_potential_score: 1-10
  payback_period_months:
  recommendation: approve | quote | defer | reject | convert_to_saas_pattern
```

Default rule:

```text
No feature request enters the build queue until it has a linked goal, a quote classification, and an ROI score.
```

## 4. Feature Creep Quote Gate

Already added in Slack Command Center.

This phase will connect it to the ROI Approval Engine.

Feature request path:

```text
New Feature Request
→ Link to Goal
→ Classify as In-Scope or Out-of-Scope
→ If Out-of-Scope, create Quote Request
→ Calculate ROI / Payback / Strategic Value
→ Slack Approval
→ GitHub Issue or PRD Update
→ Build Queue
```

## 5. Qdrant Semantic Memory Service

Planned folder:

```text
18-MEMORY-SERVICE/
  MEMORYSERVICE-SPEC.md
  QDRANT-ADAPTER-SPEC.md
  MEMORY-INDEXING-SOP.md
  MEMORY-RETRIEVAL-RULES.md
```

Purpose:

Add reusable semantic recall so Hermes can retrieve similar prior work, decisions, PRDs, offers, research fragments, opportunity patterns, and client context across approved workspaces.

Memory service rule:

```text
Supabase remains the structured system of record.
Markdown Vault remains the human-readable operating knowledge layer.
Qdrant stores embeddings and metadata pointers for semantic recall.
MemoryService prevents Hermes and workers from being tightly coupled to Qdrant directly.
```

Initial MemoryService interface:

```yaml
memory_service:
  write_memory:
    input: source_text, source_record_id, workspace_id, entity_type, tags
    output: qdrant_point_id
  search_memory:
    input: query, workspace_id, filters, top_k
    output: ranked_memory_results
  link_to_source:
    input: qdrant_point_id, source_system, source_path_or_id
    output: source_pointer
  retrieve_similar_projects:
    input: project_summary, filters
    output: similar_projects
  retrieve_related_decisions:
    input: decision_context, filters
    output: related_decisions
```

Do not index unapproved, sensitive, legal, financial, or compliance-heavy material unless the source-of-truth and access-control rules are clear.

---

# Phase 3 — AI Workforce Management

## 6. AI Workforce Registry

Planned folder:

```text
14-WORKFORCE/
  WORKER-REGISTRY.md
  WORKER-ASSIGNMENT-RULES.md
  WORKER-PERFORMANCE-LOG.md
```

Purpose:

Prevent agent chaos by defining every worker, what it owns, when Hermes should use it, and what outputs it must return.

Worker record format:

```yaml
worker:
  name: OpenClaw Research Worker
  type: openclaw
  owner: hermes
  role: field research and operational execution
  allowed_tasks:
    - signal scans
    - lead enrichment
    - competitor research
    - markdown vault updates
  not_allowed:
    - strategic pricing decisions
    - production deploys
    - outbound sending without approval
  default_outputs:
    - markdown
    - csv
    - json
  approval_required: depends_on_task
```

Initial workers:

- ChatGPT Strategic Planning Agent
- Hermes Research Mode
- OpenClaw Research Worker
- OpenClaw Outreach Prep Worker
- Claude Code Build Worker
- Codex Build Worker
- Python/API Data Worker
- n8n Automation Worker
- Capital Intelligence Worker
- QA Review Worker
- Slack Governance Worker
- Memory Indexing Worker

---

# Phase 4 — Venture Studio Operating Layer

## 7. Venture Scorecard

Planned folder:

```text
15-VENTURE-STUDIO/
  VENTURE-SCORECARD.md
  VENTURE-SCORING-TEMPLATE.md
  VENTURE-PRIORITIZATION-RULES.md
```

Purpose:

Rank opportunities so Dennis does not overbuild too many ventures at once.

Scorecard categories:

```yaml
venture_score:
  name:
  problem_severity: 1-10
  buyer_budget: 1-10
  speed_to_revenue: 1-10
  founder_advantage: 1-10
  data_advantage: 1-10
  automation_fit: 1-10
  recurring_revenue_potential: 1-10
  build_complexity_inverse: 1-10
  capital_required_inverse: 1-10
  strategic_fit: 1-10
  total_score:
  recommendation: build_now | incubate | partner | defer | archive
```

Initial ventures to score:

- RIOS Core
- Mortgage Intelligence Exchange / MIX
- FieldTrack Pro
- GrantFundingAI
- Wealth Wire Radar
- MineTeck Intelligence
- GMBOS Trading Education / SaaS
- Freedom Blueprint RIOS Operating System

## 8. Opportunity Pipeline

Planned file:

```text
15-VENTURE-STUDIO/OPPORTUNITY-PIPELINE.md
```

Pipeline stages:

```text
IDEA
→ SIGNAL CONFIRMED
→ RESEARCH
→ STRATEGY BRIEF
→ PRD
→ MVP
→ PILOT
→ REVENUE
→ SCALE
→ PARTNER / EXIT
→ ARCHIVE
```

Hermes should update pipeline stage when new evidence is captured.

---

# Phase 5 — Capital Formation Layer

## 9. Investor Relations Module

Planned folder:

```text
16-CAPITAL-FORMATION/
  INVESTOR-CRM.md
  INTRODUCTION-TRACKER.md
  CAPITAL-PIPELINE.md
  INVESTOR-MEMO-SOP.md
  WARM-INTRO-SOP.md
```

Purpose:

Support capital formation workflows for Spectra, MineTeck, urban mining, RIOS venture studio, and future investor-backed opportunities.

Capital pipeline:

```text
Investor Identified
→ Relationship Path Found
→ Intro Requested
→ Intro Made
→ First Meeting
→ Follow-Up Sent
→ Materials Shared
→ Diligence
→ Soft Commit
→ Closed
→ Nurture
```

Investor record format:

```yaml
investor:
  name:
  firm:
  thesis:
  check_size:
  geography:
  relationship_path:
  warm_intro_source:
  fit_score: 1-10
  status:
  next_action:
  notes:
```

---

# Phase 6 — Knowledge Capture and Meeting Intelligence

## 10. Knowledge Capture SOP

Planned folder:

```text
17-KNOWLEDGE-CAPTURE/
  MEETING-CAPTURE-SOP.md
  CALL-SUMMARY-TEMPLATE.md
  ACTION-ITEM-EXTRACTION.md
  DECISION-EXTRACTION.md
```

Purpose:

Every meeting, call, Slack thread, or strategic discussion should become structured operating memory.

Standard flow:

```text
Meeting / Conversation
→ Summary
→ Decisions
→ Action Items
→ New Goals
→ Feature Requests
→ Hermes Missions
→ RIOS Workspace Updates
→ Decision Log Updates
→ MemoryService Indexing Decision
→ Qdrant Semantic Recall When Approved
```

Output files:

```text
/workspaces/{client-or-venture}/00-context/meeting-summary.md
/workspaces/{client-or-venture}/05-optimization/action-items.md
11-GOVERNANCE/DECISION-LOG.md
18-MEMORY-SERVICE/indexing-queue.md
```

---

# Implementation Priority

## Priority 1 — Must Add Next

1. Decision Log
2. Architecture Decision Records
3. ROI Approval Engine
4. AI Workforce Registry
5. Qdrant MemoryService foundation

These create governance, system memory, prioritization, worker discipline, and future-proof semantic recall.

## Priority 2 — Venture Studio Expansion

6. Venture Scorecard
7. Opportunity Pipeline
8. Capital Formation Module

These support RIOS as a venture studio system.

## Priority 3 — Operating Memory

9. Knowledge Capture SOP
10. Meeting Intelligence Workflow
11. Memory indexing workflow

These ensure no strategic conversation is lost and that reusable patterns can be retrieved later.

---

# Hermes Implementation Rule

Hermes should not treat this roadmap as active implementation until Dennis approves each module.

Status states:

```yaml
planned_implementation_status:
  proposed: idea captured, not approved
  approved: approved for build
  in_progress: files being created or integrated
  implemented: added to repo and ready for use
  deprecated: replaced or no longer needed
```

Current status:

```yaml
roadmap_status:
  decision_log: proposed
  architecture_decision_records: proposed
  roi_approval_engine: proposed
  ai_workforce_registry: proposed
  qdrant_memory_service: proposed
  venture_scorecard: proposed
  opportunity_pipeline: proposed
  investor_relations_module: proposed
  knowledge_capture_sop: proposed
```

Final rule:

```text
Capture everything. Build only what is approved. Price every out-of-scope request. Score every feature. Log every major decision. Index only approved reusable knowledge.
```

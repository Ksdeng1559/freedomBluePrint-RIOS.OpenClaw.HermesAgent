# Hermes + OpenClaw + RIOS Integration

## Purpose

This document defines how ChatGPT, Hermes Agent, OpenClaw, RIOS, and Qdrant work together inside the Freedom Blueprint operating system.

The goal is not to make OpenClaw the whole system. OpenClaw is a delegated worker layer. Hermes is the orchestration and mission-control layer. RIOS is the business intelligence and operating system layer. ChatGPT is the strategic planning and executive reasoning layer. Qdrant is the semantic recall layer used through MemoryService.

Hermes Agent may also perform research, drafting, enrichment, and analysis directly. Research execution should be interchangeable between Hermes and OpenClaw depending on task type, tool access, cost, speed, reliability, and memory context required.

## Core Positioning

| Layer | Role | Simple Meaning |
|---|---|---|
| ChatGPT | Strategic Planning Agent | Defines strategy, business model, offer architecture, prioritization, positioning, investor logic, and executive decisions |
| RIOS | Intelligence OS | Decides what matters, stores context, manages business logic |
| Hermes Agent | Orchestrator + Mission Control | Routes tasks, performs research when appropriate, coordinates agents, enforces workflows, manages approvals |
| OpenClaw | Delegated Worker / Field Execution Agent | Performs assigned research, outreach prep, scraping, file work, reminders, vault updates, and operational tasks |
| Claude Code / Codex | Build Engine | Creates, edits, tests, and deploys software |
| Supabase / Markdown Vault / Qdrant | Memory Layer | Stores structured truth, human-readable operating knowledge, and semantic recall |
| MemoryService | Memory Abstraction | Prevents Hermes and workers from being tightly coupled to Qdrant directly |

## Integration Doctrine

ChatGPT is the strategic planning agent.

Hermes is the orchestrator.

OpenClaw is a worker.

RIOS defines the operating model and stores intelligence.

Qdrant provides semantic recall through MemoryService.

ChatGPT helps determine what should be built, why it matters, how it should be positioned, and what the strategic plan should be.

Hermes converts the strategy into missions, assigns workers, enforces approval gates, retrieves relevant memory when useful, and tracks mission state.

OpenClaw performs delegated field tasks. It does not own the mission, choose the strategy, control the workflow, or become the system of record.

Claude Code and Codex build the products.

The complete loop is:

```text
Signal -> RIOS captures context -> MemoryService retrieves similar prior knowledge when useful -> ChatGPT creates strategy and prioritization -> Hermes creates mission -> Hermes decides whether to research directly or delegate to OpenClaw -> OpenClaw executes assigned worker tasks -> Research outputs return to Hermes -> Hermes writes mission state back to RIOS -> approved reusable knowledge is indexed through MemoryService -> ChatGPT reviews strategic implications when needed -> Hermes routes build or outreach tasks -> Claude Code / Codex builds -> RIOS records -> Hermes follows up
```

## Memory Doctrine

Qdrant does not replace Supabase, Markdown Vault, GitHub, or Slack.

```text
Supabase = structured system of record
Markdown Vault = human-readable operating knowledge
Qdrant = semantic recall and similarity search
GitHub = technical evidence trail
Slack = approvals and governance
MemoryService = access layer for semantic memory
```

Hermes should use MemoryService / Qdrant when it needs to:

- retrieve similar prior projects
- find related PRDs, offers, decisions, or workflows
- compare a new opportunity against past patterns
- detect duplicated work
- enrich a mission with approved background context
- support reusable agent memory across workspaces

Hermes should not use Qdrant alone to:

- approve spending
- send outbound messages
- make legal, financial, compliance, or investment claims
- override human-approved decisions
- change production systems
- determine source-of-truth status

## OpenClaw Worker Doctrine

OpenClaw should be treated as a worker, not the central brain.

### OpenClaw is allowed to:

- Execute delegated research tasks
- Scan websites, public sources, directories, and lead sources
- Create markdown notes and update vault folders
- Prepare outreach drafts for approval
- Enrich lead records
- Monitor signals
- Generate operational reports
- Run lightweight autonomous workflows
- Interface through Telegram/mobile-style workflows
- Return structured findings to Hermes

### OpenClaw is not allowed to:

- Override ChatGPT strategic direction
- Override Hermes mission routing
- Bypass RIOS state or memory rules
- Send outbound messages without approval
- Deploy production changes
- Make legal, financial, compliance, or investment claims
- Change pricing, positioning, or offer strategy without strategic review
- Become the source of truth for client state
- Operate as the primary orchestrator unless Hermes is unavailable and the mission is explicitly low risk

### Worker rule

Every OpenClaw task must have:

```yaml
openclaw_worker_task:
  assigned_by: hermes
  mission_id: unique-id
  task_type: research | enrichment | drafting | monitoring | file_update | reporting
  objective: clear task objective
  input_context:
    - workspace/context-file.md
    - optional_memory_results_from_memory_service
  required_output:
    path: workspace/output-file.md
    format: markdown | json | csv | report
  approval_required: true | false
  return_to: hermes
```

OpenClaw completes the work and returns the result. Hermes decides the next step.

## Strategic Planning Rule

Use ChatGPT when the task requires executive judgment, strategic synthesis, business model design, offer positioning, investment logic, or prioritization.

### ChatGPT should lead when:

- The task defines the business strategy
- The task shapes the offer architecture
- The task requires market positioning or category design
- The task involves pricing, monetization, or packaging
- The task involves investor, capital, or partnership logic
- The task requires comparing multiple strategic options
- The task requires a McKinsey-style memo, operating plan, PRD strategy, or business case
- The task decides whether something becomes a service, SaaS product, or venture studio opportunity
- The task requires turning raw research into a high-level execution plan

### Hermes should lead when:

- The strategy has been decided and must be converted into missions
- Work must be routed to the correct agent or worker
- Multiple agents need coordination
- Mission state, approvals, retries, and notifications must be managed
- A recurring workflow or scheduled process must run
- A handoff must be tracked from research to PRD to build to delivery
- Semantic memory should be retrieved to enrich mission context

### OpenClaw should lead only as a worker when:

- The task is field-level research, scraping, monitoring, file work, or operational execution
- The task can be delegated without strategic judgment
- The output is structured research, markdown notes, lead lists, outreach prep, or updates to a vault
- Hermes has already assigned the objective and success criteria

## Research Interchangeability Rule

Research tasks can be performed by either Hermes Agent or OpenClaw.

ChatGPT may also perform strategic research synthesis after Hermes or OpenClaw produce findings.

### Hermes should research directly when:

- The task requires orchestration context
- The research affects mission routing or priority
- The task requires synthesis across multiple workspaces
- The research is strategic, financial, capital-formation, or business-model related
- The output will decide whether to create a PRD, proposal, outreach campaign, or SaaS pattern
- The task needs tight connection to RIOS state, client history, approval logic, or semantic memory

### OpenClaw should research when:

- The task is repetitive or field-level
- The task involves web scanning, lead list building, competitor scans, or markdown vault updates
- The task can run autonomously without strategic judgment
- The output is structured data, drafts, notes, or enrichment files
- The task benefits from mobile/Telegram-style interaction or local vault access

### Either Hermes or OpenClaw can research when:

- The task is low risk
- The output is internal only
- The task is a first-pass scan
- The best worker depends on tool availability
- Speed matters more than perfect synthesis

### Required standard

Regardless of who performs the research, all research outputs must be stored in the same workspace format and returned to Hermes for mission-state tracking.

Approved reusable outputs should be considered for MemoryService indexing.

## What Each Layer Owns

### ChatGPT Owns

- Strategic planning
- Business model design
- Offer positioning
- Executive synthesis
- PRD strategy before technical build
- Venture studio prioritization
- Market narrative
- Pricing strategy
- Investor and partnership logic
- Client-facing strategic recommendations
- High-level operating plans
- Decision memos

### RIOS Owns

- Business logic
- Client workspaces
- Offer library
- PRD factory
- CRM and opportunity states
- Revenue dashboards
- Signal scoring rules
- Agent pack definitions
- Human approval rules
- Long-term knowledge base
- Memory source-of-truth rules

### Hermes Owns

- Mission orchestration
- Task routing
- Direct research when appropriate
- Agent coordination
- Workflow state
- Approval gates
- Retry logic
- Scheduled jobs
- Notifications
- Worker assignment
- Escalation handling
- Long-running orchestration
- MemoryService retrieval decisions
- Final synthesis across worker outputs

### OpenClaw Owns

- Delegated internet research
- Local markdown file operations
- Obsidian-style vault reading and writing
- Lead research
- Outreach drafting
- Signal scans
- Competitive research
- Daily reports
- Telegram/mobile access
- Lightweight autonomous tasks
- Returning worker outputs to Hermes

### Claude Code / Codex Own

- Repository scaffolding
- Product implementation
- Refactoring
- Debugging
- Tests
- Deployment prep
- API integrations
- Technical execution from PRDs

### MemoryService / Qdrant Owns

- Embedding approved text fragments
- Semantic retrieval
- Similarity search
- Metadata pointers back to Supabase, GitHub, Slack, or Markdown Vault records
- Retrieval filters by workspace, project, entity type, confidence, and source

## Recommended Architecture

```text
User / Operator
   |
   v
ChatGPT Strategic Planning Agent
   |
   v
RIOS Dashboard / Workspace
   |
   v
Hermes Agent Orchestrator / Mission Control
   |
   |-- MemoryService: Qdrant semantic recall and source pointers
   |-- Hermes Research Mode: strategic research, synthesis, routing decisions
   |-- OpenClaw Worker: signal research, field research, vault updates
   |-- OpenClaw Worker: outreach prep
   |-- Claude Code / Codex: product build
   |-- Python/API Worker: data processing
   |-- n8n optional: external workflow handoff
   |
   v
Supabase + Markdown Vault + Qdrant + GitHub + Slack
```

## Hermes Orchestrator Decision Tree

Hermes chooses the worker before starting each mission task.

```text
New Task
  |
  |-- Does the task require similar prior knowledge, reusable PRDs, decisions, or client patterns?
  |      |-- Yes -> Query MemoryService / Qdrant first, then continue
  |      |-- No -> Continue
  |
  |-- Does the task decide strategy, business model, positioning, pricing, or venture priority?
  |      |-- Yes -> ChatGPT Strategic Planning Agent
  |      |-- No -> Continue
  |
  |-- Does the task decide mission routing, workflow state, or approval handling?
  |      |-- Yes -> Hermes
  |      |-- No -> Continue
  |
  |-- Is the task repetitive, data-gathering, or field-level research?
  |      |-- Yes -> OpenClaw Worker
  |      |-- No -> Continue
  |
  |-- Does the task require codebase changes or software build execution?
  |      |-- Yes -> Claude Code / Codex
  |      |-- No -> Continue
  |
  |-- Does the task require deterministic processing, scraping, APIs, or data transformation?
  |      |-- Yes -> Python/API Worker
  |      |-- No -> Hermes handles directly
```

## Practical Workflow Example: Build a Client AI Lead System

### Step 1: Signal enters RIOS

A lead, client request, market opportunity, or business problem is captured.

RIOS records:

- Company
- Contact
- Pain point
- Urgency
- Revenue potential
- Fit score
- Recommended offer

### Step 2: MemoryService retrieves related context

Hermes queries semantic memory when useful:

- similar client systems
- related PRDs
- prior pricing decisions
- reusable outreach patterns
- previous implementation risks

Qdrant returns semantic matches with source pointers. Hermes checks the authoritative source before using the retrieved context.

### Step 3: ChatGPT creates strategic plan

ChatGPT reviews the RIOS context and approved retrieved memory, then creates:

- Strategic opportunity brief
- Recommended offer
- Ideal outcome
- Positioning angle
- Pricing logic
- Build-vs-service-vs-SaaS recommendation
- Risk and approval notes

Output:

```text
/workspaces/client-name/00-context/chatgpt-strategy-brief.md
```

### Step 4: Hermes creates a mission

Hermes converts the approved strategy into a mission.

Example mission:

```json
{
  "mission_type": "client_system_build",
  "client": "ABC Financial Group",
  "objective": "Build AI lead capture and qualification system",
  "priority": "high",
  "approval_required": true,
  "strategic_planner": "chatgpt",
  "orchestrator": "hermes",
  "memory_mode": "query_memoryservice_when_reusable_context_is_needed",
  "research_mode": "interchangeable",
  "assigned_workers": ["chatgpt_strategy", "hermes_research", "openclaw_worker", "prd_factory", "claude_code_builder"]
}
```

### Step 5: Hermes selects the research path

Hermes decides whether to perform the research directly, delegate to OpenClaw, or run both in parallel.

Recommended default:

- ChatGPT creates strategic framing and decision logic
- Hermes retrieves relevant prior memory through MemoryService
- Hermes researches strategic context, business model, offer angle, and mission priority
- OpenClaw researches website notes, competitors, market examples, local signals, and operational details as a delegated worker
- Hermes merges research outputs into one synthesis
- ChatGPT reviews the synthesis if it changes strategy, positioning, or pricing

Outputs go into:

```text
/workspaces/client-name/01-research/chatgpt-strategy-brief.md
/workspaces/client-name/01-research/hermes-strategy-brief.md
/workspaces/client-name/01-research/openclaw-worker-findings.md
/workspaces/client-name/01-research/research-synthesis.md
```

### Step 6: RIOS PRD Factory creates build spec

RIOS converts the research synthesis into:

- PRD
- build order
- database schema
- user flows
- deployment checklist
- acceptance criteria

### Step 7: Hermes routes build to Claude Code / Codex

Hermes sends the approved PRD to the build engine.

The build engine creates:

- app skeleton
- database schema
- forms
- admin dashboard
- integrations
- deployment files

### Step 8: Hermes, ChatGPT, or OpenClaw prepares client-facing assets

ChatGPT may create strategic client-facing assets.

Hermes may create mission-based client-facing assets directly.

OpenClaw may create operational delivery assets as an assigned worker only.

Assets include:

- Executive summary
- Loom script
- onboarding checklist
- handoff email

### Step 9: Approved reusable knowledge is indexed

After human approval, reusable knowledge may be indexed through MemoryService:

- PRD summary
- decision memo
- offer pattern
- client workflow pattern
- risk note
- implementation lesson

## Final Operating Rule

```text
ChatGPT defines strategy.
RIOS stores intelligence.
Hermes orchestrates missions.
MemoryService retrieves semantic context.
Qdrant stores meaning.
OpenClaw executes delegated work.
Claude Code and Codex build.
Slack approves.
GitHub records evidence.
```

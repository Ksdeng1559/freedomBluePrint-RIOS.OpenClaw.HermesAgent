# Hermes + OpenClaw + RIOS Integration

## Purpose

This document defines how ChatGPT, Hermes Agent, OpenClaw, and RIOS work together inside the Freedom Blueprint operating system.

The goal is not to make OpenClaw the whole system. OpenClaw is one execution layer. Hermes is the orchestration and mission-control layer. RIOS is the business intelligence and operating system layer. ChatGPT is the strategic planning and executive reasoning layer.

Hermes Agent may also perform research, drafting, enrichment, and analysis directly. Research execution should be interchangeable between Hermes and OpenClaw depending on task type, tool access, cost, speed, and reliability.

## Core Positioning

| Layer | Role | Simple Meaning |
|---|---|---|
| ChatGPT | Strategic Planning Agent | Defines strategy, business model, offer architecture, prioritization, positioning, investor logic, and executive decisions |
| RIOS | Intelligence OS | Decides what matters, stores context, manages business logic |
| Hermes Agent | Orchestrator + Mission Control | Routes tasks, performs research when appropriate, coordinates agents, enforces workflows, manages approvals |
| OpenClaw | Field Execution Agent | Performs delegated research, outreach prep, scraping, file work, reminders, and operational tasks |
| Claude Code / Codex | Build Engine | Creates, edits, tests, and deploys software |
| Supabase / Markdown Vault | Memory Layer | Stores structured data and human-readable operating knowledge |

## Integration Doctrine

ChatGPT is the strategic planning agent.

Hermes is the orchestrator.

OpenClaw is an execution worker, not the only research layer.

RIOS defines the operating model and stores intelligence.

ChatGPT helps determine what should be built, why it matters, how it should be positioned, and what the strategic plan should be.

Hermes converts the strategy into missions, assigns workers, enforces approval gates, and tracks mission state.

OpenClaw performs delegated field tasks.

Claude Code and Codex build the products.

The complete loop is:

Signal -> RIOS captures context -> ChatGPT creates strategy and prioritization -> Hermes creates mission -> Hermes decides whether to research directly or delegate to OpenClaw -> Research outputs return to RIOS -> ChatGPT reviews strategic implications when needed -> Hermes routes build or outreach tasks -> Claude Code / Codex builds -> RIOS records -> Hermes follows up

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

### OpenClaw should lead when:

- The task is field-level research, scraping, monitoring, file work, or operational execution
- The task can be delegated without strategic judgment
- The output is structured research, markdown notes, lead lists, outreach prep, or updates to a vault

## Research Interchangeability Rule

Research tasks can be performed by either Hermes Agent or OpenClaw.

ChatGPT may also perform strategic research synthesis after Hermes or OpenClaw produce findings.

### Hermes should research directly when:

- The task requires orchestration context
- The research affects mission routing or priority
- The task requires synthesis across multiple workspaces
- The research is strategic, financial, capital-formation, or business-model related
- The output will decide whether to create a PRD, proposal, outreach campaign, or SaaS pattern
- The task needs tight connection to RIOS state, client history, or approval logic

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

### Claude Code / Codex Own

- Repository scaffolding
- Product implementation
- Refactoring
- Debugging
- Tests
- Deployment prep
- API integrations
- Technical execution from PRDs

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
   |-- Hermes Research Mode: strategic research, synthesis, routing decisions
   |-- OpenClaw Worker: signal research, field research, vault updates
   |-- OpenClaw Worker: outreach prep
   |-- Claude Code / Codex: product build
   |-- Python/API Worker: data processing
   |-- n8n optional: external workflow handoff
   |
   v
Supabase + Markdown Vault + GitHub
```

## Hermes Orchestrator Decision Tree

Hermes chooses the worker before starting each mission task.

```text
New Task
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

### Step 2: ChatGPT creates strategic plan

ChatGPT reviews the RIOS context and creates:

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

### Step 3: Hermes creates a mission

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
  "research_mode": "interchangeable",
  "assigned_workers": ["chatgpt_strategy", "hermes_research", "openclaw_research", "prd_factory", "claude_code_builder"]
}
```

### Step 4: Hermes selects the research path

Hermes decides whether to perform the research directly, delegate to OpenClaw, or run both in parallel.

Recommended default:

- ChatGPT creates strategic framing and decision logic
- Hermes researches strategic context, business model, offer angle, and mission priority
- OpenClaw researches website notes, competitors, market examples, local signals, and operational details
- Hermes merges research outputs into one synthesis
- ChatGPT reviews the synthesis if it changes strategy, positioning, or pricing

Outputs go into:

```text
/workspaces/client-name/01-research/chatgpt-strategy-brief.md
/workspaces/client-name/01-research/hermes-strategy-brief.md
/workspaces/client-name/01-research/openclaw-findings.md
/workspaces/client-name/01-research/research-synthesis.md
```

### Step 5: RIOS PRD Factory creates build spec

RIOS converts the research synthesis into:

- PRD
- build order
- database schema
- user flows
- deployment checklist
- acceptance criteria

### Step 6: Hermes routes build to Claude Code / Codex

Hermes sends the approved PRD to the build engine.

The build engine creates:

- app skeleton
- database schema
- forms
- admin dashboard
- integrations
- deployment files

### Step 7: Hermes, ChatGPT, or OpenClaw prepares client-facing assets

ChatGPT may create strategic client-facing assets.

Hermes may create mission-based client-facing assets directly.

OpenClaw may create operational delivery assets.

Assets include:

- Executive summary
- Loom script
- onboarding checklist
- handoff email
- FAQ
- support SOP
- first-month optimization checklist

### Step 8: RIOS records outcome

RIOS updates:

- client status
- project stage
- build assets
- testimonial request
- retainer opportunity
- SaaS pattern candidate

## Hermes Mission Types

Use these as standard mission categories.

```yaml
mission_types:
  strategy_planning:
    owner: chatgpt
    orchestrator: hermes
    approval_required: false
    output: chatgpt_strategy_brief.md

  signal_scan:
    owner: interchangeable
    default_worker: openclaw
    orchestrator: hermes
    approval_required: false
    output: signal_report.md

  strategic_research:
    owner: hermes
    strategic_reviewer: chatgpt
    approval_required: false
    output: hermes_strategy_brief.md

  lead_enrichment:
    owner: interchangeable
    default_worker: openclaw
    orchestrator: hermes
    approval_required: false
    output: enriched_leads.csv

  market_research:
    owner: interchangeable
    default_worker: hermes
    strategic_reviewer: chatgpt
    orchestrator: hermes
    approval_required: false
    output: market_research_brief.md

  prd_generation:
    owner: rios
    strategic_input: chatgpt
    orchestrator: hermes
    approval_required: true
    output: PRD.md

  product_build:
    owner: claude_code_or_codex
    orchestrator: hermes
    approval_required: true
    output: deployed_application

  outreach_campaign:
    owner: interchangeable
    default_worker: openclaw
    strategic_reviewer: chatgpt
    orchestrator: hermes
    approval_required: true
    output: approved_messages.csv

  client_delivery:
    owner: hermes
    strategic_asset_creator: chatgpt
    approval_required: true
    output: delivery_package

  recurring_optimization:
    owner: hermes
    strategic_reviewer: chatgpt
    approval_required: false
    output: weekly_report.md
```

## Approval Rules

Hermes must require approval before:

- Sending outbound messages
- Spending money
- Deploying production changes
- Updating client-facing assets
- Deleting files or records
- Making legal, financial, compliance, or investment claims
- Moving a lead to closed-won
- Issuing proposals or invoices

Hermes, OpenClaw, or ChatGPT can run without approval for:

- Research
- Drafting
- Summarizing
- File organization
- Signal monitoring
- Competitive scans
- Internal reports
- Strategic planning drafts

## Shared Workspace Structure

Each client or venture should have this structure:

```text
/workspaces/{client-or-venture}/
  00-context/
    CLIENT.md
    OFFER.md
    GOALS.md
    chatgpt-strategy-brief.md
  01-research/
    chatgpt-strategy-brief.md
    hermes-strategy-brief.md
    openclaw-findings.md
    competitor-scan.md
    signal-report.md
    research-synthesis.md
  02-prd/
    PRD.md
    BUILD-SEQUENCE.md
  03-build/
    repo-link.md
    deployment-notes.md
    qa-log.md
  04-delivery/
    executive-summary.md
    loom-script.md
    handoff-email.md
    onboarding-checklist.md
  05-optimization/
    weekly-report.md
    improvement-backlog.md
  06-saas-pattern/
    reusable-features.md
    founding-partner-notes.md
```

## Agent Handoff Contract

Every handoff between ChatGPT, RIOS, Hermes, OpenClaw, and Claude Code should use this format:

```yaml
handoff:
  from: ChatGPT | RIOS | Hermes | OpenClaw | Claude Code | Codex
  to: ChatGPT | RIOS | Hermes | OpenClaw | Claude Code | Codex
  mission_id: unique-id
  objective: what must be achieved
  strategic_planner: chatgpt
  orchestrator: hermes
  research_mode: hermes_direct | openclaw_delegated | parallel | interchangeable
  context_files:
    - path/to/context.md
  required_outputs:
    - output-one.md
    - output-two.csv
  constraints:
    - no outbound sending without approval
    - no production deployment without approval
  success_criteria:
    - clear measurable result
  next_review_checkpoint: human_review
```

## Worker Assignment Contract

Hermes should assign work using this structure:

```yaml
worker_assignment:
  mission_id: unique-id
  assigned_by: hermes
  worker: chatgpt_strategy | hermes_research | openclaw | claude_code | codex | python_api_worker | n8n
  task_type: strategy | research | enrichment | drafting | build | qa | delivery | reporting
  reason_for_assignment: why this worker is best suited
  input_context:
    - workspace/context-file.md
  required_output:
    path: workspace/output-file.md
    format: markdown | json | csv | code | report
  approval_required: true | false
  return_to: hermes
```

## Minimum Viable Integration

Do not overbuild the first version.

Start with:

1. ChatGPT strategy brief
2. RIOS workspace structure
3. Hermes mission file
4. OpenClaw research output
5. RIOS PRD output
6. Claude Code build output
7. Hermes delivery checklist
8. Weekly optimization report

## Operating Rule

ChatGPT thinks strategically.

RIOS stores and structures intelligence.

Hermes orchestrates.

OpenClaw executes field tasks.

Claude Code and Codex build.

Supabase and the Markdown Vault remember.

Do not collapse these roles unless the task is small enough that separation creates unnecessary friction.

# Hermes + OpenClaw + RIOS Integration

## Purpose

This document defines how Hermes Agent, OpenClaw, and RIOS work together inside the Freedom Blueprint operating system.

The goal is not to make OpenClaw the whole system. OpenClaw is one execution layer. Hermes is the orchestration and mission-control layer. RIOS is the business intelligence and operating system layer.

Hermes Agent may also perform research, drafting, enrichment, and analysis directly. Research execution should be interchangeable between Hermes and OpenClaw depending on task type, tool access, cost, speed, and reliability.

## Core Positioning

| Layer | Role | Simple Meaning |
|---|---|---|
| RIOS | Intelligence OS | Decides what matters, stores context, manages business logic |
| Hermes Agent | Orchestrator + Mission Control | Routes tasks, performs research when appropriate, coordinates agents, enforces workflows, manages approvals |
| OpenClaw | Field Execution Agent | Performs delegated research, outreach prep, scraping, file work, reminders, and operational tasks |
| Claude Code / Codex | Build Engine | Creates, edits, tests, and deploys software |
| Supabase / Markdown Vault | Memory Layer | Stores structured data and human-readable operating knowledge |

## Integration Doctrine

Hermes is the orchestrator.

OpenClaw is an execution worker, not the only research layer.

RIOS defines the operating model.

Hermes coordinates, delegates, executes when useful, and records mission state.

OpenClaw performs delegated field tasks.

Claude Code builds the products.

The complete loop is:

Signal -> RIOS evaluates -> Hermes creates mission -> Hermes decides whether to research directly or delegate to OpenClaw -> Research outputs return to RIOS -> Hermes routes build or outreach tasks -> Claude Code / Codex builds -> RIOS records -> Hermes follows up

## Research Interchangeability Rule

Research tasks can be performed by either Hermes Agent or OpenClaw.

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
  |-- Does the task decide strategy, priority, pricing, proposal, or build scope?
  |      |-- Yes -> Hermes Research Mode
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

### Step 2: Hermes creates a mission

Hermes converts the signal into a mission.

Example mission:

```json
{
  "mission_type": "client_system_build",
  "client": "ABC Financial Group",
  "objective": "Build AI lead capture and qualification system",
  "priority": "high",
  "approval_required": true,
  "orchestrator": "hermes",
  "research_mode": "interchangeable",
  "assigned_workers": ["hermes_research", "openclaw_research", "prd_factory", "claude_code_builder"]
}
```

### Step 3: Hermes selects the research path

Hermes decides whether to perform the research directly, delegate to OpenClaw, or run both in parallel.

Recommended default:

- Hermes researches strategic context, business model, offer angle, and mission priority
- OpenClaw researches website notes, competitors, market examples, local signals, and operational details
- Hermes merges both into one research synthesis

Outputs go into:

```text
/workspaces/client-name/01-research/hermes-strategy-brief.md
/workspaces/client-name/01-research/openclaw-findings.md
/workspaces/client-name/01-research/research-synthesis.md
```

### Step 4: RIOS PRD Factory creates build spec

RIOS converts the research synthesis into:

- PRD
- build order
- database schema
- user flows
- deployment checklist
- acceptance criteria

### Step 5: Hermes routes build to Claude Code / Codex

Hermes sends the approved PRD to the build engine.

The build engine creates:

- app skeleton
- database schema
- forms
- admin dashboard
- integrations
- deployment files

### Step 6: Hermes or OpenClaw prepares client-facing assets

Hermes may create strategic client-facing assets directly.

OpenClaw may create operational delivery assets.

Assets include:

- Loom script
- onboarding checklist
- handoff email
- FAQ
- support SOP
- first-month optimization checklist

### Step 7: RIOS records outcome

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
  signal_scan:
    owner: interchangeable
    default_worker: openclaw
    orchestrator: hermes
    approval_required: false
    output: signal_report.md

  strategic_research:
    owner: hermes
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
    orchestrator: hermes
    approval_required: false
    output: market_research_brief.md

  prd_generation:
    owner: rios
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
    orchestrator: hermes
    approval_required: true
    output: approved_messages.csv

  client_delivery:
    owner: hermes
    approval_required: true
    output: delivery_package

  recurring_optimization:
    owner: hermes
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

Hermes or OpenClaw can run without approval for:

- Research
- Drafting
- Summarizing
- File organization
- Signal monitoring
- Competitive scans
- Internal reports

## Shared Workspace Structure

Each client or venture should have this structure:

```text
/workspaces/{client-or-venture}/
  00-context/
    CLIENT.md
    OFFER.md
    GOALS.md
  01-research/
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

Every handoff between RIOS, Hermes, OpenClaw, and Claude Code should use this format:

```yaml
handoff:
  from: RIOS
  to: Hermes
  mission_id: unique-id
  objective: what must be achieved
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
  worker: hermes_research | openclaw | claude_code | codex | python_api_worker | n8n
  task_type: research | enrichment | drafting | build | qa | delivery | reporting
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

1. RIOS folder/workspace standard
2. Hermes mission file format
3. Hermes direct research mode
4. OpenClaw delegated research and vault-update tasks
5. Claude Code PRD-to-build loop
6. Supabase or Markdown record of mission status
7. Human approval checkpoints

## Version 1 Implementation Plan

### Phase 1: Documentation Integration

- Define Hermes mission schema
- Define workspace folder structure
- Define Hermes direct research mode
- Define OpenClaw worker roles
- Define approval rules
- Define handoff contract

### Phase 2: Manual Runtime

- User creates mission manually
- Hermes mission file is created as Markdown or JSON
- Hermes decides research path
- Hermes performs strategic research or delegates field research to OpenClaw
- Claude Code executes build tasks
- RIOS records mission progress

### Phase 3: Semi-Automated Runtime

- Add scheduled signal scans
- Add automatic mission creation from approved signals
- Add Supabase mission table
- Add worker assignment table
- Add notification queue
- Add weekly reporting

### Phase 4: Full Runtime

- Hermes runs on VPS
- OpenClaw runs as local or server worker
- RIOS dashboard manages missions
- Claude Code / Codex build tasks are queued
- Supabase tracks state, memory, approvals, worker assignments, and outputs

## Strategic Summary

The Freedom Blueprint teaches how to build and sell with Claude Code.

The RIOS version adds intelligence, orchestration, and repeatability.

Hermes is the orchestrator. It can research directly, delegate research to OpenClaw, or run both in parallel.

OpenClaw gives the system field execution and local/mobile operational reach.

RIOS gives the system memory, business logic, and monetization architecture.

This integration turns a solo builder workflow into an agentic venture operating system.
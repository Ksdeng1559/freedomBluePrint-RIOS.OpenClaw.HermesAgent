# Hermes + OpenClaw + RIOS Integration

## Purpose

This document defines how Hermes Agent, OpenClaw, and RIOS work together inside the Freedom Blueprint operating system.

The goal is not to make OpenClaw the whole system. OpenClaw is the field operator layer. Hermes is the mission-control coordinator. RIOS is the business intelligence and operating system layer.

## Core Positioning

| Layer | Role | Simple Meaning |
|---|---|---|
| RIOS | Intelligence OS | Decides what matters, stores context, manages business logic |
| Hermes Agent | Mission Control | Routes tasks, coordinates agents, enforces workflows, manages approvals |
| OpenClaw | Execution Agent | Performs research, outreach, scraping, file work, reminders, and operational tasks |
| Claude Code / Codex | Build Engine | Creates, edits, tests, and deploys software |
| Supabase / Markdown Vault | Memory Layer | Stores structured data and human-readable operating knowledge |

## Integration Doctrine

Hermes does not replace OpenClaw.

OpenClaw does not replace RIOS.

RIOS defines the operating model.
Hermes coordinates the work.
OpenClaw executes field tasks.
Claude Code builds the products.

The complete loop is:

Signal -> RIOS evaluates -> Hermes routes -> OpenClaw researches/executes -> Claude Code builds -> RIOS records -> Hermes follows up

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

- Task routing
- Agent coordination
- Workflow state
- Approval gates
- Retry logic
- Scheduled jobs
- Notifications
- Worker assignment
- Escalation handling
- Long-running orchestration

### OpenClaw Owns

- Internet research
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
Hermes Agent Mission Control
   |
   |-- OpenClaw Worker: signal research
   |-- OpenClaw Worker: outreach prep
   |-- OpenClaw Worker: vault updates
   |-- Claude Code / Codex: product build
   |-- Python/API Worker: data processing
   |-- n8n optional: external workflow handoff
   |
   v
Supabase + Markdown Vault + GitHub
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
  "assigned_workers": ["openclaw_research", "prd_factory", "claude_code_builder"]
}
```

### Step 3: OpenClaw researches

OpenClaw gathers:

- Website notes
- Competitor examples
- Offer positioning
- Client pain points
- Outreach hooks
- Local SEO or CRM issues

Output goes into:

```text
/workspaces/client-name/research/openclaw-findings.md
```

### Step 4: RIOS PRD Factory creates build spec

RIOS converts the research into:

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

### Step 6: OpenClaw prepares client-facing assets

OpenClaw creates:

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
    owner: openclaw
    approval_required: false
    output: signal_report.md

  lead_enrichment:
    owner: openclaw
    approval_required: false
    output: enriched_leads.csv

  prd_generation:
    owner: rios
    approval_required: true
    output: PRD.md

  product_build:
    owner: claude_code_or_codex
    approval_required: true
    output: deployed_application

  outreach_campaign:
    owner: openclaw
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

OpenClaw can run without approval for:

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
    openclaw-findings.md
    competitor-scan.md
    signal-report.md
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

## Minimum Viable Integration

Do not overbuild the first version.

Start with:

1. RIOS folder/workspace standard
2. Hermes mission file format
3. OpenClaw research and vault-update tasks
4. Claude Code PRD-to-build loop
5. Supabase or Markdown record of mission status
6. Human approval checkpoints

## Version 1 Implementation Plan

### Phase 1: Documentation Integration

- Define Hermes mission schema
- Define workspace folder structure
- Define OpenClaw worker roles
- Define approval rules
- Define handoff contract

### Phase 2: Manual Runtime

- User creates mission manually
- Hermes mission file is created as Markdown or JSON
- OpenClaw executes research and drafting tasks
- Claude Code executes build tasks
- RIOS records mission progress

### Phase 3: Semi-Automated Runtime

- Add scheduled signal scans
- Add automatic mission creation from approved signals
- Add Supabase mission table
- Add notification queue
- Add weekly reporting

### Phase 4: Full Runtime

- Hermes runs on VPS
- OpenClaw runs as local or server worker
- RIOS dashboard manages missions
- Claude Code / Codex build tasks are queued
- Supabase tracks state, memory, approvals, and outputs

## Strategic Summary

The Freedom Blueprint teaches how to build and sell with Claude Code.

The RIOS version adds intelligence, orchestration, and repeatability.

OpenClaw gives the system hands.
Hermes gives the system command and control.
RIOS gives the system memory, business logic, and monetization architecture.

This integration turns a solo builder workflow into an agentic venture operating system.

# RIOS Operating Architecture

## Purpose

RIOS is the intelligence and execution layer that upgrades the Freedom Blueprint from a solo builder workflow into an AI-powered business operating system.

## Layered Architecture

```text
Client / Market Signal
        ↓
Discovery and Research Layer
        ↓
PRD Factory
        ↓
Build Lab: Claude Code / Codex
        ↓
Deployment Layer: GitHub / Vercel / Railway / Supabase
        ↓
Client Delivery Layer
        ↓
Retainer / Optimization Layer
        ↓
Productization / SaaS Layer
```

## Core Roles

### 1. Strategy Operator

Owns:

- Business model
- Offer design
- Client discovery
- Pricing
- Sales judgment
- Final approval

### 2. PRD Architect

Owns:

- Interviewing the operator
- Turning ideas into requirements
- Defining build scope
- Creating feature priority
- Writing Claude Code prompt sequence

### 3. Technical Builder

Owns:

- Repository setup
- Application build
- Debugging
- Testing
- Deployment
- Documentation

Primary tools:

- Claude Code
- Codex
- GitHub

### 4. Hermes Agent

Owns:

- Long-running workflows
- Scheduled scans
- Task assignment
- Logs
- Approval queues
- Memory retrieval
- Workflow orchestration

### 5. OpenClaw-Style Agent Layer

Owns:

- Markdown-first memory
- Outreach prompts
- Signal scanning
- Model routing
- Lightweight automations
- Daily operator briefings

## Memory Standard

Every project should maintain:

- `PROJECT.md` — what the project is
- `USER.md` — operator/client context
- `AGENT.md` — agent behavior rules
- `DECISIONS.md` — key decisions and rationale
- `CHANGELOG.md` — what changed over time
- `NEXT-STEPS.md` — current work queue

## Human Approval Checkpoints

Human approval is required before:

- Sending outbound client messages
- Spending money
- Deploying production changes
- Deleting data
- Handling legal, financial, tax, or compliance-sensitive information
- Making irreversible business commitments

## Default RIOS Build Flow

```text
1. Capture idea
2. Create PRD
3. Confirm scope
4. Generate build prompts
5. Build one prompt at a time
6. QA after each major feature
7. Deploy to staging
8. Review with human
9. Deploy to production
10. Document delivery
11. Convert to monthly support
```

## Principle

RIOS is not a chatbot. RIOS is the operating system for turning business problems into deployed, revenue-generating systems.

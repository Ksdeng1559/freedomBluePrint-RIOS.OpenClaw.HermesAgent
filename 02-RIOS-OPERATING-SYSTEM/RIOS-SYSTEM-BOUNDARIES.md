# RIOS System Boundaries

## Purpose

This document defines what each layer of the Freedom Blueprint RIOS OpenClaw HermesAgent Operating System owns, does not own, and must hand off to another layer.

The goal is to prevent role confusion, tool sprawl, duplicated work, and unsafe automation.

## Core Boundary Principle

RIOS is the intelligence operating system.

Hermes is the orchestrator.

OpenClaw is the worker layer.

Claude Code and Codex are build execution engines.

Slack is the governance layer.

GitHub is the technical evidence layer.

Supabase is the structured system of record.

Markdown is the human-readable operating layer.

Qdrant is semantic recall.

## Layer Ownership Matrix

| Layer | Owns | Does Not Own |
|---|---|---|
| ChatGPT | Strategy, synthesis, offer design, prioritization, executive reasoning | Production deployment, autonomous outbound, database truth |
| RIOS | Goals, opportunities, decisions, PRDs, context, scoring, long-term intelligence | Low-level worker execution, direct production changes |
| Hermes | Mission control, task routing, approval gates, workflow state, handoffs | Deep strategy, uncontrolled execution, replacing human approvals |
| OpenClaw | Delegated research, scraping, enrichment, scans, reporting, markdown updates | Strategic decisions, final approvals, pricing authority |
| Claude Code / Codex | Code generation, implementation, debugging, refactoring, tests | Business approval, client commitment, pricing decisions |
| Slack | Approval records, sign-offs, change requests, quote approvals | Source of technical truth, code history |
| GitHub | Issues, commits, pull requests, code review, ADRs, technical evidence | Business CRM, final client approval unless mirrored from Slack |
| Supabase | Structured records, CRM objects, opportunities, users, mission states | Long-form operating manuals, semantic similarity search |
| Markdown Vault | Human-readable knowledge, SOPs, briefs, decisions, playbooks | Structured transactional system of record |
| Qdrant | Embeddings, semantic memory, similarity recall, context retrieval | Replacing Supabase, replacing Markdown, final truth authority |

## RIOS Must Own

RIOS owns:

- Business goals
- Client context
- Opportunity records
- Mission state
- Decision logs
- PRDs
- Feature requests
- Scoring rules
- Signal definitions
- Knowledge graph relationships
- Context graph priorities
- Reusable SaaS patterns

RIOS should answer:

- What matters?
- Why does it matter?
- What is connected?
- What has been decided?
- What should happen next?

## Hermes Must Own

Hermes owns:

- Mission creation
- Worker routing
- Approval enforcement
- Workflow state tracking
- Escalation rules
- Scheduled missions
- Handoff coordination
- Status reporting
- Human-in-the-loop checkpoints

Hermes should answer:

- Who should do this?
- What is the next step?
- Is approval required?
- Has evidence been captured?
- Is the mission ready to move forward?

## OpenClaw Must Own

OpenClaw owns delegated worker execution such as:

- Company research
- Website scans
- Lead enrichment
- Feedstock signal discovery
- Investor list building
- Competitive research
- Markdown vault updates
- Daily or weekly research reports
- Source gathering
- Data extraction where permitted

OpenClaw should not approve final decisions.

OpenClaw should produce evidence, not conclusions without review.

## Claude Code and Codex Must Own

Claude Code and Codex own:

- Repository edits
- App scaffolding
- Backend implementation
- Frontend implementation
- Test creation
- Refactoring
- Debugging
- Deployment preparation
- Documentation updates tied to code

They do not own:

- Pricing
- Client promises
- Legal claims
- Financial claims
- Production deployment without approval
- Sensitive data changes without approval

## Slack Must Own

Slack owns human approval records for:

- Pricing
- Scope changes
- Quote approvals
- Deployment sign-offs
- Outbound campaign approvals
- Client-facing asset approval
- Sensitive data approval
- Legal, financial, or compliance-sensitive claims

## GitHub Must Own

GitHub owns technical evidence:

- Issues
- Pull requests
- Commits
- Code review
- Architecture Decision Records
- Build history
- Deployment references
- Technical change trail

## Supabase Must Own

Supabase owns structured truth:

- Users
- Clients
- Companies
- Contacts
- Opportunities
- Missions
- Tasks
- Statuses
- Scores
- Approval records when mirrored from Slack
- Audit logs when implemented

## Markdown Vault Must Own

Markdown owns human-readable knowledge:

- Operating manuals
- SOPs
- Meeting summaries
- Mission briefs
- Research packets
- Client notes
- Strategy notes
- Decision summaries
- Playbooks

## Qdrant Must Own

Qdrant owns semantic recall:

- Similar missions
- Similar opportunities
- Similar PRDs
- Similar client issues
- Similar objections
- Similar investor profiles
- Similar supplier profiles
- Similar historical decisions

Qdrant should return pointers back to Supabase, Markdown, GitHub, or source evidence.

## Human Approval Boundary

No automated layer may independently:

- Send outbound messages
- Spend money
- Deploy production changes
- Delete records
- Update client-facing assets
- Make legal claims
- Make financial claims
- Make compliance claims
- Move a deal to closed-won
- Send quotes or invoices
- Approve out-of-scope work

## System Expansion Rule

A new tool may only be added when it clearly improves one of these capabilities:

- Faster capture
- Better context
- Better evidence
- Better scoring
- Better workflow execution
- Better approval control
- Better delivery quality
- Better reuse of patterns

If a tool does not improve one of these, it should not be added to the core architecture.

## Final Boundary Rule

The system should stay simple until the workflow proves revenue value.

Do not add enterprise architecture before one repeatable workflow produces a client-ready or revenue-ready outcome.

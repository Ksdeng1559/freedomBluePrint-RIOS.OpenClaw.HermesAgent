# Worker Assignment Matrix

## Purpose

This document defines which system layer should own each type of task in the Freedom Blueprint RIOS OpenClaw HermesAgent Operating System.

The goal is to prevent tool confusion and make every mission executable.

## Core Rule

Strategy is not execution.

Execution is not approval.

Approval is not evidence.

Evidence is not memory.

Each task must have one clear primary owner and one clear evidence destination.

## Assignment Matrix

| Task Type | Primary Owner | Supporting Layer | Evidence Destination | Approval Required |
|---|---|---|---|---|
| Business strategy | ChatGPT | RIOS | Markdown Vault | No, unless client-facing |
| Offer design | ChatGPT | RIOS | Markdown Vault | Yes before client use |
| Goal capture | RIOS | ChatGPT | Supabase + Markdown | No |
| Mission creation | Hermes | RIOS | Supabase + Markdown | No |
| Worker routing | Hermes | RIOS | Supabase | No |
| Company research | OpenClaw | Hermes | Markdown + source links | No |
| Lead scraping | OpenClaw | Hermes | Supabase + Markdown | Yes before outreach |
| Lead enrichment | OpenClaw | Hermes | Supabase | No |
| Feedstock signal discovery | OpenClaw | RIOS | Supabase + Markdown | No |
| Investor research | OpenClaw | ChatGPT | Markdown + Supabase | Yes before outreach |
| Competitive research | OpenClaw | ChatGPT | Markdown | No |
| PRD drafting | RIOS | ChatGPT | Markdown + GitHub | Yes before build |
| Technical architecture | Claude Code / Codex | ChatGPT | GitHub + ADR | Yes before build if client-facing |
| Code implementation | Claude Code / Codex | Hermes | GitHub | Yes before production deploy |
| QA checklist | Hermes | Claude Code / Codex | GitHub + Markdown | Yes before delivery |
| Deployment | Claude Code / Codex | Hermes | GitHub | Yes |
| Client-facing copy | ChatGPT | RIOS | Markdown | Yes |
| Outbound email draft | ChatGPT | OpenClaw | Markdown | Yes before send |
| Outbound sending | Human-approved tool flow | Hermes | Slack + CRM | Yes |
| Pricing recommendation | ChatGPT | RIOS | Markdown | Yes |
| Quote generation | RIOS | ChatGPT | Markdown + Slack | Yes |
| Invoice or proposal issue | Human | Hermes | Slack + CRM | Yes |
| Slack approval tracking | Slack | Hermes | Slack | Human action required |
| GitHub issue creation | Hermes | Claude Code / Codex | GitHub | No |
| Pull request review | Human + Claude Code / Codex | Hermes | GitHub | Yes before merge if production |
| Decision logging | RIOS | Hermes | Markdown + Supabase | No, unless sensitive |
| Semantic recall | Qdrant | Hermes | Pointer to source | No |
| Structured record storage | Supabase | RIOS | Supabase | Depends on data sensitivity |
| Operating manual update | ChatGPT | Hermes | Markdown + GitHub | Yes if doctrine changes |

## Worker Classes

### Research Worker

Used for:

- Company lookup
- Industry scan
- Market signal research
- Investor list building
- Supplier discovery
- Feedstock opportunity discovery

Outputs:

- Source links
- Evidence notes
- Opportunity summary
- Confidence score
- Gaps and unknowns

### Enrichment Worker

Used for:

- Company profile enrichment
- Contact enrichment
- Industry classification
- Geography tagging
- Revenue range tagging where available
- Buyer or seller intent signal enrichment

Outputs:

- Structured Supabase-ready record
- Source references
- Data confidence score

### Outreach Prep Worker

Used for:

- Drafting outreach angles
- Preparing first 25 outreach targets
- Creating objection notes
- Matching offer to target pain
- Preparing human-approved message drafts

Outputs:

- Draft messages
- Target rationale
- Risk notes
- Required approval checkpoint

### Build Worker

Used for:

- App scaffolding
- API integration
- Database schema creation
- Component implementation
- Test generation
- Debugging

Outputs:

- GitHub commits
- Pull requests
- Build notes
- QA checklist

### Governance Worker

Used for:

- Change request review
- Scope classification
- Quote gate decision support
- Approval routing
- Decision log updates

Outputs:

- Scope classification
- Approval request
- Quote recommendation
- Decision log entry

## Mission Assignment Format

Every mission should include:

```text
Mission:
Business Goal:
Primary Owner:
Supporting Layers:
Worker Type:
Inputs:
Expected Outputs:
Evidence Destination:
Approval Gate:
Deadline or Review Rhythm:
Risks:
Definition of Done:
```

## Escalation Rules

Escalate to human approval when the task involves:

- Money
- Legal claims
- Financial claims
- Compliance claims
- Client commitments
- Production deployment
- Sending outbound messages
- Sensitive data
- Deleting or overwriting records
- Changing pricing
- Changing scope

## Final Rule

No mission should start until the owner, worker type, evidence destination, and approval gate are clear.

# Hermes / OpenClaw Agent Operations

## Purpose

This folder defines how the Freedom Blueprint operating system becomes proactive rather than reactive.

Hermes is the persistent AI workforce, including discovery, enrichment coordination, qualification, outbound preparation, CRM feedback analysis, and continuous evaluation. Mission Control is its supervision and task-routing capability, not its only function. See [CRM Learning Loop v2](CRM-LEARNING-LOOP-V2.md) and [Agency Agents workforce mapping](WORKFORCE-AGENCY-AGENTS-REFactor.md).

OpenClaw-style workflows provide memory, routing, outreach, and task automation patterns.

## Session Learning Standard

At the start of each session, load the most recent validated tenant-specific CRM learning snapshot and freeze its version for the run. At session close, reconcile CRM events, record outcome quality and propose next-session prioritization. Suppression and verified deal-status refreshes may update operational state immediately; scoring weights, ICP and external outreach require evaluation and approval. See [acceptance criteria](SESSION-FEEDBACK-ACCEPTANCE.md).

## Agent Operating Principles

1. Markdown-first memory
2. Human-readable context
3. One source of truth per project
4. Proactive scheduled briefings
5. Model routing based on task complexity
6. Human approval for sensitive actions
7. Logs for every automated workflow

## Daily Agent Brief

Hermes should be able to produce a daily brief:

```text
Daily Operator Brief

1. Active projects
2. Client commitments due
3. Outreach sent yesterday
4. Replies needing attention
5. Build blockers
6. New market signals
7. Suggested next action
8. Risks requiring human review
```

## Model Routing Standard

Use cheaper/faster models for:

- File organization
- Status updates
- Data formatting
- Simple classification
- Template generation
- Routine summaries

Use stronger reasoning models for:

- Architecture decisions
- Security review
- Customer-facing proposals
- Strategic positioning
- Complex debugging
- Financial, legal, or compliance-sensitive analysis

## Agent Memory Files

Each workspace should include:

```text
PROJECT.md
USER.md
AGENT.md
DECISIONS.md
TASKS.md
DAILY-LOG.md
CLIENT-CONTEXT.md
OUTREACH-LOG.md
```

## Standing Orders

Hermes can be instructed to:

- Review open tasks daily
- Summarize outreach activity
- Identify stalled opportunities
- Prepare next-day priorities
- Monitor repo changes
- Generate weekly revenue report
- Flag missing documentation

## Safety Rules

Agents must not automatically:

- Send client messages
- Delete production data
- Spend money
- Change DNS
- Modify contracts
- Provide legal or financial decisions as final advice
- Contact investors or clients without approval

## Future Automation Candidates

- Lead research scanner
- Warm intro tracker
- Demo booking assistant
- Client onboarding checklist generator
- PRD generator from call transcript
- Weekly project status reporter
- Retainer renewal reminder
- SaaS feature request classifier

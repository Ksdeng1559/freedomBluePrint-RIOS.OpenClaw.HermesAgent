# Operating Manual

## Purpose

This repository is the command center for converting the Freedom Blueprint into a repeatable RIOS-style AI business operating system.

The objective is to help an operator move from idea to paid client to productized service to SaaS without losing context, skipping planning, or building things that cannot be sold.

## The Operating Loop

```text
Signal -> Discovery -> PRD -> Build -> Deploy -> Demo -> Close -> Deliver -> Retain -> Productize -> SaaS
```

## Weekly Execution Cadence

### Monday — Market and Signal Review

- Review target verticals
- Identify 25 businesses or opportunities
- Capture buying signals
- Prioritize by pain, budget, urgency, and access

### Tuesday — PRD and Demo Build

- Select one workflow problem
- Run the PRD interview
- Create a 1-page build brief
- Generate the Claude Code prompt sequence

### Wednesday — Build and QA

- Execute the build loop
- Test the product locally
- Push to GitHub
- Deploy to Vercel / Railway / Cloudflare

### Thursday — Demo and Outreach

- Customize demo for 5-10 prospects
- Record short Loom videos
- Send personalized outreach
- Book discovery calls

### Friday — Sales and Delivery

- Run sales calls
- Send proposals
- Improve offer and pricing
- Convert completed builds to monthly support

### Saturday — Systemization

- Update SOPs
- Save prompts
- Add reusable components
- Document lessons learned
- Index approved reusable knowledge into Qdrant through MemoryService when it is valuable for future recall

### Sunday — Review

- Revenue generated
- Demos booked
- Builds shipped
- Retainers closed
- Bottlenecks
- Next week's one priority

## Success Metrics

### Stage 1 Metrics

- 1 sellable demo live
- 25 personalized outreach messages per week
- 5 conversations per week
- 1-2 paid builds per month
- 3-5 testimonials or proof assets

### Stage 2 Metrics

- 1 productized offer
- Repeatable delivery checklist
- VA or assistant support for outreach
- 5-10 active retainers
- Weekly inbound or referral flow
- Reusable semantic memory available across approved workspaces

### Stage 3 Metrics

- Repeated pain observed across 3+ clients
- Founding partner identified
- MVP funded by client or partner
- SaaS roadmap created
- Public case study produced

## Decision Rules

1. If the problem is not painful, do not build.
2. If the buyer cannot explain the value, simplify the offer.
3. If the workflow repeats, automate it.
4. If three clients ask for the same thing, productize it.
5. If a productized service scales with software, convert it to SaaS.
6. If there is legal, financial, compliance, or reputational risk, keep a human in the loop.
7. If knowledge will be useful across future projects, store the authoritative record first, then index it into Qdrant for semantic recall.

## Default Stack

- Planning: ChatGPT / Claude
- Build execution: Claude Code / Codex
- Frontend: Next.js / React
- Backend: Supabase / Railway
- Deployment: Vercel / Railway / Cloudflare
- CRM: GoHighLevel when client acquisition or follow-up is involved
- Orchestration: Hermes Agent
- Memory: Markdown Vault + Supabase + Qdrant through MemoryService
- Source of truth: Slack approvals, GitHub evidence, Supabase records, Markdown operating documents
- Semantic recall: Qdrant for similar projects, decisions, PRDs, offers, research, and client patterns
- Outreach: Signal-based research + personalized Loom/email

## Memory Rule

```text
Supabase stores structured truth.
Markdown stores readable operating knowledge.
Qdrant stores semantic recall.
GitHub stores technical evidence.
Slack stores approvals.
Hermes decides what context matters.
Humans approve high-impact action.
```

Qdrant is not the system of record. It is used only after source material has an approved record, file, or evidence trail.

## First Build Recommendation

Build the `AI Lead Capture + Qualification Dashboard` first.

It is simple enough to ship quickly, valuable enough to sell, and flexible enough to adapt to mortgage brokers, insurance agents, advisors, trades, consultants, and local businesses.

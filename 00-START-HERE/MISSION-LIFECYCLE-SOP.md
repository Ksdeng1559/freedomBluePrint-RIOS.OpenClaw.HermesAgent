# Mission Lifecycle SOP

## Purpose

This SOP defines the canonical lifecycle for moving a business signal, idea, or client request through the Freedom Blueprint RIOS OpenClaw HermesAgent Operating System.

It is the master operating process for the repository.

Every workflow should follow this sequence unless there is a documented reason to deviate.

```text
Signal → Goal → Mission Brief → Worker Assignment → Research Packet → PRD → Build → QA → Approval → Delivery → Pattern Capture
```

## Operating Principle

No build starts without a PRD.

No mission starts without a goal.

No worker executes without an assignment.

No client-facing action happens without approval.

No completed mission is finished until the decision and pattern are captured.

---

# Stage 1: Signal Capture

## Purpose

Capture a business trigger, market signal, client request, founder idea, operational pain, investor lead, supplier opportunity, or workflow inefficiency.

## Inputs

Examples:

- Client request
- Sales conversation
- Market signal
- Website discovery
- Investor conversation
- Supplier lead
- Competitor movement
- Internal workflow pain
- Founder idea
- Meeting note

## Owner

Primary: Human Operator or ChatGPT  
System of Record: RIOS  
Evidence Layer: Markdown Vault

## Required Output

```text
Signal:
Source:
Date:
Why it matters:
Potential business outcome:
Urgency:
Confidence:
```

## Exit Criteria

A signal becomes a goal only if it connects to a measurable business outcome.

---

# Stage 2: Goal Creation

## Purpose

Convert the signal into a clear business goal.

## Owner

Primary: RIOS  
Support: ChatGPT  
Evidence Layer: Markdown Vault + Supabase when implemented

## Goal Format

```text
Business Goal:
Target Outcome:
Success Metric:
Time Horizon:
Strategic Fit:
Commercial Value:
Risk Level:
```

## Example

```text
Business Goal: Identify qualified PC board and server feedstock suppliers in the Pacific Northwest.
Target Outcome: Build a supplier opportunity list to support urban mining capital formation.
Success Metric: 25 qualified suppliers with evidence, contact path, and confidence score.
Time Horizon: 7 days.
Strategic Fit: High.
Commercial Value: High.
Risk Level: Medium.
```

## Exit Criteria

A goal is approved for mission creation when:

- It supports revenue, delivery, capital formation, operations, or productization
- It has a measurable outcome
- It has enough context to assign work

---

# Stage 3: Mission Brief Creation

## Purpose

Turn the goal into a controlled mission that Hermes can route and workers can execute.

## Required Template

Use:

`12-TEMPLATES/MISSION-BRIEF-TEMPLATE.md`

## Owner

Primary: Hermes  
Support: RIOS + ChatGPT  
Evidence Layer: Markdown Vault

## Required Output

The mission brief must include:

- Mission title
- Business goal
- Trigger
- Mission owner
- Primary system owner
- Supporting layers
- Mission type
- Inputs
- Worker assignment
- Task instructions
- Required evidence
- Evidence destination
- Success criteria
- Approval gates
- Risks and constraints
- Scoring criteria
- Recommended next action
- Decision log section
- Reusable pattern capture section

## Exit Criteria

A mission can move forward only when it has:

1. Owner
2. Worker assignment
3. Evidence requirements
4. Definition of done
5. Approval gate

---

# Stage 4: Worker Assignment

## Purpose

Assign the mission to the correct execution layer.

## Required Matrix

Use:

`09-HERMES-OPENCLAW/WORKER-ASSIGNMENT-MATRIX.md`

## Owner

Primary: Hermes  
Support: RIOS  
Evidence Layer: Supabase mission state + Markdown brief

## Worker Types

Common worker types:

- Research Worker
- Enrichment Worker
- Outreach Prep Worker
- Build Worker
- Governance Worker
- QA Worker
- Pattern Capture Worker

## Required Output

```text
Mission:
Primary Worker:
Supporting Worker:
Inputs:
Expected Outputs:
Evidence Destination:
Approval Gate:
Definition of Done:
```

## Exit Criteria

Worker assignment is complete when the responsible system or person knows exactly:

- What to do
- What not to do
- What evidence to produce
- Where to store output
- When to stop for approval

---

# Stage 5: Research Packet

## Purpose

Produce traceable evidence before creating strategy, outreach, PRDs, or build plans.

## Owner

Primary: OpenClaw or delegated worker  
Support: Hermes  
Review: Human Operator or ChatGPT  
Evidence Layer: Markdown Vault + source links

## Required Research Packet Format

```text
Mission:
Research Date:
Worker:
Sources Reviewed:
Key Findings:
Evidence Links:
Companies or Contacts Identified:
Signals Detected:
Confidence Score:
Risks:
Unknowns:
Recommended Next Action:
```

## Rules

- Evidence must be source-linked where possible
- Unknowns must be clearly stated
- Assumptions must not be presented as facts
- Research is not approval
- Research is not outreach
- Research is not a final decision

## Exit Criteria

The research packet is complete when a reviewer can understand:

- What was researched
- What was found
- What evidence supports it
- What remains unknown
- What action is recommended

---

# Stage 6: Human Review

## Purpose

Prevent low-confidence research or unsafe recommendations from becoming actions.

## Owner

Primary: Human Operator  
Support: ChatGPT + Hermes  
Evidence Layer: Slack approval or Markdown decision note

## Review Questions

```text
Is the evidence sufficient?
Are the sources credible enough?
Are the risks acceptable?
Does this support the business goal?
Should this become a PRD, outreach list, build task, or archive item?
Does any action require approval?
```

## Possible Decisions

```text
[ ] Approve
[ ] Reject
[ ] Request more research
[ ] Convert to PRD
[ ] Convert to outreach prep
[ ] Convert to GitHub issue
[ ] Add to opportunity pipeline
[ ] Archive
```

## Exit Criteria

A mission can move to the next stage only when a human or authorized reviewer makes a decision.

---

# Stage 7: PRD Creation

## Purpose

Convert approved research and goals into a buildable product requirements document.

## Required Template

Use:

`03-PRD-FACTORY/PRD-INTERVIEW-PROMPT.md`

## Owner

Primary: RIOS + ChatGPT  
Support: Hermes  
Evidence Layer: Markdown Vault + GitHub

## PRD Must Include

- Problem statement
- Target user
- Business goal
- Workflow description
- Functional requirements
- Non-functional requirements
- Data requirements
- Approval requirements
- MVP scope
- Out-of-scope list
- Acceptance criteria

## Exit Criteria

A PRD is ready for build only when:

- Scope is clear
- Acceptance criteria are clear
- Human approval gates are preserved
- Out-of-scope items are documented

---

# Stage 8: Build Execution

## Purpose

Turn the approved PRD into a working asset, prototype, workflow, app, dashboard, automation, or client deliverable.

## Owner

Primary: Claude Code / Codex  
Support: Hermes  
Evidence Layer: GitHub

## Required Build Outputs

```text
GitHub Issue:
Branch or Commit:
Implementation Notes:
Test Notes:
Known Limitations:
QA Checklist:
Deployment Status:
```

## Rules

- Build only approved scope
- Document deviations
- Do not deploy production changes without approval
- Do not change sensitive records without approval
- Do not send outbound messages without approval

## Exit Criteria

Build stage is complete when:

- Work is traceable in GitHub
- QA checklist is created
- Known limitations are documented
- Deployment gate is clear

---

# Stage 9: QA and Governance Review

## Purpose

Confirm the deliverable is safe, accurate, and aligned with the original goal.

## Owner

Primary: Hermes  
Support: Human Operator + Claude Code / Codex  
Evidence Layer: GitHub + Slack

## QA Checklist

```text
[ ] Matches approved PRD
[ ] Solves the stated problem
[ ] No unauthorized scope added
[ ] No unsupported claims
[ ] No unapproved outbound action
[ ] No unapproved production deployment
[ ] Sensitive data protected
[ ] Known limitations documented
[ ] Human approval captured where required
```

## Exit Criteria

The deliverable can move to approval only when QA is complete.

---

# Stage 10: Approval Gate

## Purpose

Require human approval before sensitive or client-facing actions occur.

## Owner

Primary: Human Operator  
Support: Hermes  
Evidence Layer: Slack + GitHub + Markdown

## Approval Required For

- Sending outbound messages
- Spending money
- Deploying production changes
- Updating client-facing assets
- Deleting files or records
- Making legal claims
- Making financial claims
- Making compliance claims
- Moving a lead to closed-won
- Issuing proposals, quotes, invoices, or pricing changes
- Changing approved scope

## Approval Format

```text
Approval Request:
Mission:
Action Requested:
Evidence Reviewed:
Risk Level:
Approved By:
Approval Decision:
Date:
Notes:
```

## Exit Criteria

No sensitive action proceeds until approval is captured.

---

# Stage 11: Delivery

## Purpose

Package the completed work into a usable business outcome.

## Owner

Primary: Human Operator or Delivery Owner  
Support: Hermes + ChatGPT  
Evidence Layer: Markdown + GitHub + Slack

## Delivery Output

```text
Deliverable:
Business Goal Supported:
What Was Completed:
How to Use It:
Evidence Links:
Known Limitations:
Next Recommended Action:
Retainer Opportunity:
```

## Exit Criteria

Delivery is complete when the end user, client, or internal stakeholder can use the output.

---

# Stage 12: Pattern Capture

## Purpose

Convert completed work into reusable intelligence, offers, automations, or SaaS patterns.

## Owner

Primary: RIOS  
Support: ChatGPT + Hermes  
Evidence Layer: Markdown + Supabase + Qdrant when implemented

## Pattern Capture Format

```text
Mission Completed:
Problem Solved:
Repeatable Workflow:
Reusable Data Model:
Reusable Automation:
Potential Offer:
Potential SaaS Module:
Retainer Opportunity:
Lessons Learned:
Next Mission:
```

## Exit Criteria

A mission is fully complete only when the pattern capture section is filled out or marked as not applicable.

---

# Automation and Human-in-the-Loop Rules

## Can Be Automated

- Signal monitoring
- Company research
- Supplier discovery
- Lead enrichment
- Investor discovery
- Competitive scans
- Research packet drafts
- PRD drafts
- Internal summaries
- Decision log drafts
- Pattern capture drafts

## Must Stay Human-Approved

- Outbound sending
- Spending money
- Production deployment
- Legal claims
- Financial claims
- Compliance claims
- Pricing changes
- Proposals
- Quotes
- Invoices
- Client-facing final assets
- Deleting or overwriting records

## Recommended HITL Flow

```text
Automate discovery.
Automate drafting.
Automate scoring.
Automate routing.
Human approves decisions.
Human approves external actions.
Human approves money movement.
Human approves client-facing claims.
```

---

# Mission Status Definitions

Use these statuses consistently:

```text
captured
scored
mission_created
worker_assigned
researching
research_ready
human_review
approved_for_prd
prd_ready
approved_for_build
building
qa_review
approval_required
approved_for_delivery
delivered
pattern_captured
archived
```

---

# Final Rule

The system should become more automated only after the workflow has produced reliable outcomes.

Start with controlled automation.

Scale only after the approval gates work.

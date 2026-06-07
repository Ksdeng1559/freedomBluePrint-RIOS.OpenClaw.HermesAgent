# MVP Build Sequence

## Purpose

This document defines the recommended build order for turning the Freedom Blueprint RIOS OpenClaw HermesAgent Operating System into a working MVP.

The MVP should prove one repeatable business workflow before expanding into a larger platform.

## MVP Doctrine

Do not build the full operating system first.

Build the smallest working loop that can:

1. Capture a real business goal
2. Create a mission
3. Assign workers
4. Gather evidence
5. Produce a PRD
6. Build or package an asset
7. Route approval
8. Deliver value
9. Capture the pattern for reuse

## Recommended Flagship MVP

Urban Mining Feedstock Intelligence should be the first implementation use case.

Why:

- It has real commercial value
- It supports capital formation
- It requires signal detection
- It uses supplier discovery
- It benefits from worker-based research
- It can produce investor-ready intelligence
- It can become a repeatable revenue workflow

## Phase 1: Documentation and Operating Spine

Goal:

Create the minimum operating documentation required to run one mission.

Required files:

- `README.md`
- `00-START-HERE/QUICKSTART-7-DAY-ACTION-PLAN.md`
- `02-RIOS-OPERATING-SYSTEM/RIOS-SYSTEM-BOUNDARIES.md`
- `09-HERMES-OPENCLAW/WORKER-ASSIGNMENT-MATRIX.md`
- `12-TEMPLATES/MISSION-BRIEF-TEMPLATE.md`

Definition of done:

- A new operator can understand the system roles
- A mission can be created from a goal
- A worker can be assigned
- Approval gates are visible

## Phase 2: Mission Brief Workflow

Goal:

Create the first repeatable mission workflow.

Required capabilities:

- Capture business goal
- Define mission scope
- Define worker tasks
- Define evidence requirements
- Define approval gates
- Define decision log requirements

Output:

- One completed mission brief
- One approved mission
- One research packet

Definition of done:

- Mission has a clear owner
- Worker assignments are documented
- Evidence destination is defined
- Human approval gates are clear

## Phase 3: Research Packet Workflow

Goal:

Create a repeatable process for worker-generated evidence.

Required capabilities:

- Source gathering
- Company identification
- Signal tagging
- Opportunity notes
- Confidence scoring
- Risk notes
- Human review summary

Output:

- Research packet in Markdown
- Structured opportunity list ready for Supabase
- Source evidence links

Definition of done:

- Research can be reviewed by a human
- Sources are traceable
- Unknowns are clearly stated
- No unsupported claims are promoted to final strategy

## Phase 4: PRD Factory Workflow

Goal:

Convert approved research into a buildable PRD.

Required capabilities:

- Problem statement
- Target user
- Workflow map
- Functional requirements
- Non-functional requirements
- Data requirements
- Approval requirements
- MVP scope
- Out-of-scope list

Output:

- One PRD ready for Claude Code or Codex

Definition of done:

- Build scope is clear
- Business objective is clear
- Human approval gates are preserved
- Out-of-scope work is identified

## Phase 5: Build Lab Workflow

Goal:

Turn PRD into a technical asset, prototype, or client-ready deliverable.

Required capabilities:

- GitHub issue creation
- Architecture notes
- Implementation tasks
- QA checklist
- Pull request workflow
- Deployment gate

Output:

- Prototype or deliverable
- GitHub evidence trail
- QA summary

Definition of done:

- Work is traceable in GitHub
- QA checklist is complete
- Deployment approval is captured before production use

## Phase 6: Approval and Governance Workflow

Goal:

Ensure all sensitive actions require human approval.

Required approval types:

- Outbound messages
- Pricing
- Quotes
- Production deployment
- Client-facing assets
- Financial claims
- Legal or compliance claims
- Sensitive data changes

Output:

- Slack approval record
- Decision log summary
- Updated mission status

Definition of done:

- No sensitive action occurs without approval
- Approval record is easy to find
- Mission status is updated

## Phase 7: Pattern Capture and Reuse

Goal:

Turn successful missions into reusable offers, playbooks, or SaaS modules.

Required capabilities:

- Capture repeated pain
- Capture repeated workflow
- Capture reusable data model
- Capture reusable automation pattern
- Capture pricing opportunity
- Capture delivery SOP

Output:

- Reusable offer candidate
- SaaS pattern candidate
- Retainer opportunity
- Next mission recommendation

Definition of done:

- The system has learned from the mission
- The workflow can be reused
- The next revenue opportunity is documented

## MVP Success Criteria

The MVP is successful when one use case can move through this full chain:

```text
Goal → Mission → Worker Assignment → Research Packet → PRD → Build Plan → QA → Approval → Delivery → Pattern Capture
```

## Do Not Build Yet

Do not build these until the first workflow is proven:

- Full enterprise dashboard
- Complex multi-tenant permissions
- Full CRM replacement
- Full autonomous outbound
- Full investor portal
- Full knowledge graph UI
- Full agent marketplace
- Complex orchestration engine

## Build First

Build these first:

- Mission brief template
- Worker assignment rules
- Research packet format
- PRD conversion flow
- Approval gate checklist
- GitHub issue workflow
- Decision log format
- Reusable pattern capture template

## Final Rule

A working workflow is more valuable than a complete architecture diagram.

Prove the revenue loop first.

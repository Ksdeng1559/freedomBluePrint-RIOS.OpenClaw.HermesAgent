# Graph, Knowledge Graph, and Context Graph Methodology

## Purpose

This document defines the reusable RIOS methodology for converting business use cases into graph-aware, knowledge-aware, and context-aware operating systems.

The methodology is designed for GTM Engineering, venture studio builds, capital formation workflows, investor intelligence, feedstock sourcing, grant intelligence, mortgage intelligence, local SEO intelligence, commercial property buyer discovery, and other signal-driven business systems.

This is a core RIOS design pattern.

---

## Core Doctrine

```text
Graph
= What is connected?

Knowledge Graph
= What do those connections mean?

Context Graph
= What matters right now?

RIOS
= What should we do next?

Hermes
= Who should do it?

OpenClaw
= Which worker executes the task?

GitHub
= What evidence was produced?
```

The goal is not to build a graph database first.

The goal is to build a business intelligence operating system that can understand relationships, meaning, mission context, and next-best-action decisions.

---

## Why This Matters

Most business systems store records.

```text
Contact
Company
Deal
Task
Note
```

RIOS should store context.

```text
Signal
Relationship
Meaning
Opportunity
Decision
Action
Evidence
Outcome
```

Traditional CRMs answer:

```text
Who is in the database?
```

RIOS should answer:

```text
Given everything we know, what opportunity deserves attention next?
```

---

## Layer 1: Graph Layer

### Core Question

```text
What is connected?
```

The graph layer maps relationships between people, companies, assets, opportunities, documents, conversations, signals, and actions.

### Typical Entities

```text
Person
Organization
Project
Asset
Signal
Opportunity
Conversation
Document
Decision
Task
Worker
Investor
Supplier
Partner
Customer
```

### Typical Relationships

```text
Person WORKS_FOR Organization
Person KNOWS Person
Organization OWNS Asset
Organization GENERATES Signal
Signal INDICATES Opportunity
Conversation REFERENCES Opportunity
Document SUPPORTS Decision
Decision CREATES Task
Worker EXECUTES Task
Investor INTERESTED_IN Project
Supplier PROVIDES Asset
Partner INTRODUCES Contact
```

### Output

The graph layer produces a relationship map.

It shows who and what is connected.

---

## Layer 2: Knowledge Graph Layer

### Core Question

```text
What do these connections mean?
```

The knowledge graph adds business meaning to the raw relationships.

Example:

```text
A server rack is not just equipment.
It may be high-value urban mining feedstock.

A retired business owner is not just a contact.
They may be a succession opportunity.

A municipal RFP is not just a document.
It may be a grant, procurement, or partnership signal.
```

### Typical Meaning Tags

```text
Capital Source
Strategic Partner
Feedstock Source
Buyer Candidate
Grant Candidate
High-Intent Lead
Influence Node
Warm Introduction Path
Data Room Evidence
Revenue Opportunity
Operational Risk
Compliance Review Required
```

### Output

The knowledge graph produces business interpretation.

It explains why a connection matters.

---

## Layer 3: Context Graph Layer

### Core Question

```text
What matters right now?
```

The context graph filters the knowledge graph based on:

```text
Current mission
Business objective
Time horizon
User intent
Relationship access
Stage of workflow
Risk level
Compliance constraints
Available workers
Evidence quality
Next decision required
```

The context graph prevents agents from retrieving everything.

It retrieves what is useful for the current mission.

### Example

If the mission is:

```text
Secure $5M in feedstock acquisition capital.
```

The context graph should prioritize:

```text
feedstock LOIs
qualified supplier conversations
investors interested in circular economy infrastructure
warm introductions
working capital requirements
data room evidence
legal review requirements
```

It should deprioritize unrelated records, stale contacts, low-fit leads, and unverified assumptions.

### Output

The context graph produces mission-relevant context.

It answers what matters now.

---

## Layer 4: RIOS Action Layer

### Core Question

```text
What should we do next?
```

RIOS converts context into action.

Examples:

```text
Research this account
Find the decision maker
Score this opportunity
Request a warm introduction
Send a supplier education email
Create a PRD
Create a grant readiness memo
Record a Loom follow-up
Prepare a data room package
Escalate for human approval
Open a GitHub issue
Assign an OpenClaw worker
```

### Output

RIOS produces next-best-action recommendations.

---

## Layer 5: Hermes Orchestration Layer

### Core Question

```text
Who should do it?
```

Hermes turns the next-best-action into a mission.

Hermes should define:

```text
Mission objective
Assigned worker
Required tools
Required context
Approval gates
Evidence requirements
Completion criteria
Escalation rules
```

### Output

Hermes produces controlled execution.

---

## Layer 6: OpenClaw Worker Layer

### Core Question

```text
Which worker executes the task?
```

OpenClaw is a delegated worker layer.

It is not the central brain.

It executes bounded research, scraping, enrichment, reporting, and file update tasks under Hermes and RIOS governance.

### Example Worker Types

```text
Signal Hunter
Account Research Worker
Relationship Mapping Worker
Data Room Evidence Worker
Grant Research Worker
Investor Fit Worker
Competitive Scan Worker
Content Drafting Worker
CRM Hygiene Worker
Daily Report Worker
```

### Output

OpenClaw produces task evidence.

---

## Layer 7: GitHub Evidence Layer

### Core Question

```text
What evidence was produced?
```

GitHub records:

```text
architecture decisions
PRDs
issues
commits
pull requests
data models
implementation notes
agent outputs
review history
source-of-truth documents
```

For RIOS, GitHub is not just code storage.

GitHub is the evidence trail for business system construction.

---

## Standard Methodology Flow

```text
Use Case Identified
  ↓
Business Objective Defined
  ↓
Core Entities Listed
  ↓
Relationships Mapped
  ↓
Meaning Tags Defined
  ↓
Context Rules Created
  ↓
Signals Identified
  ↓
Scoring Model Created
  ↓
Next-Best-Actions Defined
  ↓
Hermes Missions Created
  ↓
OpenClaw Workers Assigned
  ↓
GitHub Evidence Captured
  ↓
RIOS Memory Updated
  ↓
Reusable Pattern Extracted
```

---

## Use Case Template

Use this structure when creating a new RIOS context intelligence use case.

```text
1. Use Case Name
2. Business Objective
3. Primary KPI
4. Core Entities
5. Core Relationships
6. Meaning Tags
7. Context Rules
8. Signal Sources
9. Scoring Model
10. Next-Best-Actions
11. Worker Types
12. Data Model
13. Governance Rules
14. Evidence Requirements
15. Reusable Pattern Candidate
```

---

## Example Use Case 1: Urban Mining Feedstock Intelligence

### Business Objective

Find, qualify, and secure high-value electronic feedstock that strengthens a $5M feedstock acquisition raise and validates the urban mining platform.

### Primary KPI

```text
Dollars of qualified feedstock opportunity identified and secured per month.
```

### Core Entities

```text
Company
Facility
Contact
Feedstock
Asset
Broker
Recycler
Investor
Project
Opportunity
Signal
Conversation
LOI
Shipment
Capital Source
Grant Program
Processing Partner
```

### Core Relationships

```text
Company OWNS Facility
Facility GENERATES Feedstock
Feedstock CONTAINS Material
Contact WORKS_FOR Company
Signal INDICATES Opportunity
Broker INTRODUCED Opportunity
Investor INTERESTED_IN Project
LOI SECURES Feedstock
Capital Source FUNDS Acquisition
Processing Partner RECOVERS Material
```

### Context Rules

Prioritize:

```text
Data center closures
Enterprise server refreshes
Hospital IT upgrades
University equipment refreshes
Telecom hardware replacements
Municipal surplus auctions
Known warm introductions
Opportunities that can produce LOIs
Opportunities that support investor diligence
```

Deprioritize:

```text
Low-grade consumer electronics
Unverified brokers
Signals with no current disposal event
Targets with poor relationship access
Opportunities outside practical logistics range
```

### Worker Types

```text
Feedstock Signal Hunter
Organization Research Worker
Relationship Intelligence Worker
Feedstock Value Worker
Capital Formation Worker
```

### Related Implementation Repository

```text
Ksdeng1559/breakthrough-urban-mining-feedstock-raise
```

Detailed implementation belongs in the use-case repository.

This methodology repository stores the reusable pattern.

---

## Additional Candidate Use Cases

This methodology can be reused for:

```text
Investor intelligence
Grant intelligence
Mortgage intelligence
Commercial property buyer discovery
Local SEO opportunity detection
FieldTrack Pro safety intelligence
MIX mortgage CRM
LeadSniperAI account targeting
Strategic partnership mapping
Revenue leak diagnosis
```

---

## Data Architecture Principle

Start graph-aware before becoming graph-database-dependent.

Recommended MVP stack:

```text
Supabase
Postgres relationship tables
Markdown / ICM workspaces
MotherDuck / DuckDB analytics
Structured JSON records
Hermes orchestration
GitHub evidence trail
```

Graph database upgrade path:

```text
Neo4j or equivalent graph database
```

Evaluate only when the system requires:

```text
high-volume multi-hop relationship traversal
large-scale entity resolution
real-time graph analytics
complex relationship pathfinding
enterprise knowledge graph integration
agent-scale context retrieval
```

---

## Governance Rules

Human approval is required before:

```text
Sending outbound messages
Making legal, financial, securities, or investment claims
Spending money
Changing production systems
Deleting records
Publishing client-facing content
Moving a deal to closed-won
Issuing quotes, proposals, or invoices
```

For capital formation use cases, all investor-facing material must be reviewed by qualified securities counsel before use.

---

## Final Doctrine

```text
The graph shows relationships.
The knowledge graph explains meaning.
The context graph identifies what matters now.
RIOS recommends the next action.
Hermes orchestrates execution.
OpenClaw performs delegated work.
GitHub records the evidence.
```

This is the reusable Context Intelligence pattern for RIOS-powered business systems.

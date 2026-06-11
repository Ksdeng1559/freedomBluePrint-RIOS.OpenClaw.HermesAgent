# RIOS Lite
## Product Requirements Document

**Version:** 1.0  
**Date:** June 10, 2026  
**Status:** Canonical MVP Product Definition

---

# 1. Product Summary

RIOS Lite is the first practical product version of the Relationship Intelligence Operating System.

It is a voice-first relationship intelligence and relationship asset management platform for businesses that depend on relationships, conversations, opportunities, introductions, follow-up, and institutional memory.

Wispr Flow is the initial front-door capture interface. It allows a user to speak naturally from their desktop or mobile workflow and convert speech into text that is submitted to RIOS Lite for classification, extraction, review, and storage.

RIOS Lite transforms unstructured business conversations and voice notes into structured relationship assets, opportunities, tasks, interactions, and durable organizational memory.

---

# 2. Product Thesis

Relationship-driven businesses often operate from personal memory, scattered notes, inboxes, documents, spreadsheets, and informal follow-up.

This creates recurring problems:

- Important relationships are forgotten.
- Opportunities are not captured consistently.
- Follow-up commitments are missed.
- Business context is lost over time.
- Organizational intelligence remains trapped in individuals.
- Management cannot see the full relationship and opportunity picture.

RIOS Lite changes the operating model from memory-based execution to intelligence-based execution.

The core product thesis is:

> Relationships become assets. Conversations become intelligence. Intelligence becomes opportunities. Opportunities become action. Action becomes enterprise value.

---

# 3. Product Positioning

RIOS Lite is not positioned as:

- A traditional CRM
- A social media tool
- A generic note-taking application
- A transcription service
- A securities brokerage platform
- A marketing automation platform

RIOS Lite is positioned as:

> A voice-first Relationship Intelligence Operating System that converts business conversations into structured relationship assets, opportunities, tasks, and organizational memory.

---

# 4. Target Users

## 4.1 Primary Users

- Business owners
- Executives
- Relationship managers
- Business development professionals
- Capital formation teams
- Commercial mortgage professionals
- Private lending professionals
- Commercial real estate teams
- Strategic partnership teams
- Industrial and technology companies
- Professional advisory firms

## 4.2 Primary Pilot Organizations

### Spectra Holdings

Primary use cases:

- Relationship Asset Management
- Capital source tracking
- Strategic partner tracking
- Opportunity intelligence
- Organizational memory

### MineTeck / Urban Mining

Primary use cases:

- Feedstock intelligence
- Strategic investor tracking
- Government funding tracking
- Capital-readiness support
- Pilot and partnership tracking

### Commercial Mortgage / Private Lending

Primary use cases:

- Lender relationship intelligence
- Borrower opportunity tracking
- Referral source intelligence
- Renewal and refinance tracking
- Compliance-aware conversation memory

---

# 5. Product Goals

The MVP must enable a user to:

1. Capture a business conversation or voice note through Wispr Flow.
2. Submit the resulting text into RIOS Lite.
3. Classify the submission automatically.
4. Extract people, organizations, opportunities, interactions, commitments, and tasks.
5. Match extracted records against existing data.
6. Present extraction candidates in a review queue.
7. Allow the user to approve, edit, merge, or reject candidates.
8. Save approved records into the operational database.
9. Store the original source and cleaned record for auditability.
10. Make approved content searchable through semantic retrieval.
11. Produce follow-up tasks and next-action recommendations.
12. Display basic relationship and opportunity intelligence in a dashboard.

---

# 6. Non-Goals for MVP

The first version will not include:

- Fully autonomous outbound communication
- Autonomous investor solicitation
- Transaction-based compensation workflows
- Securities sales or brokerage functions
- Complex forecasting engines
- Full social media publishing
- Complete multi-channel CRM replacement
- Advanced relationship graph visualization
- Native local speech transcription
- Fully autonomous record creation without review

These may be considered in later phases.

---

# 7. Core User Experience

## 7.1 Voice-First Front Door

Wispr Flow is the primary immediate capture interface.

The user speaks naturally, for example:

> I spoke with Sarah at Northview Capital. She is interested in the MineTeck pilot but wants an updated recovery economics summary. Send it by Friday and schedule a follow-up next Wednesday.

Wispr Flow converts the speech into text.

The user submits or pastes the text into the RIOS Lite Voice Inbox.

RIOS Lite then identifies:

- Person: Sarah
- Organization: Northview Capital
- Opportunity: MineTeck pilot investment or partnership
- Requested asset: Updated recovery economics summary
- Task: Send the summary by Friday
- Task: Follow up next Wednesday
- Interaction: Business conversation
- Relationship update: Investor or strategic capital contact

## 7.2 Input Methods

MVP input methods:

- Wispr Flow dictation into the RIOS Lite web interface
- Paste text into the Voice Inbox
- Upload an audio file for OpenAI Whisper transcription
- Upload an existing transcript

Wispr Flow is the preferred front-door experience, while OpenAI Whisper remains the platform transcription engine for uploaded audio.

---

# 8. Core Workflow

```text
Conversation or Voice Note
  ↓
Wispr Flow or Audio Upload
  ↓
Text or OpenAI Whisper Transcript
  ↓
Raw Intake Record
  ↓
Transcript / Text Cleaner
  ↓
RIOS Intelligence Extractor
  ↓
Extraction Candidates
  ↓
Human Review Queue
  ↓
Approved Canonical Records
  ↓
Supabase
  ↓
DuckDB / MotherDuck Analytics
  ↓
Qdrant Semantic Memory
  ↓
Tasks, Dashboards, Reports, Agent Workflows
```

---

# 9. Front-Door Intake Categories

RIOS Lite must classify each intake into one or more categories:

1. Relationship Update
2. Contact Update
3. Organization Update
4. Opportunity Update
5. Task or Commitment
6. Meeting or Call Note
7. Strategic Insight
8. Content or Campaign Idea
9. Funding or Partnership Signal
10. Report or Research Request
11. General Organizational Memory

A single intake may contain multiple categories.

---

# 10. Core Entities

## 10.1 Person

Required attributes:

- Person ID
- Tenant ID
- Full name
- Email
- Phone
- Role or title
- Primary organization
- Relationship type
- Relationship status
- Relationship strength
- Last interaction date
- Source intake ID
- Created at
- Updated at

## 10.2 Organization

Required attributes:

- Organization ID
- Tenant ID
- Organization name
- Industry
- Organization type
- Website
- Location
- Strategic value
- Relationship status
- Source intake ID
- Created at
- Updated at

## 10.3 Opportunity

Required attributes:

- Opportunity ID
- Tenant ID
- Title
- Opportunity type
- Related people
- Related organizations
- Description
- Stage
- Estimated value
- Probability
- Priority
- Expected decision or close date
- Next action
- Source intake ID
- Created at
- Updated at

## 10.4 Interaction

Required attributes:

- Interaction ID
- Tenant ID
- Interaction type
- Interaction date
- Participants
- Related organizations
- Related opportunities
- Raw source
- Clean summary
- Commitments
- Decisions
- Sentiment or relationship signal
- Source intake ID
- Created at

## 10.5 Task

Required attributes:

- Task ID
- Tenant ID
- Task title
- Description
- Owner
- Due date
- Priority
- Status
- Related person
- Related organization
- Related opportunity
- Source intake ID
- Created at
- Completed at

## 10.6 Intake Record

Required attributes:

- Intake ID
- Tenant ID
- Input type
- Source application
- Raw text
- Audio storage reference when applicable
- Cleaned text
- Classification
- Processing status
- Review status
- Created by
- Created at

## 10.7 Extraction Candidate

Required attributes:

- Candidate ID
- Tenant ID
- Intake ID
- Entity type
- Proposed operation
- Proposed values
- Match candidates
- Confidence score
- Review status
- Reviewed by
- Reviewed at

---

# 11. Functional Requirements

## FR-1: Voice and Text Intake

The system must provide a clear Voice Inbox that accepts:

- Wispr Flow dictated text
- Pasted text
- Uploaded transcripts
- Uploaded audio files

## FR-2: Raw Source Preservation

The system must preserve the original submitted text or transcript without modification.

## FR-3: Text Cleaning

The system must generate a cleaned version that:

- Removes filler words when appropriate
- Corrects obvious punctuation issues
- Preserves the original meaning
- Does not invent facts
- Identifies uncertain words or names

## FR-4: Automatic Classification

The system must assign one or more intake categories.

## FR-5: Entity Extraction

The system must extract:

- People
- Organizations
- Opportunities
- Interactions
- Tasks
- Commitments
- Decisions
- Strategic insights

## FR-6: Record Matching

Before proposing a new record, the system must search for possible existing matches using:

- Exact matching
- Fuzzy matching
- Email and phone matching
- Organization-name matching
- Qdrant semantic similarity

## FR-7: Review Queue

The system must present candidates for human review before canonical save.

The reviewer must be able to:

- Approve
- Edit
- Merge with an existing record
- Reject
- Defer

## FR-8: Canonical Save

Only approved candidates may create or update canonical Supabase records.

## FR-9: Task Creation

Approved commitments and next actions must create tasks with owners, priorities, and due dates when available.

## FR-10: Semantic Indexing

Approved transcripts, summaries, interactions, and records must be indexed in Qdrant.

## FR-11: Analytics Synchronization

Approved operational data must be available to DuckDB / MotherDuck for analytical queries and reporting.

## FR-12: Search

Users must be able to search across:

- People
- Organizations
- Opportunities
- Interactions
- Tasks
- Transcripts
- Strategic insights

Search must support both keyword and semantic retrieval.

## FR-13: Dashboard

The MVP dashboard must show:

- New relationship records
- Open opportunities
- Tasks due
- Overdue tasks
- Recent interactions
- Pending review items
- Relationship activity
- Opportunity activity

## FR-14: Audit Trail

Every approved record must maintain a traceable link to:

- Original source intake
- Cleaned text
- Extraction candidate
- Reviewer decision
- Final canonical record

## FR-15: Multi-Tenant Isolation

All operational records, semantic memory, transcripts, files, and agent context must be isolated by tenant.

---

# 12. Agent Architecture

## 12.1 Hermes Agent

Role:

Primary orchestrator and workflow manager.

Responsibilities:

- Load tenant context
- Select the correct workflow
- Coordinate specialist agents
- Monitor workflow completion
- Produce summaries and reports
- Write approved outputs back into RIOS

## 12.2 Relationship Extractor

Responsibilities:

- Identify people and organizations
- Identify relationship roles and signals
- Propose new records or updates
- Detect relationship strength and follow-up needs

## 12.3 Opportunity Extractor

Responsibilities:

- Identify explicit and implied opportunities
- Link opportunities to people and organizations
- Extract stage, priority, value, timing, risks, and next actions

## 12.4 Task Agent

Responsibilities:

- Identify promises, deadlines, follow-ups, and assigned work
- Propose task owner and due date
- Detect missing ownership or unclear timing

## 12.5 Memory Agent

Responsibilities:

- Identify durable organizational memory
- Distinguish permanent knowledge from temporary working context
- Prepare approved memory for Obsidian and Qdrant

## 12.6 Review Support Agent

Responsibilities:

- Explain why a candidate was proposed
- Highlight uncertainty
- Show possible duplicates
- Recommend approve, merge, edit, or reject

---

# 13. Technology Architecture

## 13.1 Front Door

### Wispr Flow

Purpose:

- Immediate voice-to-text capture
- Low-friction dictation
- Desktop and mobile workflow compatibility
- Natural voice interaction before native RIOS voice capture is built

Important boundary:

Wispr Flow is an external capture interface. RIOS Lite must not depend on proprietary Wispr Flow APIs for core system operation unless an official supported integration becomes available.

The MVP should accept Wispr Flow output as ordinary text input.

## 13.2 Transcription

### OpenAI Whisper

Purpose:

- Transcribe uploaded audio
- Preserve raw transcript
- Support future native recording workflows

Potential later option:

- Whisper.cpp for local or private transcription

## 13.3 Operational Database

### Supabase

Purpose:

- Canonical operational records
- Authentication
- Tenant isolation
- Row-level security
- File metadata
- Review queue
- Workflow state
- Audit records

## 13.4 Analytics

### DuckDB / MotherDuck

Purpose:

- Analytical queries
- Historical analysis
- KPI reporting
- Relationship activity analysis
- Opportunity analysis
- Executive dashboards

Supabase remains the operational source of truth.

DuckDB / MotherDuck is a derived analytics layer, not the canonical transaction database.

## 13.5 Semantic Memory

### Qdrant

Purpose:

- Semantic transcript search
- Context retrieval
- Similar relationship discovery
- Similar opportunity discovery
- Agent memory retrieval

Every Qdrant record must include tenant isolation metadata.

## 13.6 Human-Readable Knowledge Vault

### Obsidian

Purpose:

- Context folder architecture
- Strategy documents
- Decisions
- Lessons learned
- Client operating knowledge
- Human-readable reports

Obsidian is not required to operate the MVP dashboard, but approved memory may be synchronized into the tenant vault.

---

# 14. Context Folder Architecture

Each tenant may maintain:

```text
/tenant-name
  /context
    SOUL.md
    CLIENT_PROFILE.md
    BUSINESS_MODEL.md
    OFFER_CONTEXT.md
    ICP_CONTEXT.md
    BRAND_VOICE.md
    STRATEGIC_OBJECTIVES.md
    CONSTRAINTS.md
    SUCCESS_METRICS.md

  /memory
    DECISIONS.md
    LESSONS_LEARNED.md
    CLIENT_PREFERENCES.md
    WORK_COMPLETED.md
    STRATEGIC_INSIGHTS.md

  /workflows
    VOICE_INTAKE.md
    RELATIONSHIP_REVIEW.md
    OPPORTUNITY_REVIEW.md
    TASK_REVIEW.md
    WEEKLY_EXECUTIVE_REVIEW.md

  /outputs
    /reports
    /briefings
    /recommendations
```

Agents must load the relevant tenant context before processing intake.

---

# 15. Review Queue UX

The review interface must display:

- Original text
- Cleaned text
- Extracted candidate
- Candidate type
- Proposed action
- Proposed fields
- Confidence score
- Existing possible matches
- Source evidence

Review actions:

- Approve as new
- Approve update
- Merge
- Edit and approve
- Reject
- Mark uncertain
- Return for reprocessing

Bulk approval may be added later but is not required for the first release.

---

# 16. Dashboard Requirements

## 16.1 Home Dashboard

Show:

- Voice Inbox entry point
- Pending review count
- Tasks due today
- Overdue tasks
- New opportunities
- Recent relationship updates
- Recent conversations

## 16.2 Relationship Dashboard

Show:

- Active relationships
- Dormant relationships
- Recent interactions
- Follow-up due
- Strategic contacts

## 16.3 Opportunity Dashboard

Show:

- Open opportunities
- Stage
- Priority
- Estimated value
- Next action
- Stalled opportunities

## 16.4 Intake and Transcript Search

Show:

- Date
- Source
- User
- Classification
- Processing status
- Linked people
- Linked organizations
- Linked opportunities
- Linked tasks

---

# 17. Security and Privacy Requirements

Mandatory controls:

- Tenant-level isolation
- Supabase row-level security
- Separate Qdrant filtering or collections per tenant
- Private audio storage
- Encrypted transport
- Secrets outside source code and vault files
- Role-based access
- Full audit trail
- Configurable retention policy
- Deletion capability for audio, transcript, and derived records

Sensitive data must not be used across tenants.

---

# 18. Compliance Boundary

RIOS Lite does not:

- Sell securities
- Solicit investors
- Negotiate investment terms
- Act as a broker-dealer
- Act as an exempt market dealer
- Receive transaction-based compensation
- Replace licensed legal, financial, mortgage, or compliance professionals

RIOS Lite provides:

- Software infrastructure
- Relationship intelligence
- Workflow automation
- Opportunity tracking
- Organizational memory
- Capital-readiness support
- Compliance-aware information management

Regulated workflows must remain under the control of appropriately licensed professionals.

---

# 19. MVP Acceptance Criteria

The MVP is accepted when a user can complete this end-to-end scenario:

1. Dictate a business update using Wispr Flow.
2. Paste or submit the resulting text into the RIOS Lite Voice Inbox.
3. View the preserved raw intake.
4. View the cleaned text.
5. View automatically extracted people, organizations, opportunities, interactions, and tasks.
6. Review possible duplicate matches.
7. Edit and approve extraction candidates.
8. Save approved records into Supabase.
9. View the created relationship and opportunity records.
10. View resulting follow-up tasks.
11. Search the source transcript semantically.
12. Trace every saved record back to the source intake and review decision.

A second accepted scenario must allow the user to upload an audio file and complete the same workflow using OpenAI Whisper transcription.

---

# 20. Success Metrics

## Product Metrics

- Percentage of voice or text intakes successfully processed
- Average time from intake to review-ready candidates
- Candidate approval rate
- Duplicate-detection accuracy
- Task extraction accuracy
- Opportunity extraction accuracy
- Search success rate
- Weekly active users
- Intakes per active user

## Business Outcome Metrics

- Follow-up commitments captured
- Relationships reactivated
- Opportunities identified
- Tasks completed
- Missed follow-ups reduced
- Organizational knowledge retained
- Revenue opportunities influenced

---

# 21. Release Phases

## Phase 1 — Voice-First Intake MVP

- Wispr Flow text intake
- Text paste
- Audio upload
- OpenAI Whisper transcription
- Cleaning
- Classification
- Extraction
- Review queue
- Supabase save
- Basic search
- Basic dashboard

## Phase 2 — Relationship Asset Management

- Relationship health scoring
- Dormancy alerts
- Introduction tracking
- Relationship maps
- Follow-up recommendations
- Obsidian memory synchronization

## Phase 3 — Opportunity Intelligence

- Opportunity scoring
- Stalled opportunity alerts
- Next-best action
- Strategic signal detection
- Executive opportunity reporting

## Phase 4 — Agent Execution

- Hermes scheduled workflows
- Approved task execution
- Report generation
- Research workflows
- Content and outreach preparation

## Phase 5 — Vertical Intelligence Packs

- Spectra Holdings
- MineTeck / Urban Mining
- Commercial Mortgage / Private Lending
- Capital Formation
- Commercial Real Estate
- Professional Advisory Services

---

# 22. Product Risks and Mitigations

## Risk: Transcription or dictation errors

Mitigation:

- Preserve original source
- Highlight uncertain language
- Require human review

## Risk: Incorrect entity creation

Mitigation:

- Candidate queue
- Duplicate matching
- Confidence scores
- No autonomous canonical save

## Risk: Cross-tenant data exposure

Mitigation:

- Tenant IDs on all records
- Row-level security
- Tenant-scoped semantic retrieval
- Automated isolation tests

## Risk: Product becomes too broad

Mitigation:

- Limit MVP to intake, extraction, review, canonical save, tasks, search, and dashboard

## Risk: Dependence on Wispr Flow

Mitigation:

- Treat Wispr Flow as an interchangeable capture interface
- Accept standard text input
- Retain OpenAI Whisper for native audio processing

---

# 23. Build Priority

Claude Code implementation order:

1. Supabase schema and row-level security
2. Tenant and user authentication
3. Voice Inbox UI
4. Wispr Flow text intake path
5. Audio upload and OpenAI Whisper path
6. Raw and cleaned transcript records
7. Intelligence extraction contracts
8. Entity and duplicate matching
9. Human review queue
10. Canonical save service
11. Task creation
12. Qdrant indexing and search
13. DuckDB / MotherDuck analytical sync
14. Basic dashboards
15. Audit trail
16. End-to-end tests

---

# 24. Final Product Definition

RIOS Lite is the voice-first front door to a broader Relationship Intelligence Operating System.

It gives business owners and relationship-driven teams a simple way to speak naturally, capture what happened, convert conversations into structured intelligence, and turn that intelligence into accountable action.

RIOS Lite transforms conversations from temporary communications into durable business assets.

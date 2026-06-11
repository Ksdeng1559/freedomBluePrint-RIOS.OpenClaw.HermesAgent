# RIOS Single Source of Truth

**Date:** June 10, 2026

## Summary

RIOS will be built as a voice-first Relationship Intelligence Operating System and Relationship Asset Management platform.

## Canonical Decision

- RIOS Lite is the first practical product.
- The voice module is the front door into RIOS.
- OpenAI Whisper is the initial transcription engine.
- Wispr Flow may be used as an immediate capture interface.
- Whisper.cpp may be evaluated later for local transcription.
- Supabase is the operational database and system of record.
- DuckDB / MotherDuck is the analytics layer.
- Qdrant is the semantic memory layer.
- Obsidian may remain the human-readable knowledge vault.
- Hermes Agent is the primary orchestrator.
- Specialist agents perform relationship, opportunity, task, and memory extraction.
- Human review is required before extracted intelligence becomes canonical.

## Reference Document

`docs/voice/RIOS-Voice-Module-Whisper-Build.md`

## Core RIOS Workflow

```text
Conversation
  ↓
Transcript
  ↓
Relationship Asset
  ↓
Opportunity
  ↓
Task
  ↓
Execution
```

## RIOS Voice Gateway Workflow

```text
Voice Source
  ↓
Audio File
  ↓
OpenAI Whisper
  ↓
Raw Transcript
  ↓
Transcript Cleaner
  ↓
RIOS Intelligence Extractor
  ↓
Extraction Candidates
  ↓
Human Review Queue
  ↓
Relationship Asset Register
  ↓
Supabase / DuckDB / Qdrant
  ↓
Tasks, Dashboards, Reports, Agent Workflows
```

## Canonical Data Flow

```text
Voice capture
  ↓
Transcription
  ↓
Extraction candidates
  ↓
Human review
  ↓
Canonical records
  ↓
Semantic indexing
  ↓
Agent execution
```

This review boundary prevents imperfect transcripts or model extractions from corrupting the Relationship Asset Register.

## Primary Pilot Use Cases

### Spectra Holdings

- Relationship Asset Management
- Capital source tracking
- Strategic partner tracking
- Opportunity intelligence
- Organizational memory

### MineTeck / Urban Mining

- Feedstock intelligence
- Capital formation support
- Strategic investor tracking
- Government funding tracking
- Pilot and partnership tracking

### Commercial Mortgage / Private Lending

- Lender relationship intelligence
- Borrower opportunity tracking
- Referral source intelligence
- Renewal and refinance tracking
- Compliance-aware conversation memory

## Relationship Asset Register

Core entities:

- People
- Organizations
- Opportunities
- Interactions
- Tasks

## Initial Agent Roles

- Hermes Agent
- Relationship Extractor
- Opportunity Extractor
- Task Agent
- Memory Agent

## System Responsibilities

### Supabase

Operational system of record for:

- People
- Organizations
- Opportunities
- Interactions
- Tasks
- Transcripts
- Review queue
- Workflow status
- Audit records

### DuckDB / MotherDuck

Analytics layer for:

- Portfolio-level reporting
- Historical analysis
- Workflow performance
- Opportunity trends
- Relationship activity
- Executive dashboards

### Qdrant

Semantic memory layer for:

- Transcript retrieval
- Similar relationship discovery
- Opportunity context retrieval
- Knowledge recall
- Agent context assembly

### Obsidian

Human-readable knowledge vault for:

- Context folders
- Strategy documents
- Client operating knowledge
- Decisions
- Lessons learned
- Reports
- Reference material

### Hermes Agent

Orchestration layer responsible for:

- Loading client and vertical context
- Coordinating specialist agents
- Scheduling workflows
- Reviewing task completion
- Writing approved results back to RIOS
- Generating summaries and executive reports

## Compliance Boundary

RIOS does not sell securities, solicit investors, negotiate investment terms, act as a broker-dealer, or receive transaction-based compensation.

RIOS provides:

- Software infrastructure
- Relationship intelligence
- Workflow automation
- Opportunity tracking
- Organizational memory
- Capital-readiness support

Any regulated activity must remain with appropriately licensed professionals and external legal or compliance advisors.

## MVP Scope

The first MVP must include:

1. Audio upload or voice capture intake
2. OpenAI Whisper transcription
3. Raw transcript storage
4. Clean transcript generation
5. Relationship intelligence extraction
6. Contact creation or matching
7. Organization creation or matching
8. Opportunity creation or matching
9. Follow-up task creation
10. Review queue before final save
11. Basic dashboard
12. Searchable transcript and memory records

## MVP Acceptance Criteria

The MVP is accepted when a user can:

1. Upload or capture a voice recording.
2. Generate and view a raw transcript.
3. Generate and view a cleaned transcript.
4. Review extracted people, organizations, opportunities, interactions, and tasks.
5. Approve, edit, or reject each extraction candidate.
6. Save approved records into Supabase.
7. Query structured analytics through DuckDB or MotherDuck.
8. Retrieve transcript and relationship context through Qdrant.
9. View an audit trail linking the source recording, transcript, approved records, and resulting tasks.

## Multi-Tenant Principle

Each client workspace must maintain strict isolation across:

- Operational records
- Audio files
- Transcripts
- Context folders
- Semantic collections
- Agent memory
- Credentials
- Audit logs

No client information may be retrieved or used in another client's workflow unless explicitly authorized.

## Product Sequence

### Phase 1 — RIOS Lite

Voice-first intake, transcript processing, relationship extraction, review, task generation, and basic search.

### Phase 2 — Relationship Asset Management

Relationship scoring, interaction history, follow-up recommendations, introduction tracking, and organizational memory.

### Phase 3 — Opportunity Intelligence

Opportunity scoring, next-best actions, pipeline risk, strategic signals, and executive reporting.

### Phase 4 — Vertical Intelligence Packs

Reusable context, workflow, agent, and reporting packs for:

- Spectra Holdings
- MineTeck / Urban Mining
- Commercial Mortgage / Private Lending
- Capital Formation
- Commercial Real Estate
- Professional Advisory Services

## Final Product Thesis

RIOS transforms relationship-driven businesses from memory-based execution into intelligence-based execution.

Relationships become assets. Conversations become intelligence. Intelligence becomes opportunities. Opportunities become action. Action becomes enterprise value.

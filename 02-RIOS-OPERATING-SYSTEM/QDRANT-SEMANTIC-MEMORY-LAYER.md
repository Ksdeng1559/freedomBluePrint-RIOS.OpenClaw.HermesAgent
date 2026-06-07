# Qdrant Semantic Memory Layer

## Purpose

Qdrant is the semantic recall layer for the Freedom Blueprint RIOS architecture.

It allows RIOS and Hermes to retrieve similar conversations, documents, decisions, opportunities, PRDs, research fragments, and client patterns across workspaces.

Qdrant does not replace Supabase, Markdown Vault, or GitHub.

## Architecture Rule

```text
Supabase = structured system of record
Markdown Vault = human-readable operating knowledge
Qdrant = semantic recall and similarity search
RIOS = intelligence and memory layer
Hermes = orchestration and mission control
OpenClaw = delegated execution layer
GitHub = evidence trail
Slack = governance and approvals
```

## Why Qdrant Exists in This Architecture

RIOS needs more than ordinary keyword search.

As the system grows, Hermes must be able to answer questions such as:

- Which past client project is most similar to this new request?
- Have we solved this problem before?
- What previous PRD, decision, or workflow should be reused?
- Which opportunity resembles this new market signal?
- Which outreach campaign or offer pattern matches this lead?
- What conversations, meeting notes, or research fragments are semantically related?

Qdrant stores embeddings and metadata pointers so Hermes can retrieve meaning, not just matching words.

## What Qdrant Stores

Qdrant stores vectorized representations of knowledge fragments.

Each Qdrant point should include:

```text
id
embedding
workspace_id
entity_type
entity_id
source_type
source_path
source_url
summary
tags
created_at
updated_at
confidence_score
```

Example entity types:

```text
client
company
contact
project
prd
decision
meeting_note
research_note
opportunity
workflow
offer
outreach_campaign
feature_request
```

## What Qdrant Does Not Store

Qdrant should not be treated as the system of record.

Do not use Qdrant as the primary store for:

- client records
- contact records
- opportunity pipeline data
- financial records
- source documents
- approval status
- pricing decisions
- legal or compliance records
- production workflow state

Those belong in Supabase, GitHub, Slack, or the Markdown Vault depending on the record type.

## Source-of-Truth Hierarchy

When there is a conflict between systems, use this hierarchy:

```text
1. Human-approved Slack decision or signed client document
2. GitHub issue, PR, commit, or architecture decision record
3. Supabase structured record
4. Markdown Vault operating document
5. Qdrant semantic retrieval result
6. Raw transcript, scrape, or unverified note
```

Qdrant helps find relevant material. It does not automatically make retrieved material authoritative.

## Recommended Collection Design

Use separate collections only when search behavior, retention, or access control differs.

Suggested MVP collections:

```text
rios_knowledge
rios_conversations
rios_prds
rios_opportunities
rios_outreach
```

For a simpler MVP, begin with one collection:

```text
rios_memory
```

Use payload metadata to filter by workspace, client, project, entity type, and source.

## RIOS Memory Flow

```text
1. Capture source material
   - meeting note
   - transcript
   - PRD
   - research summary
   - outreach result
   - decision log

2. Store structured record in Supabase or Markdown Vault

3. Chunk important text into retrievable fragments

4. Generate embedding

5. Store embedding and metadata pointer in Qdrant

6. Hermes retrieves related memory during planning or execution

7. Human approves high-impact decisions before action
```

## Hermes Usage Pattern

Hermes should use Qdrant when it needs to:

- retrieve similar prior work
- enrich a mission with background context
- compare a new opportunity against past patterns
- find reusable PRDs, offers, or workflows
- detect duplicated work
- support agent memory across workspaces

Hermes should not use Qdrant alone to:

- approve spending
- send outbound messages
- make legal, financial, or compliance claims
- override a human-approved decision
- change production systems

## Freedom Blueprint Stage Placement

Qdrant belongs in Stage 2 of the Freedom architecture.

```text
Stage 1: Build revenue infrastructure and first client systems
Stage 2: Add reusable memory, semantic recall, and agent automation
Stage 3: Convert repeated patterns into productized systems and SaaS modules
```

Implementing Qdrant early is useful because it creates a stable memory abstraction before the system becomes large.

## Implementation Recommendation

Add Qdrant behind a MemoryService abstraction.

```text
MemoryService
├── write_memory()
├── search_memory()
├── link_to_supabase_record()
├── retrieve_similar_projects()
├── retrieve_related_decisions()
└── retrieve_reusable_prds()
```

This prevents Hermes, OpenClaw, and future workers from being tightly coupled to one vector database implementation.

If Qdrant is later replaced or supplemented by another vector store, only the MemoryService adapter needs to change.

## Initial Docker Command

```bash
docker run -p 6333:6333 qdrant/qdrant
```

## Operating Principle

```text
Supabase stores facts.
Markdown stores operating knowledge.
Qdrant stores meaning.
Hermes decides what context matters.
Humans approve high-impact action.
```

## Final Decision

Qdrant is approved as the semantic memory layer for the Freedom Blueprint RIOS architecture.

It is optional for the earliest prototype, but recommended early in the platform foundation to reduce future rework and support reusable agent memory across client systems, offers, PRDs, and venture studio workflows.

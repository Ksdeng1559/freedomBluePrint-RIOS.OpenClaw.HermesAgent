# Approval Gates

## Purpose

Approval gates define which actions require human approval before Hermes, OpenClaw, Claude Code, Codex, or any automation proceeds.

Slack is the visible approval trail.

RIOS is the system of record.

Hermes enforces the gate.

## Actions Requiring Approval

Hermes must require approval before:

```yaml
approval_required_for:
  - production_deployment
  - outbound_client_message
  - cold_outreach_campaign_launch
  - investor_document_send
  - client_proposal_send
  - invoice_send
  - pricing_change
  - offer_scope_change
  - legal_claim
  - financial_claim
  - compliance_claim
  - database_schema_change
  - production_database_change
  - delete_file_or_record
  - access_permission_change
  - API_key_or_secret_rotation
  - public_website_publish
  - client_facing_asset_update
```

## Actions That Can Run Without Approval

```yaml
approval_not_required_for:
  - internal_research
  - draft_creation
  - summarization
  - internal_report_generation
  - local_markdown_file_update
  - first_pass_signal_scan
  - competitor_scan
  - lead_enrichment_draft
  - QA_draft_notes
  - backlog_item_creation
  - non_production_code_experiment
```

## Approval Flow

```text
Worker output ready
   |
   v
Hermes reviews risk level
   |
   v
Approval required?
   |
   |-- No -> Continue workflow and update RIOS
   |
   |-- Yes -> Post to #signoffs
              |
              v
           Human decision
              |
              |-- Approve -> Hermes proceeds
              |-- Reject -> Hermes stops task and records reason
              |-- Defer -> Hermes moves to backlog
              |-- Request Changes -> Hermes creates revision task
```

## Approval Request Format

```yaml
approval_request:
  approval_id: APP-YYYY-NNN
  mission_id: mission-id
  cr_id: optional-change-request-id
  project: project-name
  requested_by: hermes
  approval_type: deployment | proposal | outbound | pricing | database | client_asset | other
  summary: short description
  business_reason: why approval is needed
  risk_level: low | medium | high
  artifact_links:
    - GitHub PR
    - document link
    - deployment preview
  qa_status: not_started | partial | passed | failed
  decision_options:
    - approve
    - reject
    - defer
    - request_changes
  approver: human-name
  decision_timestamp: YYYY-MM-DD HH:MM
```

## Slack Sign-Off Message

```text
APPROVAL REQUIRED
Approval ID: APP-YYYY-NNN
Mission: {mission_id}
Project: {project}
Type: {approval_type}
Risk: {risk_level}

Summary:
{summary}

Business Reason:
{business_reason}

Artifact Links:
- {link_1}
- {link_2}

QA Status:
{qa_status}

Decision Needed:
Approve / Reject / Defer / Request Changes
```

## Role Rules

### ChatGPT

May recommend whether approval is required when the issue affects strategy, positioning, pricing, risk, investor logic, or client expectation.

### Hermes

Owns enforcement of approval gates.

Hermes must not proceed when approval is required and missing.

### OpenClaw

Cannot approve anything.

OpenClaw can only produce worker outputs and return them to Hermes.

### Claude Code / Codex

Can create code and PRs, but cannot deploy production changes without sign-off.

### Human Operator

Final approver for all high-impact actions.

## Final Rule

If an action could create external impact, financial risk, client confusion, reputational risk, data risk, or production instability, require Slack approval before proceeding.

# 05 — Approved Execution and Distribution

**Inputs:** decision_card, Battle Card, approved Client Brain claims, current suppression and contact permissions.
**Process:** prepare context-aware conversational messaging as the LAST stage of ICM; prove relevance rather than superficial personalization. Request approval for recipient, channel and exact message content; execute only when approval and legally valid contact basis remain current.
**Outputs:** `outreach_draft`, `approval_record`, `send_receipt` or documented non-send.
**Evidence:** approver, message hash, send-time compliance check, content/policy versions.
**Success:** no unapproved sends and CRM attribution identifiers attached.
**Allowed tools:** draft generation; outbound sender only behind verified approval gate.
**Review gate:** human approval mandatory for external sends and commercial commitments.
**Escalation:** missing consent, unsubscribe or stale approval -> do not send.
**Next:** `06_feedback`.

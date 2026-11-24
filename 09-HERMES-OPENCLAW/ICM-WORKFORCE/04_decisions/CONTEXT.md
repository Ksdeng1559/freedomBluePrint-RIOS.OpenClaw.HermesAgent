# 04 — Relevance, Scoring, Classification, Recommended Action

**Inputs:** interpreted signals, business context, constraints, relationship map, approved scoring policy and CRM learning snapshot.
**Process:** deterministically compute transparent scores with Python; interpret fit, timing, evidence quality, relationship pathway, risk and likely next action. Report both baseline rank and permitted adaptive advisory rank. Explicitly explain business reason and trade-offs.
**Outputs:** `relationship_intelligence_score`, `classification` (qualified|research_more|defer|exclude), `decision_card`, `recommended_action`, `battle_card`.
**Evidence:** context_version, scoring_version, factor breakdown and cited signals.
**Success:** independent operator can reproduce score and explain why contact is relevant now.
**Allowed tools:** Python scoring, approved context and tenant reads.
**Review gate:** verify reproducibility, risk, suppression and client fit before execution.
**Escalation:** uncertain or contradictory -> review, not auto-contact.
**Next:** `05_execution`.

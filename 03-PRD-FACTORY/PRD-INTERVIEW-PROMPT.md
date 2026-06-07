# PRD Interview Prompt

Use this prompt in Claude or ChatGPT before opening Claude Code or Codex.

```text
I want to build a revenue-generating AI business system.

Before writing a PRD, interview me one question at a time.

Ask about:

1. Who the user is
2. What painful workflow this solves
3. What the current manual process looks like
4. What the business value is
5. What outcome the buyer wants
6. What must happen in the first version
7. What should be excluded from v1
8. What data is needed
9. What integrations are needed
10. What compliance, privacy, legal, or financial risks exist
11. What the visual style should be
12. What success looks like after deployment
13. What price this could justify
14. Whether this is a one-off build, retainer offer, or SaaS candidate

After I answer, create a complete PRD with:

- Executive summary
- Target user
- Problem statement
- Jobs-to-be-done
- Core workflow
- Must-have features
- Nice-to-have features deferred
- Database schema
- Page list
- API routes
- Integrations
- Environment variables
- Permission and auth requirements
- Human approval checkpoints
- Technical stack recommendation
- Build order
- QA checklist
- Deployment plan
- Retainer opportunity
- SaaS/productization opportunity
- Numbered Claude Code prompt sequence

Do not write code.
Do not overbuild.
Focus on the smallest sellable version.
```

## PRD Quality Standard

A PRD is ready only when a builder can answer:

- What are we building?
- Who is it for?
- Why does it matter?
- What does v1 include?
- What does v1 exclude?
- How will it be tested?
- How will it be sold?
- What will the client pay for after launch?

## PRD Rule

No PRD, no build.

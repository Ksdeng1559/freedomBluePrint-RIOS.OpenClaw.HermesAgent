# Claude Code / Codex Build Loop

## Rule

Do not freestyle directly into the coding agent.

Planning agent writes the prompt. Builder agent executes the prompt. Planning agent reviews the result.

## Standard Loop

```text
1. Rough idea
2. PRD interview
3. PRD approval
4. Numbered build prompts
5. Execute Prompt 1 in Claude Code / Codex
6. Copy output, error, or screenshot back to planning agent
7. Planning agent writes next prompt or fix prompt
8. Repeat until deployed
```

## Build Prompt Standard

Each build prompt must have:

- One job only
- Clear files to create or modify
- Acceptance criteria
- Instructions to run tests or dev server
- Instructions to report what changed

## First Prompt Template

```text
Read the PRD below carefully.

Before writing code, do the following:

1. Confirm the recommended tech stack
2. Propose the folder structure
3. Identify risks or missing information
4. Create the build order
5. Ask clarifying questions if needed

Wait for my approval before creating files.

[PASTE PRD]
```

## Feature Build Prompt Template

```text
Build only the following feature:

Feature:
[FEATURE NAME]

Requirements:
[REQUIREMENTS]

Files to create or update:
[FILES]

Acceptance criteria:
[WHAT DONE MEANS]

After completing:
1. List files changed
2. List commands run
3. Explain how to test it
4. Identify remaining issues
```

## QA Prompt Template

```text
Review the current implementation against the PRD.

Check for:

- Missing requirements
- Broken flows
- Security issues
- Environment variable issues
- Accessibility problems
- Mobile responsiveness
- Database/schema mismatch
- Error handling gaps
- Deployment risks

Return:

1. Pass/fail summary
2. Critical fixes
3. Recommended polish
4. Exact fix prompt I can run next
```

## Commit Standard

Commit after each major milestone:

```text
feat: add lead capture form
feat: add admin dashboard
fix: resolve database connection issue
docs: update deployment guide
```

## Build Completion Checklist

- App runs locally
- Environment variables documented
- Database schema created
- User-facing flow tested
- Admin flow tested
- Error states tested
- README updated
- Deployment guide added
- Retainer/handoff notes created

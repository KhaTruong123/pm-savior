# Quick Plan — No Research

Think. Plan directly from the inputs at hand.

## Your mission

<task>
$ARGUMENTS
</task>

## Workflow

1. If creating new: create the plan directory `./plans/{YYYY-MM-DD}-{slug}/` (e.g., `mkdir -p ./plans/2026-06-12-b2b-pricing-tier-launch`). If reusing an existing plan, work in that directory.
2. Read every input the user provided or referenced: briefs, meeting notes, PRD drafts, decision logs, prior research.
3. Break the initiative into 2–6 phases. Each phase = one coherent deliverable or milestone (e.g., "stakeholder map", "draft PRD", "pilot checklist").
4. Write `plan.md` plus one `phase-XX-{name}.md` per phase (specification below).
5. Ask the user to review the plan.

## Output Requirements

**Plan Directory Structure**

```
./plans/{YYYY-MM-DD}-{slug}/
├── plan.md
├── phase-01-{phase-name}.md
├── phase-02-{phase-name}.md
└── ...
```

**Plan File Specification**

Every `plan.md` MUST start with YAML frontmatter:

```yaml
---
title: "{Brief title}"
description: "{One sentence summary}"
status: pending          # pending | in-progress | completed
priority: P2
effort: {sum of phases, e.g., 3 days}
tags: [relevant, tags]
created: {YYYY-MM-DD}
---
```

- Keep `plan.md` generic and under 80 lines: list each phase with its status and a link to its phase file, plus key dependencies between phases.
- Each `phase-XX-{phase-name}.md` contains the following sections in order:
  1. **Context Links** — parent plan, dependencies on other phases, input documents
  2. **Overview** — priority, current status, one-paragraph description
  3. **Key Insights** — what matters most, critical considerations
  4. **Requirements** — what this phase must deliver
  5. **Approach** — how the deliverable will be structured and produced
  6. **Related Documents** — inputs to read, artifacts to produce (with paths)
  7. **Work Steps** — detailed, numbered steps
  8. **Todo** — checkbox list (`- [ ]`) for tracking
  9. **Success Criteria** — definition of done, how to verify it
  10. **Risks** — what could go wrong + mitigation
  11. **Next Steps** — dependencies, follow-up work

## Important Notes

- **IMPORTANT: Do not** start executing the plan. Planning only — execution belongs to `pm-cook`.
- Keep it concise; sacrifice grammar for the sake of concision.
- List unresolved questions at the end of `plan.md`, if any.

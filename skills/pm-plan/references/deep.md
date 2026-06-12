# Deep Plan — Research First

Think harder. Research before planning.

## Your mission

<task>
$ARGUMENTS
</task>

## Workflow

1. If creating new: create the plan directory `./plans/{YYYY-MM-DD}-{slug}/`. If reusing an existing plan, work in that directory.
2. Research the initiative before planning (max 2 focused research passes, each on a different aspect — e.g., market/competitors, users/stakeholders, vendors, regulations, internal precedents):
   - Use WebSearch and any documents the user provides.
   - Save each research note to `{plan-dir}/research/research-XX-{topic}.md`, ≤150 lines, with source citations.
3. Read every input the user provided or referenced: briefs, meeting notes, PRD drafts, decision logs.
4. Synthesize research + inputs into a phased plan: write `plan.md` plus one `phase-XX-{name}.md` per phase, following the exact output specification in `references/quick.md` (frontmatter, ≤80-line overview, 11 phase sections).
5. Ask the user to review the plan.

## Post-Plan Validation (Optional)

After plan creation, offer a validation interview to confirm decisions before execution:

- Ask the user: "Validate this plan with a brief interview?" → Yes (Recommended) / No
- If yes → follow `references/validate.md` with this plan's path.

## Output Requirements

**Plan Directory Structure**

```
./plans/{YYYY-MM-DD}-{slug}/
├── research/
│   ├── research-01-{topic}.md
│   └── ...
├── plan.md
├── phase-01-{phase-name}.md
└── ...
```

- Research notes: concise (≤150 lines each), cover the requested topic, cite sources.
- `plan.md` frontmatter and `phase-XX` section structure: identical to `references/quick.md`.

## Important Notes

- **IMPORTANT: Do not** start executing the plan. Planning only — execution belongs to `pm-cook`.
- Keep reports concise; sacrifice grammar for the sake of concision.
- List unresolved questions at the end of `plan.md`, if any.

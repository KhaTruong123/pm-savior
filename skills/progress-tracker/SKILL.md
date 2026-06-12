---
name: progress-tracker
description: "Track progress across plan phases, generate a status report, and resume multi-session work. Use when asked for 'plan status', 'where are we', 'progress report', 'what's done', 'resume the plan', or 'what's left in phase X'."
license: MIT
attribution: "Adapted from ClaudeKit Engineer's project-management skill — https://github.com/claudekit/claudekit-engineer (MIT)"
argument-hint: "[plan path or plan name]"
metadata:
  author: kelvin
  version: "1.0.0"
---

# Progress Tracker

Check the status of an active plan, generate a progress report, and identify what is done versus what remains — so you can pick up exactly where you left off across sessions.

## Your mission

<task>
$ARGUMENTS
</task>

## When to Use

- Starting a new session and need to resume a plan
- Checking completion % before a stakeholder update
- Generating a quick status report for a Slack update or meeting
- Verifying all phases are complete before closing a plan

---

## How Plans Are Tracked

Plans live in `./plans/` as directories with markdown files. Progress is tracked via checkboxes:

```
[ ] = not started
[x] = done
```

Phase files follow the pattern: `phase-NN-description.md`
The overview file is always: `plan.md`

---

## Workflow

1. **Find the plan** — if no path is given, list `./plans/*/plan.md` files and ask which one
2. **Read `plan.md`** — get the overall status, phases, and priorities
3. **Read each `phase-NN-*.md`** — count `[x]` vs `[ ]` items
4. **Compute completion %** per phase and overall
5. **Identify blockers** — unchecked items with no clear owner or unresolved dependencies
6. **Generate report** — concise table + next actions

---

## Output Format

```
## Progress Report: [Plan Name]

**Generated:** [date]
**Plan path:** ./plans/{slug}/

### Phase Summary

| Phase | Status | Done | Total | % |
|-------|--------|------|-------|---|
| Phase 01 — Research | Complete | 5 | 5 | 100% |
| Phase 02 — Scaffold | Complete | 4 | 4 | 100% |
| Phase 03 — Core skills | In Progress | 6 | 10 | 60% |
| Phase 04 — Supporting skills | Not started | 0 | 8 | 0% |

**Overall: 15 / 27 tasks done (56%)**

### Current Phase Detail (Phase 03)

Done:
- [x] Port brainstorm skill
- [x] Port plan skill

In Progress / Remaining:
- [ ] Port research skill
- [ ] Port sequential-thinking skill

### Blockers
- None identified / [describe if any]

### Next Actions
1. [First unchecked item in current phase]
2. [Second unchecked item]

### Resume Command
Continue with: `/pm-cook plans/{slug}/phase-03-description.md`
```

---

## Updating Plan Status

When asked to mark items complete, update the relevant phase file directly:
- `[ ]` → `[x]` for completed items
- Update the phase status header from `Pending` → `In Progress` → `Complete`
- Update `plan.md` phase status table to match

**Never mark a phase complete unless all its `[ ]` items are checked.**

---

## Example Invocations

```
/progress-tracker
/progress-tracker plans/260612-1326-pm-ba-skill-pack-extraction/
/progress-tracker "what's left in phase 4"
/progress-tracker "mark offramp-kyc research as done and update the plan"
```

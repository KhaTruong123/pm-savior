# Unified Workflow Steps

All modes share core steps with mode-specific variations. Progress is tracked in the plan files themselves — the phase Todo checkboxes are the source of truth.

## Step 0: Intent Detection & Setup

1. Parse input with `intent-detection.md` rules
2. Log detected mode: `✓ Step 0: Mode [X] - [reason]`
3. Resolve plan + target phase (see Plan & Phase Resolution in `intent-detection.md`)
4. Read `plan.md` and the target `phase-XX-*.md` **fully** — Requirements, Work Steps, Todo, Success Criteria

**Output:** `✓ Step 0: Mode [interactive|auto|fast|no-review|execute] - plan: [path], phase: [XX]`

## Step 1: Gather Inputs (skip if fast mode)

- Read every document listed in the phase's Context Links / Related Documents
- If a required input is missing or unreadable, ask the user for it — don't guess at content you don't have
- Clarify ambiguous requirements with `AskUserQuestion` (max 4 questions)

**Output:** `✓ Step 1: Inputs gathered - [N] documents read`

### [Gate 1] Pre-Production (skip if auto mode)
- Summarize: what this phase will produce, from which inputs, per which success criteria
- Ask: "Proceed to produce the deliverables?" / "Adjust scope first" / "Abort"
- **Auto mode:** skip this gate

## Step 2: Planning (only if no plan exists)

- HARD-GATE: create a plan first using the `pm-plan` skill (quick or deep), get user approval, then return here
- If a plan already exists: skip — never re-plan an approved plan

**Output:** `✓ Step 2: Plan ready - [N] phases`

## Step 3: Artifact Production

**All modes:**
- Produce each deliverable the phase promises, following its Work Steps in order
- Scoping discipline: produce ONLY what the phase asks — no bonus sections, no unrequested artifacts
- Save artifacts where the phase's Related Documents section says; if unspecified, default to an `artifacts/` folder inside the plan directory (e.g., `./plans/2026-06-12-pricing-launch/artifacts/`)
- Mark each Todo item `[x]` in the phase file as it completes
- One phase at a time — never start the next phase before this one is finalized

**Output:** `✓ Step 3: Produced [N] artifacts - [X/Y] todo items complete`

## Step 4: Completeness Check

- Re-read the phase's Requirements and promised deliverables
- Compare against what was actually produced: list every promised section/artifact and mark present/missing
- Fix anything missing before proceeding — no silent omissions, no "TBD" left without flagging it

**Output:** `✓ Step 4: Completeness [N/N sections present]`

## Step 5: Self-Test Against Success Criteria

- Walk the artifact against the phase's Success Criteria, one criterion at a time
- Output a table: criterion → pass/fail → evidence (quote or pointer into the artifact)
- Fix every fail and re-check
- **Forbidden:** rewording a criterion to make it pass, skipping a criterion, declaring pass without evidence

**Output:** `✓ Step 5: Self-test [X/X criteria passed]`

### [Gate 2] Post-Production (skip if auto mode)
- Present the artifacts and the self-test table
- Ask: "Proceed to quality review?" / "Request changes" / "Abort"
- **Auto mode:** skip this gate

## Step 6: Quality Review (skip if no-review mode)

- Run the document quality checklist from `review-cycle.md`: clarity, completeness, testability, consistency, stakeholder readiness, scope
- Score /10, list critical issues / warnings / suggestions

**Interactive/execute/fast:** interactive review cycle (max 3) — see `review-cycle.md`; requires user approval
**Auto:** auto-approve if score ≥9.5 AND 0 critical; auto-fix critical (max 3 cycles); escalate to user after 3 failed cycles
**Fast:** simplified review, no fix loop — user approves or aborts

**Output:** `✓ Step 6: Review [score]/10 - [Approved|Auto-approved]`

## Step 7: Finalize (MANDATORY — never skip)

1. **Phase file sync:** mark every completed Todo item `[ ] → [x]`; set the phase's Overview status (`pending` → `in-progress` → `completed`, same vocabulary as plan.md frontmatter)
2. **Full plan sync-back:** sweep ALL `phase-XX-*.md` files in the plan directory — backfill any stale completed checkboxes from earlier phases, then update `plan.md` phase-table statuses and frontmatter `status` from the **actual checkbox state**, not just the current phase
3. **Wrap-up summary:** artifacts produced (with paths), success criteria results, open questions
4. **Offer export:** ask if the user wants artifacts saved/copied elsewhere (shared folder, paste-ready format)

**Auto mode:** continue to the next phase automatically, restarting from **Step 1**.
**Other modes:** ask the user before starting the next phase.

**Output:** `✓ Step 7: Finalized - phase [XX] complete - plan status synced`

## Final Wrap-Up (after the last phase)

- Plan-level summary: every phase's status, all artifacts with paths, unresolved questions
- Set `plan.md` frontmatter `status: completed` only when every phase's checkboxes are complete

## Mode-Specific Flow Summary

Legend: `[G]` = approval gate (user decision required)

```
interactive: 0 → 1 → [G] → 3 → 4 → 5 → [G] → 6(user) → 7 → next phase (ask)
auto:        0 → 1 → 3 → 4 → 5 → 6(auto) → 7 → next phase (NO stops)
fast:        0 → skip → 3 → 4 → 5 → [G] → 6(simple) → 7 → next phase (ask)
no-review:   0 → 1 → [G] → 3 → 4 → 5 → [G] → skip → 7 → next phase (ask)
execute:     0 → 1 → [G] → 3 → 4 → 5 → [G] → 6(user) → 7 → next phase (ask)
```

(Step 2 inserts before Step 3 only when no plan exists.)

## Critical Rules

- Never skip steps without mode justification
- Steps 4, 5, and 7 run in EVERY mode — completeness, self-test, and finalize are non-negotiable
- Never mark a Todo item `[x]` for work not actually done
- Statuses are derived from checkbox state, never asserted from memory — a phase may only be marked `completed` when every one of its Todo items is `[x]`
- All step outputs follow the format: `✓ Step [N]: [status] - [metrics]`

# Intent Detection Logic

Detect user intent from natural language and route to the appropriate workflow mode.

## Detection Algorithm

```
FUNCTION detectMode(input):
  # Priority 1: Explicit flags (override all)
  IF input contains "--fast": RETURN "fast"
  IF input contains "--auto": RETURN "auto"
  IF input contains "--no-review": RETURN "no-review"

  # Priority 2: Plan path detection
  IF input matches path pattern (./plans/*, plan.md, phase-*.md):
    RETURN "execute"

  # Priority 3: Keyword detection (case-insensitive)
  keywords = lowercase(input)

  IF keywords contains ["fast", "quick", "rapidly", "asap"]:
    RETURN "fast"

  IF keywords contains ["trust me", "auto", "just do it"]:
    RETURN "auto"

  IF keywords contains ["no review", "skip review", "without review"]:
    RETURN "no-review"

  # Default: interactive workflow
  RETURN "interactive"
```

## Plan & Phase Resolution

After mode detection, resolve WHICH plan and WHICH phase:

1. **Explicit phase path** (`phase-02-*.md`) → execute that phase only, then ask about the next
2. **Plan directory or `plan.md` path** → read the phase table, start from the first phase not marked completed
3. **"continue the plan" / "continue phase N"** → look in `./plans/` for the most recent plan with unfinished phases; confirm with the user if ambiguous
4. **Natural-language task, no plan exists** → HARD-GATE applies: create a plan first via the `pm-plan` skill

## Mode Behaviors

| Mode | Skip Clarification | Skip Quality Review | Approval Gates | Auto-Approve |
|------|--------------------|---------------------|----------------|--------------|
| interactive | ✗ | ✗ | **Yes (stops)** | ✗ |
| auto | ✗ | ✗ | **No (skips)** | ✓ (score ≥9.5) |
| fast | ✓ | simplified | Yes (stops) | ✗ |
| no-review | ✗ | ✓ | Yes (stops) | ✗ |
| execute | ✓ | ✗ | Yes (stops) | per plan |

**Approval Gates:** user checkpoints between major steps (see `workflow-steps.md`).
- All modes EXCEPT `auto` stop at gates for user approval.
- `auto` mode is the only mode that runs continuously without stopping.

## Examples

```
"Execute plans/2026-06-12-pricing-launch/phase-02-draft-prd.md"
→ Mode: execute (path detected, stops at gates)

"Implement the market research plan"
→ Mode: execute (plan reference; resolve plan dir, start at first open phase)

"Quick draft of the stakeholder update"
→ Mode: fast ("quick" keyword; HARD-GATE still requires a plan)

"Work through the whole launch plan, trust me"
→ Mode: auto (NO STOPS, executes all phases continuously)

"Produce phase 3 deliverables --no-review"
→ Mode: no-review (skips quality review, still stops at gates)
```

**Note:** only the `--auto` flag or "trust me"/"auto" keywords enable continuous execution.

## Conflict Resolution

When multiple signals are detected, priority order:
1. Explicit flags (`--fast`, `--auto`, `--no-review`)
2. Path detection (plan/phase files)
3. Keywords in text
4. Default (interactive)

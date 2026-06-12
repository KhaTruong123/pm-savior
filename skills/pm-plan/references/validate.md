# Validate Plan — Critical Questions Interview

## Your mission

Interview the user with critical questions to validate assumptions, confirm decisions, and surface potential issues in a plan **before execution begins**.

## Plan Resolution

1. If a plan path was provided → use it
2. Else look in `./plans/` for the most recently created plan directory and confirm it with the user
3. If no plan found → ask the user to specify a path or create one first (`pm-plan` quick/deep)

## Configuration

Defaults (no external configuration needed):
- Question count: 3–8 (fewer is fine for simple plans)
- Each question: 2–4 concrete options, recommended option marked

## Workflow

### Step 1: Read Plan Files

Read the plan directory:
- `plan.md` — overview and phase list
- `phase-*.md` — all phase files
- Look for decision points, assumptions, risks, trade-offs

### Step 2: Extract Question Topics

Scan plan content for:

| Category | Keywords to detect |
|----------|-------------------|
| **Approach** | "approach", "format", "structure", "framework", "channel", "audience" |
| **Assumptions** | "assume", "expect", "should", "will", "must", "default" |
| **Trade-offs** | "trade-off", "vs", "alternative", "option", "choice", "either/or" |
| **Risks** | "risk", "might", "could fail", "dependency", "blocker", "concern" |
| **Scope** | "phase", "MVP", "future", "out of scope", "nice to have" |

### Step 3: Generate Questions

For each detected topic, formulate a concrete question:

**Question format rules:**
- Each question must have 2–4 concrete options
- Mark the recommended option with a "(Recommended)" suffix
- An "Other" option is added automatically — don't add it yourself
- Questions should surface implicit decisions

**Example questions:**

```
Category: Assumptions
Question: "The plan assumes legal review is not needed before the pilot. Is this correct?"
Options:
1. Yes, legal review not needed for the pilot
2. No, get legal sign-off first (Recommended)
3. Defer to a later phase
```

```
Category: Scope
Question: "Phase 2 includes both the pricing page copy and the sales one-pager. Keep both in scope?"
Options:
1. Keep both (Recommended) - They share the same messaging work
2. Pricing page only - One-pager moves to a new phase
3. One-pager only
```

### Step 4: Interview User

Use the `AskUserQuestion` tool to present questions.

**Rules:**
- Stay within the 3–8 question range
- Group related questions when possible (max 4 questions per tool call)
- Focus on: assumptions, risks, trade-offs, approach, scope

### Step 5: Document Answers

After collecting answers, update the plan:

1. Add a `## Validation Summary` section to `plan.md`:

```markdown
## Validation Summary

**Validated:** {date}
**Questions asked:** {count}

### Confirmed Decisions
- {decision 1}: {user choice}
- {decision 2}: {user choice}

### Action Items
- [ ] {any changes needed based on answers}
```

2. If answers require plan changes, note them in Action Items but **do not modify phase files** — just document what needs updating.

## Output

After validation completes, provide a summary:
- Number of questions asked
- Key decisions confirmed
- Any items flagged for plan revision
- Recommendation: proceed to execution (`pm-cook`) or revise the plan first

## Important Notes

- **IMPORTANT:** Only ask questions about genuine decision points — don't manufacture artificial choices.
- **IMPORTANT:** If the plan is simple with few decisions, it's okay to ask fewer than 3 questions.
- **IMPORTANT:** Prioritize questions that could change the deliverables significantly.

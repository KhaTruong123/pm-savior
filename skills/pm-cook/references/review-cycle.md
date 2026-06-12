# Document Quality Review Cycle

Interactive review-fix cycle used before finalizing a phase's artifacts.

## Quality Checklist (score each /10, report the overall)

| Dimension | What to check |
|-----------|---------------|
| **Clarity** | Unambiguous language; no undefined jargon; one possible interpretation per statement |
| **Completeness** | Every promised section present; no silent "TBD"; all inputs accounted for |
| **Testability** | Requirements and acceptance criteria are verifiable — a reader could check pass/fail |
| **Consistency** | No contradictions with the plan, confirmed decisions, or earlier phases |
| **Stakeholder readiness** | Right level for the audience; actionable next steps; ready to share without a walkthrough |
| **Scope** | Nothing beyond what the phase asked (scope-creep check); nothing the phase asked left out |

## Interactive Cycle (max 3 cycles)

```
cycle = 0
LOOP:
  1. Run the quality checklist → score, critical_count, warnings, suggestions

  2. DISPLAY FINDINGS:
     ┌─────────────────────────────────────────┐
     │ Quality Review Results: [score]/10      │
     ├─────────────────────────────────────────┤
     │ Summary: [what was produced],           │
     │ self-test [X/X criteria passed]         │
     ├─────────────────────────────────────────┤
     │ Critical Issues ([N]): MUST FIX         │
     │  - [issue] at [artifact/section]        │
     │ Warnings ([N]): SHOULD FIX              │
     │  - [issue] at [artifact/section]        │
     │ Suggestions ([N]): NICE TO HAVE         │
     │  - [suggestion]                         │
     └─────────────────────────────────────────┘

  3. AskUserQuestion (header: "Review & Approve"):
     IF critical_count > 0:
       - "Fix critical issues" → fix, re-run self-test, cycle++, LOOP
       - "Fix all issues" → fix all, re-run self-test, cycle++, LOOP
       - "Approve anyway" → PROCEED
       - "Abort" → stop
     ELSE:
       - "Approve" → PROCEED
       - "Fix warnings/suggestions" → fix, cycle++, LOOP
       - "Abort" → stop

  4. IF cycle >= 3 AND user selects fix:
     → "⚠ 3 review cycles completed. Final decision required."
     → AskUserQuestion: "Approve with noted issues" / "Abort workflow"
```

## Auto-Handling Cycle (for auto mode)

```
cycle = 0
LOOP:
  1. Run the quality checklist → score, critical_count, warnings

  2. IF score >= 9.5 AND critical_count == 0:
     → Auto-approve, PROCEED

  3. ELSE IF critical_count > 0 AND cycle < 3:
     → Auto-fix critical issues
     → Re-run self-test against success criteria
     → cycle++, LOOP

  4. ELSE IF critical_count > 0 AND cycle >= 3:
     → ESCALATE TO USER

  5. ELSE (no critical, score < 9.5):
     → Approve with warnings logged, PROCEED
```

## Critical Issues Definition

- An ambiguous core requirement (two readers would build different things)
- An acceptance criterion that cannot be verified
- A contradiction with a confirmed decision or an earlier phase
- A mandatory section missing or silently stubbed
- Scope expansion the user never approved
- A factual claim with no source when the phase requires evidence

## Output Formats

- Waiting: `⏸ Step 6: Reviewed - [score]/10 - WAITING for approval`
- After fix: `✓ Step 6: [old]/10 → Fixed [N] issues → [new]/10 - Approved`
- Auto-approved: `✓ Step 6: Reviewed - 9.8/10 - Auto-approved`
- Approved: `✓ Step 6: Reviewed - [score]/10 - User approved`

# Example: Initiative Scoping with Sequential Thinking

**Problem**: Leadership asks to "improve customer onboarding" — fuzzy initiative, no defined scope.

## Sequential Thinking Approach

```
Thought 1/4: Initial assessment

"Improve onboarding" is vague. Complaints scattered across accounts.
Instinct: launch a big onboarding revamp program.
Options: full journey redesign, new training portal, dedicated onboarding team, automation.

Next: Define what "improved" means

Thought 2/5: Requirements gathering (adjusted up)

Evidence collected:
- 40% of new accounts stall before first transaction
- Average time-to-first-value: 24 days (target: 7)
- Support tickets cluster in week 1 (account setup confusion)
- Sales promises features that activate late in onboarding
- No owner measures onboarding success today

These point at several distinct problems, not one.
Next: Decompose before solutioning

Thought 3/5 [REVISION of Thought 1]: Scope refinement via requirement decomposition

Original assumption: One big onboarding revamp program.
Realization: "Onboarding" bundles four separable requirement groups.

Decomposition of the fuzzy initiative into requirements:
- R1 Setup requirements: account creation completable in one session,
  week-1 confusion points removed (drives the ticket cluster)
- R2 First-value requirements: first transaction achievable in 7 days,
  guided path to the "aha" action
- R3 Expectation requirements: sales-to-onboarding handoff checklist,
  promised features mapped to activation timing
- R4 Measurement requirements: named owner, time-to-first-value and
  stall-rate tracked weekly

This reduces problem scope significantly.
Each group has a different owner, cost, and urgency.
Next: Re-evaluate with refined scope

Thought 4/6: Re-evaluation (adjusted)

Prioritizing the requirement groups:
- R1 + R4 are cheap and unblock everything (fix confusion, start measuring)
- R2 needs design work but drives the stall metric directly
- R3 is a process change with sales—needs negotiation, slower

No need for a "big program"—phase the requirements instead.

Next: Verify phasing covers the original ask

Thought 5/6 [HYPOTHESIS]: Phased delivery

Hypothesis: Three phases satisfy "improve onboarding" without a revamp.

- Phase 1 (2 weeks): R1 setup fixes + R4 measurement baseline
- Phase 2 (6 weeks): R2 guided first-value path, target 7-day metric
- Phase 3 (ongoing): R3 sales handoff process, renegotiated quarterly

Benefits: Fast visible wins, measurable, each phase independently valuable.
Uncertainty: Does Phase 1 alone move the stall metric?

Thought 6/6 [FINAL]: Verified scope

Baseline evidence: Week-1 tickets account for half of stalled accounts—
Phase 1 plausibly moves the stall metric on its own.
Phase 2 attacks the remainder. Phase 3 prevents recurrence.

Initiative scope decision:
- Decomposed fuzzy ask into 4 requirement groups (R1-R4)
- Phased delivery: setup+measurement → first-value → handoff process
- Success metric: time-to-first-value 24→7 days, stall rate 40%→15%

Confidence: High
Assumptions: Support ticket data reflects real friction points
Benefits: Smaller commitments, earlier evidence, clear owners per phase
Trade-offs: Slower full-journey polish (but measurable progress each phase)
```

## Key Insights

1. **Scope revision crucial**: "One big revamp" reframed into four distinct requirement groups
2. **Requirement decomposition**: Fuzzy initiative → R1-R4 with separate owners, costs, urgency
3. **Hypothesis verification**: Confirmed Phase 1 could move the metric before committing
4. **Smaller is better**: Avoided over-committing to a monolithic program

## Impact of Revision

Without Thought 3 decomposition, the team might have launched a 6-month revamp program—significant over-commitment. Decomposing into phased requirements led to faster wins and clearer accountability.

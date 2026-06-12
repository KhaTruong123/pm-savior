---
name: requirement-risk-review
description: "Five PM personas stress-test a requirement or feature spec before it is built. Use when asked to 'review this requirement', 'what could go wrong with this feature', 'stress test this spec', or 'find the risks in this PRD section'."
license: MIT
attribution: "Adapted from ClaudeKit Engineer's ck-predict skill — https://github.com/claudekit/claudekit-engineer (MIT)"
argument-hint: "<requirement, spec, or feature description>"
metadata:
  author: kelvin
  version: "1.0.0"
---

# Requirement Risk Review

Five product personas independently analyze a requirement or feature spec, debate their conflicts, and produce a consensus verdict with actionable risk items — before a single ticket is written.

## Your mission

<task>
$ARGUMENTS
</task>

## When to Use

- Before adding a requirement to a PRD
- Before kicking off a sprint containing a new feature
- When a requirement feels vague, risky, or politically sensitive
- Stress-testing assumptions in a proposed design or policy change

## When NOT to Use

- Already-approved, fully-specified work with no open questions
- Minor copy changes or configuration tweaks

---

## The 5 PM Personas

| Persona | Focus | Core Questions |
|---------|-------|----------------|
| **End User** | Usability, clarity, value delivery | Does this solve their actual problem? Is it intuitive? What is the unhappy path? |
| **Support Agent** | Operational burden, edge cases, escalations | What will users ask about? What breaks and needs manual intervention? |
| **Compliance / Risk** | Legal, regulatory, data protection, audit trail | What regulations apply? What data is collected? What audit evidence is needed? |
| **Engineering Feasibility** | Scope clarity, technical unknowns, dependencies | Is this well-specified enough to build? What dependencies are unclear? How long is the tail risk? |
| **Business Owner** | Revenue impact, strategic fit, opportunity cost | Does this move a key metric? Is this the right priority right now? What is the cost of not doing it? |

---

## Debate Protocol

1. **Read** the requirement/spec from the argument
2. **Clarify** — if the requirement is ambiguous, ask 1–2 questions before proceeding
3. **Each persona analyzes independently** — do not let personas influence each other during this phase
4. **Identify agreements** — points where 4+ personas align
5. **Identify conflicts** — points where personas meaningfully disagree
6. **Weigh tradeoffs** — for each conflict, evaluate which concern has higher impact
7. **Produce verdict** — GO / CAUTION / STOP with risk rows ready to paste into a plan

---

## Output Format

```
## Risk Review: [Requirement Title]

## Verdict: GO | CAUTION | STOP

### Agreements (4+ personas align)
- [Point 1]
- [Point 2]

### Conflicts & Resolutions

| Topic | End User | Support Agent | Compliance/Risk | Eng Feasibility | Business Owner | Resolution |
|-------|----------|---------------|-----------------|-----------------|----------------|------------|
| [Issue] | [View] | [View] | [View] | [View] | [View] | [Recommendation] |

### Risk Summary

| Risk | Severity | Mitigation |
|------|----------|------------|
| [Risk description] | Critical/High/Medium/Low | [Concrete action] |

### Recommendations
1. [Action item — rationale]
2. [Action item — rationale]
3. [Action item — rationale]

### Next Steps
- Paste Critical/High risk rows into the plan as constraints (via `pm-plan`)
- Use `test-case-generator` to turn High risks into explicit test cases
```

---

## Verdict Levels

| Verdict | Meaning |
|---------|---------|
| **GO** | All personas aligned, no critical risks, proceed with confidence |
| **CAUTION** | Concerns exist but manageable — mitigations identified, proceed carefully |
| **STOP** | Critical unresolved issue — needs redesign or more information before proceeding |

### STOP Triggers (any one is sufficient)
- Compliance persona identifies a regulatory or data-protection violation with no viable mitigation
- Engineering Feasibility persona identifies an under-specified dependency that blocks estimation
- Business Owner persona identifies a strategic misalignment that invalidates the priority
- End User persona exposes a fundamental UX flaw that the requirement doesn't address

---

## Example Invocations

```
/requirement-risk-review "Users can opt out of marketing emails from their profile page"
/requirement-risk-review "Merchant KYC — accept national ID as proof of identity"
/requirement-risk-review requirements/cross-border-payment-flow.md
/requirement-risk-review "Auto-approve transactions below $100 for verified merchants"
```

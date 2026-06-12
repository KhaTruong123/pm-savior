---
name: pm-sequential-thinking
description: "Apply step-by-step reasoning for complex product decisions with revision capability. Use for multi-step analysis, requirement decomposition, hypothesis verification, adaptive planning, course correction. Triggers: 'think through step by step', 'analyse step by step', 'reason through', 'work through methodically'."
license: MIT
attribution: "Adapted from ClaudeKit Engineer's sequential-thinking skill — https://github.com/claudekit/claudekit-engineer (MIT)"
metadata:
  author: kelvin
  version: "1.0.0"
---

# Sequential Thinking

Structured problem-solving via manageable, reflective thought sequences with dynamic adjustment.

## When to Apply

- Complex problem decomposition (breaking a fuzzy initiative into concrete requirements)
- Adaptive planning with revision capability
- Analysis needing course correction
- Problems with unclear/emerging scope
- Multi-step decisions requiring context maintenance
- Hypothesis-driven investigation (e.g., diagnosing why a client is churning)

Example invocations:
- "Think through step by step: should we delay the launch?"
- "Reason through whether we build or buy the reporting tool"
- "Work through methodically why our biggest client is disengaging"

## Core Process

### 1. Start with Loose Estimate
```
Thought 1/5: [Initial analysis]
```
Adjust dynamically as understanding evolves.

### 2. Structure Each Thought
- Build on previous context explicitly
- Address one aspect per thought
- State assumptions, uncertainties, realizations
- Signal what next thought should address

### 3. Apply Dynamic Adjustment
- **Expand**: More complexity discovered → increase total
- **Contract**: Simpler than expected → decrease total
- **Revise**: New insight invalidates previous → mark revision
- **Branch**: Multiple approaches → explore alternatives

### 4. Use Revision When Needed
```
Thought 5/8 [REVISION of Thought 2]: [Corrected understanding]
- Original: [What was stated]
- Why revised: [New insight]
- Impact: [What changes]
```

### 5. Branch for Alternatives
```
Thought 4/7 [BRANCH A from Thought 2]: [Approach A]
Thought 4/7 [BRANCH B from Thought 2]: [Approach B]
```
Compare explicitly, converge with decision rationale.

### 6. Generate & Verify Hypotheses
```
Thought 6/9 [HYPOTHESIS]: [Proposed explanation or decision]
Thought 7/9 [VERIFICATION]: [Evidence check results]
```
Iterate until hypothesis verified.

### 7. Complete Only When Ready
Mark final: `Thought N/N [FINAL]`

Complete when:
- Decision or solution verified
- All critical aspects addressed
- Confidence achieved
- No outstanding uncertainties

## Application Modes

**Explicit**: Use visible thought markers when complexity warrants visible reasoning or user requests breakdown.

**Implicit**: Apply methodology internally for routine problem-solving where thinking aids accuracy without cluttering response.

## Scripts (Optional)

Optional scripts for deterministic validation/tracking:
- `scripts/process-thought.js` - Validate & track thoughts with history
- `scripts/format-thought.js` - Format for display (box/markdown/simple)

Use when validation/persistence needed; otherwise apply methodology directly.

## References

Load when deeper understanding needed:
- `references/core-patterns.md` - Revision & branching patterns
- `references/examples-product-decision.md` - Build-vs-buy product decision example
- `references/examples-stakeholder-analysis.md` - Client churn diagnosis example
- `references/examples-initiative-scoping.md` - Initiative scoping & requirement decomposition example
- `references/advanced-techniques.md` - Spiral refinement, hypothesis testing, convergence
- `references/advanced-strategies.md` - Uncertainty, revision cascades, meta-thinking

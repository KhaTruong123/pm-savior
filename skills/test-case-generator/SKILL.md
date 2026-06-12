---
name: test-case-generator
description: "Generate structured test cases and edge case lists from a requirement, user story, or acceptance criteria. Use when asked to 'write test cases', 'create QA scenarios', 'edge cases for this requirement', 'acceptance tests', or 'QA checklist'."
license: MIT
attribution: "Adapted from ClaudeKit Engineer's ck-scenario skill — https://github.com/claudekit/claudekit-engineer (MIT)"
argument-hint: "<requirement text, user story, or file path>"
metadata:
  author: kelvin
  version: "1.0.0"
---

# Test Case Generator

Decompose a requirement or user story across 12 dimensions to produce a structured test case table and edge case list — ready to paste into a tracker ticket, PRD risk section, or QA document.

## Your mission

<task>
$ARGUMENTS
</task>

## When to Use

- Before a sprint starts — turn acceptance criteria into testable cases
- During PRD review — surface gaps in requirements
- Before handoff to QA — give them a head start
- Risk assessment — find edge cases before they become bugs

## When NOT to Use

- Pure visual/cosmetic changes with no logic
- Already-tested, stable requirements with no recent changes

---

## 12 Decomposition Dimensions

Not all 12 apply to every requirement. Identify relevant dimensions first, then generate cases only for those.

| # | Dimension | What to Look For |
|---|-----------|------------------|
| 1 | **User Types** | new user, returning user, blocked/suspended user, admin, guest |
| 2 | **Input Extremes** | empty field, max length, special characters, invalid format |
| 3 | **Timing** | slow connection, session timeout, simultaneous submissions, retry |
| 4 | **Scale** | zero items, one item, large list, pagination boundary |
| 5 | **State Transitions** | first use, mid-flow abandon, resume after interruption, partial completion |
| 6 | **Environment** | mobile, low-bandwidth, different locale/timezone, accessibility (screen reader) |
| 7 | **Error Paths** | service unavailable, payment failure, network drop, file upload error |
| 8 | **Authorization** | expired session, wrong role, shared link access, unauthenticated attempt |
| 9 | **Data Integrity** | duplicate submission, missing required fields, encoding edge cases |
| 10 | **Integration** | third-party API down, webhook replay, version mismatch |
| 11 | **Compliance** | GDPR data deletion, consent withdrawal, audit trail gaps, PII exposure |
| 12 | **Business Logic** | free tier limit reached, promo code stacking, refund after partial delivery, zero/negative amounts |

---

## Workflow

1. **Parse** the requirement/user story/acceptance criteria from the argument or ask user to paste it
2. **Clarify** — if requirement is vague, ask 1–2 targeted questions before proceeding (e.g. "What are the roles involved?", "What does success look like?")
3. **Filter dimensions** — mark which of the 12 apply; skip irrelevant ones with a brief reason
4. **Generate test cases** — 3–5 per relevant dimension
5. **Assign priority** — Critical / High / Medium / Low
6. **Output** as test case table + edge case list

### Priority Criteria

| Level | Meaning |
|-------|---------|
| **Critical** | Feature completely broken, data loss, security/compliance issue |
| **High** | Core flow broken for subset of users, data inconsistency |
| **Medium** | Degraded experience, recoverable error not surfaced |
| **Low** | Minor UX issue, non-blocking warning |

---

## Output Format

```
## Test Cases: [Requirement Title]

**Requirement summary:** [1–2 sentence summary of what was analyzed]
**Dimensions analyzed:** [list]
**Dimensions skipped:** [list + reason]

### Test Case Table

| ID | Dimension | Precondition | Steps | Expected Result | Priority |
|----|-----------|--------------|-------|-----------------|----------|
| TC-01 | Input Extremes | User is on registration form | 1. Leave name field blank 2. Click Submit | Error message: "Name is required" | High |
| TC-02 | Authorization | User session has expired | 1. Attempt to access profile page | Redirected to login screen | Critical |
| TC-03 | Business Logic | Free tier user has used all 5 slots | 1. Try to add 6th item | Upgrade prompt shown, item not added | High |

### Edge Case List (Critical + High only)
- [Edge case description] — [why it matters]
- [Edge case description] — [why it matters]

### Summary
- Critical: N
- High: N
- Medium: N
- Low: N
- Total: N test cases across X dimensions

### Next Steps
- Paste Critical/High rows into the PRD risk section or tracker ticket
- Use `requirement-risk-review` to stress-test the requirement with PM personas before finalizing
```

---

## Example Invocations

```
/test-case-generator "User can request a refund within 30 days of purchase"
/test-case-generator "Merchant onboarding — KYC document upload step"
/test-case-generator requirements/offramp-kyc-flow.md
/test-case-generator "Payment checkout — user selects currency and confirms amount"
```

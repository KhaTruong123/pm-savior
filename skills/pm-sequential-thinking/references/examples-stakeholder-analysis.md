# Example: Stakeholder Analysis with Sequential Thinking

**Problem**: Key client account is disengaging (usage down 60%, renewal in 8 weeks).

## Sequential Thinking Approach

```
Thought 1/5: Initial investigation

Account: Northstar Logistics (top-5 by revenue)
Expected: Steady weekly usage, active champion
Actual: Usage down 60% over 6 weeks, champion silent

Need to identify the churn driver.
Next: Analyze the account relationship

Thought 2/5: Account analysis

Touchpoints with this client:
- Weekly product usage (transactions)
- Monthly business review meetings
- Support tickets
- Champion contact (head of operations)

Last two business reviews were cancelled by client. Could be losing the champion.
Next: Examine actual signals

Thought 3/6: Signal review (adjusted up—more complex)

Data pulled:
- Usage drop started exactly 6 weeks ago (sharp, not gradual)
- 4 support tickets in that week (!!) — all about failed transactions
- Champion last replied 5 weeks ago
- Competitor announced a promo 2 months ago

Sharp drop + ticket cluster suggests an event, not slow drift.
Need to test competing explanations.
Next: Form hypotheses

Thought 4/6 [BRANCH A]: Hypothesis - Competitor poaching

Competitor promo undercuts our pricing by ~20%.
Client may be migrating volume to the competitor.
Verification: Check if usage drop matches a gradual migration pattern and whether client mentioned pricing.

Thought 4/6 [BRANCH B]: Hypothesis - Service failure broke trust

The 4 failed-transaction tickets coincide with drop start.
A bad incident may have pushed client to route volume elsewhere as a precaution.
Verification: Check ticket severity, resolution time, and client's words in ticket threads.

Thought 5/6 [VERIFICATION]: Testing hypotheses

Migration pattern test: Drop was overnight, not gradual—inconsistent with price-driven migration.
Ticket review: All 4 tickets = failed transactions during one outage window; resolution took 9 days; final client message: "We can't keep explaining this to our customers."

Branch B confirmed: Reliability incident broke trust; client rerouted volume.
Branch A weakened: No pricing mention anywhere; drop pattern wrong for poaching.

Root cause identified.
Next: Define recovery plan

Thought 6/6 [FINAL]: Recovery plan and verification

Actions:
1. Executive apology call within 48h (not account manager—needs senior signal)
2. Share incident post-mortem + concrete reliability commitments
3. Offer service credits tied to uptime guarantees
4. Re-establish weekly check-ins with champion until renewal

Tested assumption: Champion went silent AFTER the unresolved tickets—relationship is recoverable if trust is repaired, not lost to a competitor.

Confidence: High (verified against usage pattern + ticket evidence)
Result: Renewal conversation reframed around reliability commitments, not price
```

## Key Techniques Demonstrated

1. **Branching for hypothesis testing**: Explored competitor-poaching vs service-failure in parallel
2. **Verification before action**: Tested both hypotheses against evidence systematically
3. **Data-driven decisions**: Used usage patterns and ticket history to guide investigation
4. **Dynamic adjustment**: Expanded thought count when complexity emerged
5. **Elimination method**: Ruled out poaching, confirmed trust breakdown

## Comparison

**Without sequential thinking**: Might jump to "competitor stole them" (common assumption), respond with a discount, and miss the real trust issue.

**With sequential thinking**: Systematically tested hypotheses, identified actual churn driver, responded with the right intervention.

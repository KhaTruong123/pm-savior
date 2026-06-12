# Example: Product Decision with Sequential Thinking

**Problem**: Decide build-vs-buy for a customer analytics dashboard requested by top accounts.

## Without Sequential Thinking
"Buy a vendor tool. It's faster than building. Pick the market leader and integrate it."
(Misses cost structure, data ownership, vendor lock-in, roadmap fit)

## With Sequential Thinking

```
Thought 1/5: Requirements

Customer analytics dashboard needs:
- Account-level usage reporting (top accounts demand it)
- Data stays under our control (enterprise contracts)
- Live within one quarter (renewal deadlines)

Uncertainty: Build in-house vs buy vendor tool vs embed white-label?
Next: Evaluate approaches

Thought 2/6: Approach evaluation (adjusted)

Comparing build vs buy:
- Build: Full control, roadmap fit, slow (2+ quarters), team distraction
- Buy: Fast (weeks), recurring cost, limited customization

White-label embed is a middle path worth including.
Buy looks better for the deadline.
Next: Cost and contract structure

Thought 3/6: Vendor cost design

Vendor option includes: per-seat pricing, usage tiers, annual contract, data export add-on

Uncertainty: Who owns the underlying data? What happens at contract exit?
Next: Switching-cost analysis

Thought 4/6 [REVISION of Thought 3]: Lock-in risk fix

Original: Per-seat vendor contract with data export add-on.
Issue: Export add-on only covers summary data—raw event data stays with vendor.

Corrected:
- Require raw data export clause in contract (needed for exit)
- Add quarterly export to our own storage
- Log a contract review before each renewal

Impact: Need procurement involved before signing

Thought 5/7: Phasing strategy (adjusted)

Phase 1: Buy white-label embed (live in 6 weeks)
Phase 2: Quarterly raw-data exports running, contract exit terms locked

Ownership:
- Vendor: dashboards and visual layer
- Us: raw data copy + customer relationship

Enables speed now + exit option later.

Thought 6/7: Decision flow

1. Shortlist 2 vendors with raw-export clauses
2. Pilot with one top account
3. Verify export works end-to-end (test the exit path)
4. Roll out to remaining accounts

Addresses Thought 4 lock-in concern.

Thought 7/7 [FINAL]: Complete decision

- Buy white-label embed, not build
- Raw data export clause mandatory
- 6-week pilot with one top account, then rollout
- Quarterly exports to our storage + renewal review
- Revisit build option only if vendor blocks roadmap needs

Confidence: High
Assumptions: Vendor accepts export clause, deadline holds
Trade-offs: Recurring cost vs one-quarter delivery
```

## Key Outcomes

1. **Revision caught lock-in issue**: Export add-on excluded raw data
2. **Dynamic adjustment**: 5→7 thoughts as complexity emerged
3. **Comprehensive**: Speed, cost, data ownership, exit strategy, phasing

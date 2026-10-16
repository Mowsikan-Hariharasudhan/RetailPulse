# 08 — Metric Definitions

**Status:** Draft. Approve each definition after profiling and reconciliation.

| Metric | Draft definition | Grain | Required filters/caveats | Status |
|---|---|---|---|---|
| Orders | Count distinct `order_id` | Order | Status policy to be explicit | Draft |
| Item merchandise value | Sum item `price` | Order-item | Not interchangeable with payment amount | Draft |
| Freight value | Sum `freight_value` | Order-item | Confirm source meaning | Draft |
| Payment value | Sum `payment_value` | Payment row | Multiple payments can exist per order | Draft |
| Delivered order count | Count distinct eligible delivered orders | Order | Use declared order-status policy | Draft |
| Late delivery rate | Late delivered orders / delivered orders with both dates | Order | Actual customer delivery later than estimated date; missing dates excluded from denominator and counted separately | Draft |
| Average review score | Average review score at chosen review grain | Review/order | Validate multiple rows or review relationships | Draft |
| Repeat customer rate | Unique customers with >1 distinct order / eligible unique customers | Customer identity | Use `customer_unique_id`; define eligible statuses | Draft |
| Category item value | Sum item price grouped by translated category | Order-item | Do not multiply item rows by payment/review rows | Draft |

For every metric, final documentation must state its SQL file, source model, grain, status/date inclusion rules, missing-data handling, and at least one validation check.

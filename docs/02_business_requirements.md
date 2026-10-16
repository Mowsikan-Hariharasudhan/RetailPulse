# 02 — Business Requirements

**Status:** Initial requirements baseline; metrics will be refined after source profiling.

## Business questions

| ID | Business question | Initial analytical output | Important caution |
|---|---|---|---|
| BR-01 | How many orders are placed over time? | Orders by day/month | Define which statuses count as orders; don't silently exclude cancelled orders. |
| BR-02 | What is the order/item sales value over time? | Value by day/month | Keep item price, freight, payments, and total paid distinct until reconciled. |
| BR-03 | Which product categories have the highest item value? | Category ranking | Category translation may require a mapping table; handle missing category labels. |
| BR-04 | Which sellers handle the most items and item value? | Seller-level volume/value | One order can include multiple items and sellers. |
| BR-05 | What payment types are used and what is paid? | Payment totals and mix | One order may have multiple payment rows; use the right grain. |
| BR-06 | What share of delivered orders arrived after the estimated date? | Late-delivery rate | Define eligible orders and exclude missing dates transparently. |
| BR-07 | How do review scores vary with delivery performance? | Review score by delivery group | Reviews and orders may need deduplication or aggregation before joining. |
| BR-08 | How many customers purchase more than once? | Repeat-customer rate | Use `customer_unique_id`, not order-level `customer_id`, for repeat identity. |
| BR-09 | How does order status vary? | Status counts and trends | Preserve source status labels and document any grouped status categories. |
| BR-10 | Are source and transformed totals consistent? | Reconciliation checks | Some values cannot be compared directly because tables have different grains. |

## Functional requirements

- FR-01: Load selected source CSVs into a dedicated BigQuery dataset.
- FR-02: Record schema, row counts, and table grain for each source.
- FR-03: Create staging models with explicit data types and documented cleaning rules.
- FR-04: Create analytical models with documented primary/business keys and join relationships.
- FR-05: Implement a reusable query for each approved metric.
- FR-06: Implement quality checks for uniqueness, nulls, referential integrity, status/date validity, and amount reconciliation where appropriate.
- FR-07: Expose validated results in a dashboard or static report.
- FR-08: Document how to reproduce the project and interpret each KPI.

## Non-functional requirements

- NFR-01: Reproducibility: SQL and configuration instructions are version-controlled.
- NFR-02: Cost awareness: avoid unnecessary full scans and track query bytes processed where available.
- NFR-03: Correctness: define metric grain and join cardinality before calculating totals.
- NFR-04: Transparency: report data date range and data-quality limitations.
- NFR-05: Security: do not commit credentials or secrets.
- NFR-06: Portability: keep source CSVs out of Git by default and document how to obtain them.
- NFR-07: Maintainability: separate profiling, staging, data marts, analysis, and tests.

## Draft metric definitions — to be validated

- **Order count:** count of distinct `order_id` under a documented order-status inclusion policy.
- **Item merchandise value:** sum of `price` from order-item rows. This is not necessarily equal to total payment value.
- **Freight value:** sum of `freight_value` from order-item rows.
- **Payment value:** sum of `payment_value` from payment rows, aggregated at the correct grain.
- **Late delivered order:** an eligible order with both actual delivery date and estimated delivery date present, where actual customer delivery timestamp is later than estimated delivery timestamp.
- **Repeat customer:** a `customer_unique_id` associated with more than one distinct order.
- **Average review score:** average of the chosen review-score grain after ensuring each order/review is counted according to a declared rule.

These are working definitions, not final metrics. We will confirm names, null handling, status rules, and aggregation level after inspecting actual source data.

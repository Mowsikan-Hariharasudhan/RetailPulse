# 06 — Data Quality and Cleaning Plan

**Status:** Planned checks; no results have been measured yet.

## Principles

1. Profile before cleaning.
2. Preserve the raw layer and do not silently delete suspicious records.
3. Make every cleaning rule explicit and reproducible.
4. Track row counts before and after each transformation.
5. Distinguish source defects from legitimate lifecycle states (for example, undelivered orders may not have actual delivery timestamps).

## Planned checks

- Schema and type checks.
- Row counts and duplicate-key checks at each table's declared grain.
- Null counts for IDs, status fields, amounts, and important timestamps.
- Allowed-value profiles for order statuses, payment types, and review scores.
- Referential integrity: order items to orders/products/sellers; orders to customers; payments/reviews to orders.
- Date logic: approval, shipment, delivery, and estimated-delivery timestamp relationships where applicable.
- Amount reconciliation across item value, freight, and payment values, with clear explanations for legitimate differences.
- Join fanout checks after each relationship is modelled.

## Results template

| Check ID | Table/model | Check | Expected rule | Actual result | Status | Resolution/evidence |
|---|---|---|---|---|---|---|
| DQ-001 | TBD | Uniqueness | TBD | Not run | Pending | TBD |

No check should be marked passed until its SQL has been executed and the output recorded.

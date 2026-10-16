# 07 — Data Model

**Status:** Initial hypothesis; finalize only after source profiling.

## Modelling rules

- State the grain of every table in one sentence.
- Declare primary/business keys and test uniqueness rather than assuming it.
- Preserve different grains for orders, order items, payments, and reviews.
- Aggregate each fact to the target grain before joining facts to avoid fanout and double counting.
- Use clear names for source, staging, and analytics models.

## Candidate fact tables

| Model | Expected grain | Candidate measure(s) | Candidate keys |
|---|---|---|---|
| `fct_orders` | One row per order | Order count; lifecycle intervals | `order_id` |
| `fct_order_items` | One row per order-item | Item price; freight | Composite/source item key to be verified; `order_id`, product and seller identifiers |
| `fct_payments` | One row per payment record | Payment value; installments | Order ID plus payment sequence/other source key to verify |
| `fct_order_reviews` | Source review grain to be verified | Review score | Review ID and/or order relationship to verify |

## Candidate dimensions

| Model | Expected grain | Candidate key |
|---|---|---|
| `dim_customers` | One source customer record | `customer_id`; use `customer_unique_id` for repeat-customer identity |
| `dim_products` | One product | `product_id` |
| `dim_sellers` | One seller | `seller_id` |
| `dim_product_categories` | One translated category mapping | Source category key to verify |
| Date dimension | One calendar date, only if useful | Calendar date |

## Model validation still required

- Confirm source primary keys and duplicate behavior.
- Confirm item and payment table row grains.
- Measure one-to-many relationships and null foreign keys.
- Choose whether a star schema is justified for the first dashboard.
- Record diagram/screenshots after the actual models have been created.

# 04 — Dataset Inventory

**Status:** Awaiting download and inspection. Do not treat expected files or row counts as verified until recorded from the downloaded source and/or BigQuery.

## Source information

- Dataset: Brazilian E-Commerce Public Dataset by Olist
- Source URL: https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce
- Format: CSV
- Stated coverage: historical orders from approximately 2016–2018
- License shown on source page: CC BY-NC-SA 4.0 (verify current terms)

## Inventory register

Fill in `Actual file name`, `Local file size`, `Local row count`, `BigQuery table`, `Loaded row count`, and `Load notes` after downloading and loading.

| Source file | Expected purpose | Local file size | Local row count | BigQuery table | Loaded row count | Load notes |
|---|---|---:|---:|---|---:|---|
| `olist_orders_dataset.csv` | Order status and lifecycle timestamps | TBD | TBD | TBD | TBD | Not yet loaded |
| `olist_order_items_dataset.csv` | Items, products, sellers, item prices, freight | TBD | TBD | TBD | TBD | Not yet loaded |
| `olist_customers_dataset.csv` | Order-level customer record and customer identity | TBD | TBD | TBD | TBD | Not yet loaded |
| `olist_products_dataset.csv` | Product attributes | TBD | TBD | TBD | TBD | Not yet loaded |
| `olist_sellers_dataset.csv` | Seller identifiers and location | TBD | TBD | TBD | TBD | Not yet loaded |
| `olist_order_payments_dataset.csv` | Payment method and payment value | TBD | TBD | TBD | TBD | Not yet loaded |
| `olist_order_reviews_dataset.csv` | Review scores/text and timestamps | TBD | TBD | TBD | TBD | Not yet loaded |
| `product_category_name_translation.csv` | Source category to English label mapping | TBD | TBD | TBD | TBD | Not yet loaded |
| `olist_geolocation_dataset.csv` | ZIP-prefix geolocation data | TBD | TBD | TBD | TBD | Optional for initial scope; can be relatively wide/large after cleaning |

## Loading evidence checklist

- [ ] Record source download date and source page version if displayed.
- [ ] Record file sizes and CSV encoding/delimiter assumptions.
- [ ] Decide whether header rows are present and document load options.
- [ ] Load one small/important file first and validate the schema before bulk loading.
- [ ] Record BigQuery dataset location and expiration settings.
- [ ] Compare source record counts with loaded table counts.
- [ ] Record rejected rows, malformed records, or parsing warnings.
- [ ] Keep source CSVs outside Git by default.

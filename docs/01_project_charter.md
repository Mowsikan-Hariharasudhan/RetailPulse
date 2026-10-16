# 01 — Project Charter

**Project:** RetailPulse — E-commerce Sales & Operations Intelligence  
**Status:** Draft baseline, Phase 1  
**Owner:** Project learner  
**Warehouse:** Google BigQuery  
**Data source:** Brazilian E-Commerce Public Dataset by Olist

## 1. Executive summary

RetailPulse is a portfolio project that demonstrates an end-to-end analytics workflow: obtain historical ecommerce data, load it into BigQuery, profile and clean the source tables, model facts and dimensions, define trustworthy business metrics, test the outputs, and present the results in a dashboard.

The project is intentionally built in stages. BigQuery and SQL are the core learning objectives. Airbyte and Cube.dev are optional extensions, evaluated only after a working and validated warehouse layer exists.

## 2. Problem statement

An e-commerce operations team has data spread across orders, order items, customers, products, sellers, payments, reviews, and delivery dates. Without a consistent analytical model, different reports may count orders differently, double-count amounts after joins, or calculate delivery performance inconsistently. The team needs a reproducible, documented source of truth for operational and commercial KPIs.

## 3. Goal

Create a reproducible batch analytics solution in BigQuery that transforms related raw CSV tables into tested, documented datasets and clear business insights.

## 4. Intended users

- Sales manager: order trends and sales performance.
- Operations manager: fulfilment and delivery performance.
- Merchandising/category manager: product and category analysis.
- Customer experience team: review score and delivery experience analysis.
- Data/analytics engineer: reproducible SQL, data quality, data model, cost and performance notes.

These users are personas for the project, not verified users of an existing business system.

## 5. Scope

### In scope

- Historical batch data from the Olist public dataset.
- BigQuery project/dataset setup within sandbox constraints.
- Source inventory, schema profiling, quality checks, and transformation rules.
- Staging and analytics-ready fact/dimension models.
- Business metrics for order volume/value, products/categories, repeat customers, payment methods, review scores, and estimated-versus-actual delivery.
- Query validation, documentation, basic performance/cost awareness.
- A dashboard after the SQL layer is stable.
- Optional proof-of-concept integrations with Airbyte and/or Cube.dev, if feasible without surprise costs.

### Out of scope for the first version

- Real-time streaming or claims of live business data.
- Predictive machine learning and recommendations.
- Production SLAs, enterprise identity governance, and high-availability operations.
- Any paid cloud commitment without explicit approval.
- Republishing the dataset itself in this repository.

## 6. Data and date caveat

The dataset is historical (orders from approximately 2016–2018), anonymized commercial data. It is suitable for practising business analytics but does not represent current market conditions or a live operational feed. Analyses must display the date range and avoid describing historical metrics as current performance.

## 7. Success criteria

The project is considered complete when:

1. Each source file used is documented with row count, schema, grain, and load result.
2. Raw tables can be recreated from the source files using documented steps.
3. Staging rules are explicit and testable.
4. Fact/dimension grains, keys, and join paths are documented.
5. Metric definitions state numerator/denominator and inclusion/exclusion rules.
6. Quality checks run and results (including failures and resolutions) are recorded.
7. At least 8 business questions are answered using reusable SQL.
8. Aggregate results are reconciled to source-level checks where possible.
9. The dashboard reflects validated SQL outputs and notes the data period.
10. A new reader can follow the README and rebuild the project without private credentials.
11. The final repository includes screenshots, a demo, attribution, limitations, and lessons learned.

## 8. Constraints and assumptions

- Initial environment is BigQuery Sandbox, with no billing enablement assumed.
- Sandbox restrictions, expiration, quota, and storage limits must be checked against official documentation.
- Initial ingestion is batch-based. Automation is a later decision.
- Exact source row counts will be measured after download and recorded in the dataset inventory; no local load result is assumed at charter stage.
- Source files remain outside Git by default because they are downloadable from the original source and have separate licensing/attribution considerations.

## 9. Risks and mitigations

| Risk | Mitigation |
|---|---|
| Sandbox storage/expiration limits | Keep SQL and docs in Git; preserve source files locally; document rebuild steps. |
| Accidental double counting after joins | Document table grain; aggregate at correct grain; reconcile totals and test uniqueness. |
| Ambiguous revenue definition | Define business metrics before dashboard work; distinguish item price, freight, payments, and order value. |
| Missing timestamps or incomplete orders | Profile nulls and status distribution; define inclusion rules explicitly. |
| Optional tool costs or account requirements | Evaluate tools separately; keep BigQuery-only fallback. |
| Historical data mistaken for current data | Display source date range in README and dashboard. |

## 10. Initial deliverables

- This charter.
- Business requirements and metric questions.
- Architecture diagram and decision log.
- Repository scaffold and documentation placeholders.

## 11. Source

Olist. *Brazilian E-Commerce Public Dataset by Olist*. Kaggle: https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce  
The dataset page identifies the license as CC BY-NC-SA 4.0. Confirm the current source page/license before reuse or redistribution.

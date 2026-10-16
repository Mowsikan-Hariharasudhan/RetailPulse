# RetailPulse — E-commerce Sales & Operations Intelligence

RetailPulse is a learning-focused analytics engineering project built around Google BigQuery. It turns the Brazilian E-Commerce Public Dataset by Olist into validated and reusable business analytics for sales, products, customers, payments, reviews, and delivery performance.

> **Project status:** Phase 1 — Project charter and repository setup.
>
> **Important:** This repository is a starter scaffold. No data has been loaded, queries have not yet been run against the Olist dataset, and no dashboard or integrations should be considered implemented until we record evidence in this repository.

## Business objective

Build a reproducible batch analytics pipeline and dashboard that helps a fictional e-commerce operations team answer questions such as:

- How do order volume and merchandise value change over time?
- Which product categories and sellers perform best?
- What share of orders arrive later than the estimated delivery date?
- How do review scores vary with delivery experience?
- How many customers make repeat purchases?

## Planned technology

- **Required:** Google BigQuery and GoogleSQL.
- **Planned dashboard:** React and Chart.js, after the analytics layer is validated.
- **Optional, subject to feasibility and free-tier constraints:** Airbyte for ingestion and Cube.dev for a semantic/API layer.
- **Initial ingestion method:** Batch upload of CSV files. We will evaluate automation after the core model works.

## Data source

Brazilian E-Commerce Public Dataset by Olist on Kaggle: https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce

The source provides anonymized historical e-commerce data, commonly described as around 100,000 orders from 2016–2018. It includes related CSV files for orders, items, customers, products, sellers, payments, reviews, geolocation, and category-name translation.

**License note:** The Kaggle dataset page identifies the dataset as CC BY-NC-SA 4.0. Review the dataset's current license and attribution requirements before redistributing data or using this work commercially. This repository should normally contain code and documentation, not a copy of the source CSV files.

## Repository map

```text
RetailPulse/
├── README.md
├── LICENSE_AND_ATTRIBUTION.md
├── .gitignore
├── docs/
│   ├── 01_project_charter.md
│   ├── 02_business_requirements.md
│   ├── 03_architecture.md
│   ├── 04_dataset_inventory.md
│   ├── 05_data_dictionary.md
│   ├── 06_data_quality_and_cleaning.md
│   ├── 07_data_model.md
│   ├── 08_metric_definitions.md
│   ├── 09_validation_results.md
│   ├── 10_optimisation_and_costs.md
│   ├── 11_setup_and_runbook.md
│   ├── decision_log.md
│   └── learning_log.md
├── sql/
│   ├── 01_data_profiling/
│   ├── 02_staging/
│   ├── 03_data_marts/
│   ├── 04_business_analysis/
│   └── 05_data_quality_tests/
├── dashboard/
├── screenshots/
└── data/  # Keep source CSV files out of Git unless there is a clear, licensed reason.
```

## Working method

Every implementation step should include:

1. The question or requirement being addressed.
2. A short explanation of the design choice.
3. The SQL/code/configuration used.
4. Evidence: output, screenshot, row counts, or test results.
5. Known limitations and the next step.

## Cost and safety guardrails

- Start with BigQuery Sandbox and do not enable billing as a workaround without an explicit discussion.
- Sandbox has a 10 GiB lifetime storage limit and 1 TiB monthly query-processing free limit; its documented restrictions include no streaming, DML statements, or BigQuery Data Transfer Service, and resources can expire after 60 days. Verify current limits in the official docs before relying on them: https://cloud.google.com/bigquery/docs/sandbox
- Prefer read-only `SELECT` queries for exploration. For supported transformations in the sandbox, use carefully reviewed `CREATE OR REPLACE TABLE ... AS SELECT` patterns when appropriate.
- Estimate/query-check before repeatedly scanning full datasets. Avoid selecting unnecessary columns.
- Never commit credentials, service-account JSON keys, API keys, or personal data.
- Optional integrations are not a requirement if their free tier, setup, or sandbox compatibility is unsuitable.

## Current status

- [x] Project idea selected
- [x] Starter repository and initial documentation scaffold
- [ ] Dataset downloaded and source files inventoried
- [ ] BigQuery dataset/location confirmed
- [ ] Raw tables loaded and row counts recorded
- [ ] Staging models and quality checks implemented
- [ ] Analytical data marts implemented
- [ ] Business metrics validated
- [ ] Dashboard built
- [ ] Optional integrations evaluated
- [ ] Final demo and project retrospective documented

## Dataset citation

Olist. *Brazilian E-Commerce Public Dataset by Olist*. Kaggle. https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce

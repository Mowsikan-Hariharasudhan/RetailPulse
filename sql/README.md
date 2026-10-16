# SQL organization

Use numbered folders to keep the workflow reproducible:

1. `01_data_profiling/` — inspect schemas, row counts, missing values, duplicates, and category values.
2. `02_staging/` — data type conversion, standardisation, and explicit cleaning rules.
3. `03_data_marts/` — facts, dimensions, and reusable analytics models.
4. `04_business_analysis/` — queries answering documented business questions.
5. `05_data_quality_tests/` — independent quality and reconciliation checks.

Name each file for the task (for example, `profile_orders.sql`). Add a short header comment with purpose, input tables, expected grain, and validation. Prefer read-only profiling queries first. Don't put real project credentials or secrets in SQL files.

# 11 — Setup and Runbook

**Status:** Initial scaffold; exact load commands and queries will be added after the environment is inspected.

## Prerequisites

- Google account with access to BigQuery Sandbox.
- Access to the Olist dataset source page and ability to download its files.
- Git and a GitHub account (optional for local development, recommended for portfolio publishing).
- A local editor such as VS Code.

## Initial setup checklist

- [ ] Download the dataset from https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce
- [ ] Review dataset license and attribution terms.
- [ ] Keep CSV files outside this repository by default.
- [ ] Confirm the Google Cloud project and BigQuery dataset location.
- [ ] Record dataset expiration and applicable Sandbox restrictions.
- [ ] Upload one selected CSV and validate its schema and row count.
- [ ] Document any location mismatches before loading other files.
- [ ] Run profiling SQL stored in `sql/01_data_profiling/`.

## Recovery/rebuild principles

- Source files can be re-downloaded from the source page.
- SQL and documentation are source-controlled.
- BigQuery Sandbox resources may expire; the repository should be sufficient to recreate them.
- Any project-specific IDs, dataset IDs, region, and date of last load should be recorded here, but never secrets.

## Environment record

| Setting | Value |
|---|---|
| Google Cloud project ID | To be recorded by user; do not commit if organization policy forbids it |
| BigQuery dataset location | To verify |
| BigQuery dataset name | Proposed: `retailpulse` (confirm before creation) |
| Sandbox or billing-enabled | Sandbox assumed |
| Initial source data download date | Pending |
| Last successful load date | Pending |
| Tables expiration date/configuration | Pending |

## Troubleshooting log

| Date | Symptom/error | Root cause | Resolution | Evidence |
|---|---|---|---|---|
| — | Not started | — | — | — |

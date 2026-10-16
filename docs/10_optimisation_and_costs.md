# 10 — Optimisation and Cost Notes

**Status:** Planning baseline; capture measurements after representative queries exist.

## Working rules

- Select only required columns; avoid `SELECT *` in stable production-style queries.
- Check bytes processed or estimated cost before expensive repeated scans when the UI offers this information.
- Filter early where semantics permit.
- Avoid repeatedly scanning geolocation data unless a use case needs it.
- Be deliberate about joins, since incorrect grain can cause both incorrect numbers and excess processing.
- Consider partitioning on a suitable date column and clustering on frequently filtered/joined columns only when table size, access pattern, and environment justify it.
- Measure before claiming an optimisation improved performance.

## Measurement log

| Query/model | Baseline bytes processed | Baseline duration | Change | New bytes processed | New duration | Conclusion |
|---|---:|---:|---|---:|---:|---|
| Not measured | — | — | — | — | — | Pending |

## Sandbox guardrails

Use the official documentation for current restrictions and quotas: https://cloud.google.com/bigquery/docs/sandbox

This project does not require enabling billing. If a planned capability is unsupported in Sandbox, record the limitation and choose an acceptable fallback rather than bypassing it.

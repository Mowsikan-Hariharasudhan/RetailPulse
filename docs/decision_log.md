# Decision Log

Record decisions when they are made, including alternatives considered and trade-offs.

| ID | Date | Decision | Reason | Alternatives considered | Consequence/status |
|---|---|---|---|---|---|
| ADR-001 | 2026-10-15 | Use Olist's public Brazilian e-commerce dataset as the initial source | Multi-table historical data supports realistic joins, customer/order grain, payments, reviews, and delivery analytics | Synthetic data; other public datasets | Provisional; verify source download, license, and data usability |
| ADR-002 | 2026-10-15 | Build the first version around BigQuery Sandbox without enabling billing | Keeps project accessible while learning; aligns with stated cost constraint | Billing-enabled project; local warehouse | Sandbox limitations must be handled; optional integrations may be skipped |
| ADR-003 | 2026-10-15 | Start with batch CSV ingestion; evaluate Airbyte after core models work | Smaller initial surface area and easier debugging/documentation | Start with orchestrated ingestion | Provisional; later revisit based on feasibility and current tool limits |
| ADR-004 | 2026-10-15 | Treat Cube.dev as optional rather than a prerequisite | The project should demonstrate analytics correctness before adding a semantic/API layer | Direct backend queries; Cube.dev | Evaluate only after stable metric models exist |
| ADR-005 | 2026-10-15 | Keep source CSVs out of Git by default | Avoid large repository and licensing/redistribution complications | Commit source data | Store download instructions and source attribution instead |

## Decision template

- **ID/date:**
- **Context/problem:**
- **Decision:**
- **Alternatives:**
- **Reason/trade-offs:**
- **Status:** Proposed / accepted / superseded

# Changes by section

Columns: the quickstart/notebook section the change touched, which artifact it applies to (Quickstart, Notebook, or Quickstart, Notebook), and what was done.

This reflects the current revision only (review feedback):
- Use "Interactive Warehouses" (not "Interactive Warehouses and Tables") as the general term.
- Remove Interactive Tables from the hands-on demo; make zero-copy interactive analytics (querying standard tables directly) the primary pattern, with a brief compatibility note on Interactive Tables.
- Substantially increase the row count in `BENCHMARK_FDN.HITS2_CSV` so the concurrent benchmark shows a clearer latency/throughput advantage.
- Remove the single-query "run once on interactive, then once on standard" comparison sections, keeping only the sequential 50-run benchmark and the concurrent benchmark.

| Section | Applies to | What was done |
| --- | --- | --- |
| Overview | Quickstart | Reworded to describe Interactive Warehouses (not "...and Tables") and added that they query standard tables directly via zero-copy, with no data conversion required. Removed the `architecture.png` diagram: it depicted a standard-table-to-interactive-table CTAS conversion step, which contradicted the "no data conversion required" text next to it. |
| What You'll Learn / What You'll Build | Quickstart | Dropped the "create an Interactive Table" framing; added a bullet on zero-copy querying standard tables directly. |
| Understand Interactive Warehouses | Quickstart | Renamed from "Understand Interactive Warehouses and Interactive Tables"; removed the "high-performance pair" framing. |
| Zero-copy interactive analytics | Quickstart | Promoted to the primary explanation of how an interactive warehouse queries data; removed the "currently in Public Preview" note to keep the wording neutral. |
| Interactive tables | Quickstart | Condensed to a single-sentence compatibility note appended to the end of the "Zero-copy interactive analytics" section (no separate heading). Removed the `interactive-tables-and-warehouses.png` diagram since a one-line note doesn't need a supporting image. |
| Use cases | Quickstart | Reworded to describe interactive warehouses generally, dropping "interactive tables"/"this pairing" phrasing. |
| Limitations | Quickstart | Removed the interactive-table-specific DML/ETL and "modify data" bullets; kept the warehouse-level limits (5s statement timeout + fallback warehouse, 24h min auto-suspend, no `CALL` support). |
| Setup - Data operations | Quickstart | Removed the now-unused `BENCHMARK_INTERACTIVE` schema from the manual SQL steps; reworded the warehouse-creation step to reference loading data into a standard table instead of building an interactive table. |
| Set up role, warehouse, and database | Quickstart, Notebook | Dropped `CREATE SCHEMA ... BENCHMARK_INTERACTIVE` (no longer needed); updated the GA note to say "Interactive Warehouses" only. |
| Data setup and loading | Quickstart, Notebook | Added a new, idempotent data-scale-up step that grows `BENCHMARK_FDN.HITS2_CSV` from 100,000 to roughly 2,000,000 rows with jittered `ClientIP`, `ResolutionWidth`, and `EventDate` values, so the concurrent benchmark shows a clearer latency/throughput advantage. Guarded by a row-count check so re-running the notebook doesn't re-expand the table. Implemented as a single `INSERT ... SELECT ... FROM table, TABLE(GENERATOR(ROWCOUNT => n))` statement (verified against a live Snowflake table to produce correct linear row growth). An earlier version used a Python loop of self-referencing `INSERT INTO t SELECT ... FROM t` statements, which was caught during review to double the row count on every iteration instead of growing it linearly, and was replaced before publishing. |
| Create an interactive table | Quickstart, Notebook | Removed entirely, including the `CREATE OR REPLACE INTERACTIVE TABLE ... CUSTOMERS` statement and its image. |
| Attach interactive table to a warehouse | Quickstart, Notebook | Renamed to "Attach a table to the interactive warehouse"; now attaches `BENCHMARK_FDN.HITS2_CSV` (a standard table) instead of the removed `BENCHMARK_INTERACTIVE.CUSTOMERS` interactive table. Relabeled the accompanying diagram's "Interactive Table" box and caption to "Standard Table". |
| Run queries with interactive warehouse | Quickstart, Notebook | Removed the misleading single-query comparison narrative, but kept its diagram (already relabeled to "Standard Table" in an earlier design refresh) and moved it into the "Zero-copy interactive analytics" section to illustrate querying a standard table directly on an interactive warehouse. |
| Compare to a standard warehouse | Quickstart, Notebook | Removed entirely (misleading single-query comparison). Its diagram was unreferenced after the removal and was dropped from the assets folder. |
| Sequential Query Benchmark | Quickstart, Notebook | Simplified the table reference so both the interactive and standard warehouse runs query `BENCHMARK_FDN.HITS2_CSV`. |
| Concurrent Query Benchmark | Quickstart, Notebook | Simplified the table reference so both the interactive and standard warehouse runs query `BENCHMARK_FDN.HITS2_CSV`. |
| Conclusion and Resources | Quickstart | Reworded to drop the interactive-table-conversion framing and emphasize zero-copy plus the benchmark results. Corrected the documentation link title to match the live page title ("Snowflake interactive analytics"). |
| Front matter | Quickstart | Removed the `snowflake-feature/interactive-tables` taxonomy tag, since the guide no longer focuses on Interactive Tables. |

## Image assets

| File | Action |
| --- | --- |
| `create-interactive-table.png`, `compare-to-standard-warehouse.png`, `py-iw-run.png`, `py-std-run.png`, `iw-run-exec.png`, `py-std-iw-run-exec.png`, `architecture.png`, `interactive-tables-and-warehouses.png` | Removed from `quickstart/getting-started-with-interactive-analytics/assets/` (kept as a local backup only, not committed to this repo). |
| `attach-interactive-table-to-warehouse.png` | Kept; box label and caption edited from "Interactive Table" to "Standard Table". |
| `run-queries-with-interactive-warehouse.png` | Kept; already relabeled to "Standard Table" in an earlier design refresh. Moved from the removed "Run queries with interactive warehouse" section into "Zero-copy interactive analytics". |

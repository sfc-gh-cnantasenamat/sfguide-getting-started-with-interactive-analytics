# Changes by section

Columns: the quickstart/notebook section the change touched, which artifact it applies to (Quickstart, Notebook, or Quickstart, Notebook), the originating request (if any), and what was done.

Requested changes (from the review feedback):
- R1 — remove the version / account-parameter checks (Interactive Warehouses and Tables are GA and enabled by default).
- R2 — use native SQL cells where possible instead of running SQL via Python, using the Snowflake Notebook's SQL/Python cells.
- R3 — note that standard tables can be queried directly now (zero-copy). **Deferred:** this content was removed and saved to `zero-copy-deferred-content.md` for a future, dedicated quickstart. The demo stays on the GA interactive-table path; zero-copy (querying standard tables directly) is Public Preview.
- R4 — add fallback warehouses for queries that run over 5 seconds.
- R5 — clarify auto-suspend / auto-resume and the 24-hour minimum auto-suspend in Limitations.
- R6 — call out configuring a fallback warehouse (protects p99) in the Limitations section.
- R7 — fix the "modify data" limitation (typos, and clarify interactive tables vs. standard/dynamic tables).
- "—" = not from an explicit request (consistency fix, cleanup, or follow-on).

A code in the "Requested change" column means that request is addressed by the row's "What was done".

| Section | Applies to | Requested change | What was done |
| --- | --- | --- | --- |
| Frontmatter (categories) | Quickstart | — | Replaced the incorrect hybrid-tables taxonomy tag with interactive-tables and interactive-warehouse. |
| Prerequisites | Quickstart | — | Updated the required role to ACCOUNTADMIN. |
| What You'll Learn / Understand - Interactive Warehouses / Understand - Zero-copy | Quickstart | R3 (deferred) | Zero-copy content that was added earlier — the What You'll Learn bullet, the "standard tables directly" clause in Interactive Warehouses, and the whole "Zero-copy interactive analytics" section (with its SQL example) — was removed and saved to `zero-copy-deferred-content.md` for a future quickstart. The Interactive Warehouses paragraph now reads "can query interactive tables." |
| Understand - Limitations | Quickstart | — | Dropped the tangential hybrid-tables and Iceberg-tables mentions, and removed the standalone zero-copy bullet (deferred with the rest of the zero-copy content). |
| Understand - Use cases | Quickstart | — | Rewrote the section around a three-domain taxonomy (AI & Agents, Customer-Facing Data Apps, Operational Analytics) with new examples (low-cost RAG, AI observability, high-concurrency MCPs, embedded analytics, trading & risk, supply chain & inventory), and framed the shared requirements as low latency, high concurrency, fresh data, and low cost per query. The three domains are formatted as bullet points and the prose avoids em/en dashes. Replaced `use-cases.png` with the matching updated diagram. |
| Understand - Limitations | Quickstart | R5 | Clarified that interactive warehouses support auto-suspend/auto-resume, with a 24-hour minimum auto-suspend. |
| Understand - Limitations | Quickstart | R6 | Called out configuring a fallback warehouse (protects p99) for queries that exceed the 5-second limit. |
| Understand - Limitations | Quickstart | R7 | Fixed typos and clarified how to modify data: interactive tables need a base-table update plus a full replace or TARGET_LAG refresh. (The zero-copy "standard table needs no extra step" clause was removed with the deferred content.) |
| Setup - Optional: Create warehouse | Quickstart | — | Kept as the warehouse-creation step (the notebook creates the warehouse in its setup cell instead). |
| Setup - Step 5: Query the data | Quickstart, Notebook | — | Aligned the preview query so both use the same statement (added the standard warehouse selection). |
| Load libraries and define custom functions | Quickstart, Notebook | R2 | Trimmed to the libraries the benchmark needs and removed the print helper, unused imports, and leftover placeholder data. |
| Load libraries and define custom functions | Notebook | — | Reworded the package note to say the libraries come pre-installed; added the data-load library; removed the image library once inline images were dropped. |
| Set up role, warehouse, and database | Quickstart, Notebook | R1, R2 | Removed the version and account-parameter checks, converted the step to a SQL cell, and set the role to ACCOUNTADMIN. |
| Set up role, warehouse, and database | Notebook | — | Expanded the cell to also create the warehouse, database, and schemas if they do not already exist. |
| The Data | Notebook | — | Added a self-contained, idempotent load that creates and fills the source table from the bundled file only when it is empty; removed the broken setup-script reference. |
| Create an interactive warehouse | Quickstart, Notebook | R2 | Converted from Python to a native SQL cell. |
| Create an interactive table | Quickstart, Notebook | R2 | Converted to a SQL cell. (The "this step is now optional" zero-copy note was removed and deferred.) |
| Attach interactive table to a warehouse | Quickstart, Notebook | R2 | Converted to a SQL cell and added a note that attaching is a caching optimization, not a requirement (describes cache-warming behavior; no zero-copy dependency). |
| Configure a fallback warehouse | Quickstart, Notebook | R4 | Added this new section on re-running queries that exceed the five-second limit on a standard warehouse. |
| Run queries with interactive warehouse | Quickstart, Notebook | R2 | Moved the session setup into a SQL cell; the timed query stays in Python. |
| Compare to a standard warehouse | Quickstart, Notebook | R2 | Moved the session setup into a SQL cell; the timed query stays in Python. |
| Run some queries concurrently | Quickstart, Notebook | — | Kept as the concurrent benchmark (logic unchanged). |
| Section images (per section) | Notebook | — | Added inline images from local files, then removed them since the quickstart already shows each section image. |
| All markdown callouts | Notebook | — | Prefixed each callout with the word Note and moved them to the bottom of their cells. |
| Callouts (asides) | Quickstart | — | Replaced the deprecated aside positive directive with the current Note: blockquote convention. |
| Notebook environment | Notebook | — | Removed the environment file since the required packages are pre-installed. |

# Project-level actions

These are not tied to a single document section, and none came from an explicit request.

| Action | Applies to | Requested change | What was done |
| --- | --- | --- | --- |
| On-Snowflake verification | Notebook | — | Ran the notebook end to end on Snowflake and confirmed all cells work, with sub-second benchmark queries. |
| Sync audit | Quickstart, Notebook | — | Compared the quickstart and notebook and confirmed the shared code matches. |
| Companion repository | Quickstart, Notebook | — | Created a public repo bundling both, each in a subfolder that mirrors its target repository path. |
| Images pull request | Notebook | — | Closed the earlier pull request that added section images, since it was no longer needed. |
| Local cleanup | Quickstart, Notebook | — | Removed redundant local notebook copies, deleted stray system files, and mirrored the working folder to the published repo layout. |

# Changes by section

Columns: the quickstart/notebook section the change touched, which artifact it applies to (Quickstart, Notebook, or Both), and what was done.

| Section | Applies to | What was done |
| --- | --- | --- |
| Frontmatter (categories) | Quickstart | Replaced the incorrect hybrid-tables taxonomy tag with interactive-tables and interactive-warehouse. |
| Prerequisites | Quickstart | Updated the required role to ACCOUNTADMIN. |
| What You'll Learn | Quickstart | Added a bullet on zero-copy interactive analytics. |
| Understand - Interactive Warehouses | Quickstart | Corrected the claim that interactive warehouses can only query interactive tables. |
| Understand - Zero-copy interactive analytics | Quickstart | Added this new section: querying standard tables directly, ADD TABLES as an optional optimization, and the caveats (clustering, ten-table warming cap, five-second timeout, when to still use interactive tables). |
| Understand - Limitations | Quickstart | Removed the incorrect claim that standard tables can't be queried; states standard tables are supported directly (dropped the tangential hybrid-tables and Iceberg-tables mentions). |
| Setup - Optional: Create warehouse | Quickstart | Kept as the warehouse-creation step (the notebook creates the warehouse in its setup cell instead). |
| Setup - Step 5: Query the data | Quickstart, Notebook | Aligned the preview query so both use the same statement (added the standard warehouse selection). |
| Load libraries and define custom functions | Quickstart, Notebook | Trimmed to the libraries the benchmark needs and removed the print helper, unused imports, and leftover placeholder data. |
| Load libraries and define custom functions | Notebook | Reworded the package note to say the libraries come pre-installed; added the data-load library; removed the image library once inline images were dropped. |
| Set up role, warehouse, and database | Quickstart, Notebook | Removed the version and account-parameter checks, converted the step to a SQL cell, and set the role to ACCOUNTADMIN. |
| Set up role, warehouse, and database | Notebook | Expanded the cell to also create the warehouse, database, and schemas if they do not already exist. |
| The Data | Notebook | Added a self-contained, idempotent load that creates and fills the source table from the bundled file only when it is empty; removed the broken setup-script reference. |
| Create an interactive warehouse | Quickstart, Notebook | Converted from Python to a native SQL cell. |
| Create an interactive table | Quickstart, Notebook | Converted to a SQL cell and added a note that this step is now optional. |
| Attach interactive table to a warehouse | Quickstart, Notebook | Converted to a SQL cell and added a note that attaching is a caching optimization, not a requirement. |
| Configure a fallback warehouse | Quickstart, Notebook | Added this new section on re-running queries that exceed the five-second limit on a standard warehouse. |
| Run queries with interactive warehouse | Quickstart, Notebook | Moved the session setup into a SQL cell; the timed query stays in Python. |
| Compare to a standard warehouse | Quickstart, Notebook | Moved the session setup into a SQL cell; the timed query stays in Python. |
| Run some queries concurrently | Quickstart, Notebook | Kept as the concurrent benchmark (logic unchanged). |
| Section images (per section) | Notebook | Added inline images from local files, then removed them since the quickstart already shows each section image. |
| All markdown callouts | Notebook | Prefixed each callout with the word Note and moved them to the bottom of their cells. |
| Notebook environment | Notebook | Removed the environment file since the required packages are pre-installed. |

# Project-level actions

These are not tied to a single document section.

| Action | Applies to | What was done |
| --- | --- | --- |
| On-Snowflake verification | Notebook | Ran the notebook end to end on Snowflake and confirmed all cells work, with sub-second benchmark queries. |
| Sync audit | Quickstart, Notebook | Compared the quickstart and notebook and confirmed the shared code matches. |
| Companion repository | Quickstart, Notebook | Created a public repo bundling both, each in a subfolder that mirrors its target repository path. |
| Images pull request | Notebook | Closed the earlier pull request that added section images, since it was no longer needed. |
| Local cleanup | Quickstart, Notebook | Removed redundant local notebook copies, deleted stray system files, and mirrored the working folder to the published repo layout. |

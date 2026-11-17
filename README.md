# Statistical Atlas — Flow Workspace

An offline, browser-based explorer for understanding how Statistics Canada survey and statistical programs relate to published statistical products. It is a personal knowledge workspace, not an official Statistics Canada application.

## What it does

The interface shows:

- **Inputs** — surveys, censuses, administrative-data programs, statistical accounts, registers and selected external-source records.
- **Outputs** — named current statistical tables and a small set of separately verified non-table dissemination products.
- **Connections** — documented source-program-to-product relationships.
- **Your knowledge** — editable notes on teams, sections, responsibilities, processes, projects, evidence, confidence and open questions.

Selecting an input highlights its documented outputs. Selecting an output highlights its documented source programs. Double-clicking opens the editable knowledge panel. Multiple inputs can connect to the same output.

The central orb is a visual processing metaphor. Animated lines represent the direction of documented source-to-product relationships; they do not represent measured processing time, workflow dependencies or every upstream data transformation.

## Data included

The embedded inventory was assembled on **17 November 2026**.

| Item | Count | Source and scope |
|---|---:|---|
| Base input records | 476 | Statistics Canada’s active survey and statistical-program register |
| Supplemental unresolved source codes | 64 | Source-program codes found in official table metadata but not reconciled to the base register |
| Current statistical-table products | 5,085 | Current records in the uploaded Web Data Service table inventory |
| Current tables withheld from the graph | 6 | Current tables with no source-program code in the official metadata |
| Selected non-table outputs | 9 | Seven The Daily release-family records, one dashboard and one infographic |
| Embedded output records | 5,094 | 5,085 tables plus 9 selected non-table products |
| Verified source connections | 5,755 | 5,732 table links and 23 selected publication links |
| Base programs with a mapped current product | 353 of 476 | Based on documented connections in the default product scope |
| Base programs with no verified output mapped | 123 | An inventory/research gap, not evidence that no output exists |

The workspace is designed to show expected outputs and recent cycles, not a complete historical archive. The default scope includes products updated in the last two years, longer-cycle carry-forwards and the latest available release-year cohort for sources without a recent product. It contains 3,203 products in that default view.

## Data sources

### Input register

The 476 base inputs come from Statistics Canada’s public list of active surveys and statistical programs:

- **Source:** Statistics Canada, *List of surveys and statistical programs by record number*
- **Retrieved:** 17 November 2026
- **URL:** https://www23.statcan.gc.ca/imdb-bmdi/pub/index-eng.htm

“Active” reflects the register’s status. It does **not** mean that a survey is collecting responses on a given day, that it will publish again, or that every record is a questionnaire-based survey. The register includes censuses, administrative-data programs, statistical accounts, registers, linked-data environments and selected partner-source records.

### Statistical-table outputs

The 5,085 statistical-table products come from the complete Web Data Service table inventory supplied as `getAllCubesListLite.json`.

- **Source:** Statistics Canada Web Data Service, `getAllCubesListLite`
- **Retrieved:** 17 November 2026
- **URL:** https://www150.statcan.gc.ca/t1/wds/rest/getAllCubesListLite
- **Records:** 8,283 total; 5,091 current and 3,192 archived

Only records marked current were included. Archived tables were excluded.

For each current table with source-program codes, the application creates a table-output record and connects it to every `surveyCode` listed in the official metadata. This preserves many-to-many and many-input-to-one-output relationships. The source-code array is treated as the documented basis for the connection.

### Non-table dissemination products

The application also includes a small, separately verified starting set of non-table dissemination products:

| Product type | Count | Verification basis |
|---|---:|---|
| The Daily release-family record | 7 | The release page or its “Definitions, data sources and methods” section explicitly identifies the source program(s) |
| Dashboard / visualization | 1 | The product’s source list explicitly identifies its contributing programs |
| Infographic | 1 | The product’s source list explicitly identifies its contributing programs |

These are not an exhaustive catalogue of The Daily articles, reports, dashboards, infographics, microdata files, geographic products or other publications. They are included to demonstrate the intended product-level model.

Examples include:

- *Energy statistics* — connects to the energy surveys explicitly listed in the release’s “Note to readers.”
- *Police-reported crime statistics in Canada* — connects to the Uniform Crime Reporting Survey and Homicide Survey, as identified in the release.
- *Elementary to Postsecondary Student Education Dashboard* — connects to the Elementary-Secondary Education Survey, Tuition and Living Accommodation Costs, and Postsecondary Student Information System.
- *Tourism activity* — connects to Frontier Counts, the National Travel Survey and the Visitor Travel Survey.

## What “verified connection” means

A connection is included in the visual source map only when it meets one of these conditions:

1. **Official metadata** — the official Web Data Service table record explicitly lists the source-program code in `surveyCode`.
2. **Publication source** — a Statistics Canada product page or release page explicitly identifies the contributing survey or program.
3. **User-checked source** — the user records a connection and confirms that the cited Statistics Canada page explicitly supports it.

The app records the evidence URL and a source statement for each connection. Search, topic tags and category grouping never create a source relationship.

## Important limitations

### Not a complete output catalogue

The table inventory is broad, but the non-table dissemination coverage is intentionally small. The application does **not** claim to include every current or historical Daily article, analytical report, journal article, infographic, dashboard, microdata file, geographic product, profile or publication.

The 31 generic output categories used in an earlier version were not treated as actual outputs. They are replaced by named product records and release-type filters.

### No full source-to-output lineage

A source-program connection means that the official metadata or publication identifies that program as a source. It does **not** establish:

- Every upstream file, system or processing step.
- The responsible team or section.
- The exact contribution of each source.
- Whether a source was used in every edition of a recurring product.
- Whether a product will be published again.

The application separates official evidence from user-entered understanding. User-entered confidence is a personal assessment, not independent verification.

### Current does not mean ongoing

“Current” follows the archive status in the supplied Web Data Service metadata. It does not mean that a survey is currently collecting data, that a product is actively updated, or that another release is scheduled.

For example, the Canadian Survey on Business Conditions release included in the starting set explicitly states that it was the survey’s final iteration. The application retains that status rather than implying future quarterly releases.

### Cycle-aware scope is a display heuristic

The default scope includes:

- Products released or metadata-updated between 17 November 2024 and 17 November 2026.
- Longer-cycle products within a frequency-specific window.
- The latest available release-year cohort for a source program with no product in the recent window.

Longer-cycle windows use a practical display heuristic. They are not an official Statistics Canada publication schedule or a guarantee that a product will be updated.

### Unresolved source codes

The 64 supplemental source codes are retained because they appear in official table metadata but were not reconciled to the 476-entry base register.

They are displayed as unresolved codes, not invented survey names. Their active/inactive status, current title and organizational ownership are not established in this version.

### Tables without source codes

Six current tables have no source-program code in the official metadata. They are held outside the verified connection graph and can be reviewed in the coverage view. They are not connected by inference.

## How the interface works

| Action | Behaviour |
|---|---|
| Single-click an input | Select it and highlight its documented outputs |
| Single-click the same input again | Deselect it |
| Double-click an input | Open the editable knowledge panel |
| Select an output | Highlight its documented source programs |
| Click a category’s left side | Expand or collapse that category |
| Click a category’s right side | Select or deselect its connection set |
| Search | Highlight matching titles, IDs, topic tags and user notes; it does not create connections |
| Export JSON | Download the entire workspace, including the embedded inventory and personal notes |
| Import JSON | Replace the current workspace with a previously exported version |

## Personal knowledge fields

For any input or output, the user can record:

- Section or organizational unit
- Teams involved
- Responsibilities
- Personal understanding
- Custom tags
- Inputs used
- Processing activities
- Outputs produced or supported
- Related projects
- Project-specific notes
- Open questions
- Evidence and sources
- Confidence
- Last-reviewed date

These fields are personal working notes. They are not official Statistics Canada metadata or an organizational designation.

## Saving and privacy

The application is a standalone HTML file. It does not use external libraries, analytics, fonts or background network requests.

- **No automatic save:** edits remain in the open browser tab until exported.
- **No automatic overwrite:** the browser controls download location and file handling.
- **Export JSON:** creates a timestamped local download containing the inventory, user notes and relationships.
- **Import JSON:** replaces the current workspace after confirmation; it does not merge files.
- **Keep the latest export:** the exported JSON is the portable master copy.

Do not import an untrusted JSON file. The application validates the expected workspace structure, but it is not a substitute for reviewing a file before importing it.

## Intended use

This is a personal research and knowledge-management prototype. It is intended to help build an evolving understanding of how Statistics Canada programs and published products relate.

It is not:

- An official Statistics Canada website
- A complete dissemination catalogue
- A source-to-output lineage system
- A publication schedule
- A data-quality or methodology authority
- A substitute for the official program, product and release pages

For authoritative information, use the official Statistics Canada program record, product page, release page and documentation linked from within the application.

## Credits

Data and source links are from Statistics Canada’s public website and Web Data Service. This project is independent and is not affiliated with, endorsed by, or produced by Statistics Canada.

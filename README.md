# Statistical Atlas — Flow Workspace

A single-file, offline HTML workspace for exploring how Statistics Canada source programs (inputs) connect to the products they feed (outputs), and for keeping your own notes on any of them.

## Quick start

1. Open `statistical_atlas.html` in a modern browser. No server, install or network connection is needed.
2. Search or filter inputs on the left and outputs on the right. Select any item to see its connections and the evidence behind each one.
3. Add notes to any item with **Edit selected**.
4. Save your work with **Export JSON**. Reload it later with **Import JSON**.

## What is in the data

| Item | Count (as built) |
|---|---:|
| Inputs (source programs) | 540 |
| Outputs | 5,383 |
| Verified relationships | 5,755 |
| Products held back (no source code in official metadata) | 6 |

**Outputs by type**

- Statistical tables: 5,085, from Statistics Canada's Web Data Service (`getAllCubesListLite`), current tables only. Archived tables are excluded.
- The Daily release records: 296. This is 7 earlier representative releases plus 289 releases from the Daily Atom feed, dated 2026-08-10 to 2026-11-17.
- Dashboard / visualization: 1.
- Infographic: 1.

## How the connections work

Every relationship has a role ("source program for"), a confidence level, a verification type, an evidence URL, an evidence statement and a checked date. All 5,755 current relationships come from official table metadata (the `surveyCode` field).

- **Daily release records have no links.** The 289 added records are listed with title, date and URL only. No source-program link is asserted for them, because the release pages were not checked in full for explicit source statements.
- **Nothing is inferred.** A link exists only where official metadata or an explicit source statement supports it.
- **Dashboards and infographics are barely covered.** Adding more is deferred until they can be linked to source programs with evidence.

## Features

- **Search the network.** Search across names, IDs, source codes, tags and your notes.
- **Filters.** Release type, scope, topic lens, sort, connected or unconnected only, documented only, and group-by for outputs.
- **Supplemental inputs.** 64 inputs are source codes not resolved to a named program. They are hidden unless you tick "Show supplemental".
- **Notes.** Per-item fields for section, teams, responsibilities, understanding, tags, inputs used, processing, outputs produced, projects, project notes, questions, sources, confidence and last reviewed.
- **Add output / Add relationship.** Create your own outputs and links. Each link records confidence, source and checked date.
- **Coverage & limitations.** Shows what the dataset does and does not include.
- **Export connections CSV.** Exports the relationships with their evidence.
- **Rename.** Names your workspace.

## Saving and sharing

- Your changes are held in the open page. Use **Export JSON** to save them; the browser does not keep them for you.
- The exported JSON holds the full workspace: inputs, outputs, relationships and your notes. Import it into a fresh copy of the HTML to restore it.
- The JSON also works for asking an LLM questions. Paste it into a chat and ask.

## Data sources

- Statistics Canada Web Data Service, `getAllCubesListLite`: https://www150.statcan.gc.ca/t1/wds/rest/getAllCubesListLite
- The Daily Atom feed: https://www150.statcan.gc.ca/n1/rss/dai-quo/0-eng.atom
- Individual Daily release pages, cited as evidence on the relevant records.

## Known limitations

- The data reflects a snapshot reviewed on 2026-11-17. It is not a live feed.
- Only current tables are included (5,091 current; 3,192 archived tables excluded).
- Daily records are a recent window, not a full history.
- Several Daily release pages could not be fully retrieved during review, so no evidence statements were taken from them.
- The file is large (about 6 MB) because all data is embedded. Very old browsers may load it slowly.

## Possible next steps

- Link Daily releases, dashboards and infographics to source programs, with an evidence quote and URL for each.
- Refresh tables and Daily records from the Web Data Service and Atom feed.
- Adapt the model for team use: projects as inputs, and process maps, business rules and use cases as outputs.
- Move the data to a database and add an LLM question-answering layer, as a longer-term idea.

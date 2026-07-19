# Awesome Parliamentary Elections Datasets

A curated list of datasets on national parliamentary / legislative elections — results,
parties, electoral rules, and election quality. Click a dataset for its full page: coverage,
key variables, caveats, and citation. Codebooks and papers are linked, never redistributed.

| Dataset | Type | What it contains | Coverage | Unit | Docs |
|---|---|---|---|---|---|
| **[CLEA](datasets/CLEA/)** — Constituency-Level Elections Archive | Results | Votes, seats, district magnitude and turnout per party per constituency. The only source combining global breadth with sub-national granularity. | ~190 countries, 1789– | constituency × party | [data](https://electiondataarchive.org/data-and-documentation/) · [codebook](https://electiondataarchive.org/wp-content/uploads/2026/01/clea_20251015_codebook_accessible.pdf) |
| **[NELDA](datasets/NELDA/)** — National Elections Across Democracy and Autocracy | Quality | Whether opposition was allowed, incumbent behaviour, fraud allegations, boycotts, violence, observers. Codes events, not results. | all states, 1945–2020 | election round | [data](https://nelda.co/) · [codebook](https://nelda.co/#codebook) · [paper](https://www.cambridge.org/core/journals/political-analysis/article/which-elections-can-be-lost/0474B124646DF486D1FD9A8E26D31DEC) |

**Type** — Results (votes and seats) · Parties · Rules (electoral systems and institutions) ·
Quality (integrity, conduct, regime context) · Regional (single-region or official sources).

## Adding an entry

Write `datasets/<NAME>/README.md` — a metadata table (data, codebook, paper, maintainer,
coverage, unit, licence), then **What it contains**, **Caveats**, **Citation** — and add one
row above, keeping the table sorted by Type.

## Licence

[CC0 1.0](LICENSE) — the list itself is public domain. The datasets it describes carry
their own licences; check each before use.

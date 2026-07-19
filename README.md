# Awesome Parliamentary Elections Datasets

A curated list of datasets on national parliamentary / legislative elections — results,
parties, electoral rules, and election quality. Click a dataset for its full page: coverage,
key variables, caveats, and citation. Codebooks are archived here; papers are linked.

| Dataset | Type | What it contains | Coverage | Links |
|---|---|---|---|---|
| **[CLEA](datasets/CLEA/)** | Results | Votes and seats per party per constituency | 190 countries, 1789– | [data](https://electiondataarchive.org/data-and-documentation/) · [codebook](datasets/CLEA/clea_20251015_codebook.pdf) |
| **[DPI](datasets/DPI/)** | Rules | Electoral formula, thresholds, seat shares, legislative fragmentation | ~180 countries, 1975–2023 | [data](https://data.iadb.org/dataset/the-database-of-political-institutions-dpi-2023) · [codebook](datasets/DPI/dpi2023_codebook.pdf) · [paper](https://doi.org/10.18235/0003049) |
| **[NELDA](datasets/NELDA/)** | Quality | Election conduct: competition, fraud, boycotts, violence | all states, 1945–2020 | [data](https://nelda.co/) · [codebook](datasets/NELDA/NELDA_Codebook_V6.pdf) · [paper](https://www.cambridge.org/core/journals/political-analysis/article/which-elections-can-be-lost/0474B124646DF486D1FD9A8E26D31DEC) |

**Type** — Results (votes and seats) · Parties · Rules (electoral systems and institutions) ·
Quality (integrity, conduct, regime context) · Regional (single-region or official sources).

## Adding an entry

Put the codebook in `datasets/<NAME>/` and write `datasets/<NAME>/README.md` — a metadata
table (data, codebook, paper, maintainer, coverage, unit, licence), then **What it
contains**, **Caveats**, **Citation**. Then add one row above, keeping the table sorted by
Type and every cell to a single short line; detail belongs on the dataset page.

## Licence

[CC0 1.0](LICENSE) — the list itself is public domain. The datasets it describes carry
their own licences; check each before use.

# Awesome Parliamentary Elections Datasets

A curated list of datasets on national parliamentary / legislative elections — results,
parties, electoral rules, and election quality. Click a dataset for its full page: coverage,
key variables, caveats, and citation. Codebooks are archived here, each with a condensed `codebook.md` — YAML frontmatter plus
one row per variable, for search and programmatic use. See [`CODEBOOK-SCHEMA.md`](CODEBOOK-SCHEMA.md).
Papers are linked.

| Dataset | Type | What it contains | Coverage | Links |
|---|---|---|---|---|
| **[CLEA](datasets/CLEA/)** | Results | Votes and seats per party per constituency | 190 countries, 1789– | [data](https://electiondataarchive.org/data-and-documentation/) · [codebook](datasets/CLEA/clea_20251015_codebook.pdf) · [md](datasets/CLEA/codebook.md) |
| **[PPEG](datasets/PPEG/)** | Results | Party-level votes and seats per lower-house election, with alliances | 73 democracies, 1942–2025 | [data](https://www.ppeg.wzb.eu) · [codebook](datasets/PPEG/codebook_ppeg_parl_2025v1.pdf) · [md](datasets/PPEG/codebook.md) |
| **[NED](datasets/NED/)** | Results | Presidential and parliamentary election results, one row per election | 212 countries, 1789–2023 | [data](https://www.nationalelectionsdatabase.com/) · [codebook](datasets/NED/codebook_elections_database_v2.pdf) · [md](datasets/NED/codebook.md) |
| **[WhoGov](datasets/WhoGov/)** | Parties | Cabinet membership: ministers, portfolios, party affiliation, leaders | worldwide, 1966–2021 | [data](https://www.whogov.net/) · [codebook](datasets/WhoGov/whogov_codebook.pdf) · [md](datasets/WhoGov/codebook.md) |
| **[DPI](datasets/DPI/)** | Rules | Electoral formula, thresholds, seat shares, legislative fragmentation | ~180 countries, 1975–2023 | [data](https://data.iadb.org/dataset/the-database-of-political-institutions-dpi-2023) · [codebook](datasets/DPI/dpi2023_codebook.pdf) · [md](datasets/DPI/codebook.md) · [paper](https://doi.org/10.18235/0003049) |
| **[CCP](datasets/CCP/)** | Rules | Constitutional events: new constitutions, amendments, suspensions | all countries, 1789–2025 | [data](http://www.comparativeconstitutionsproject.org) · [codebook](datasets/CCP/ccpcce_v6_codebook.pdf) · [md](datasets/CCP/codebook.md) |
| **[NELDA](datasets/NELDA/)** | Quality | Election conduct: competition, fraud, boycotts, violence | all states, 1945–2020 | [data](https://nelda.co/) · [codebook](datasets/NELDA/NELDA_Codebook_V6.pdf) · [md](datasets/NELDA/codebook.md) · [paper](https://www.cambridge.org/core/journals/political-analysis/article/which-elections-can-be-lost/0474B124646DF486D1FD9A8E26D31DEC) |
| **[LIED](datasets/LIED/)** | Quality | Ordinal index of electoral democracy from binary suffrage/election criteria | worldwide, 1789–2020 | [data](https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/WPKNIT) · [codebook](datasets/LIED/lied_6.8_description.pdf) · [md](datasets/LIED/codebook.md) |

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

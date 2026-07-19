# PPEG — Political Parties, Presidents, Elections and Governments

Party-level results for national lower-house elections, with alliance structure.

| | |
|---|---|
| **Data** | https://www.ppeg.wzb.eu |
| **Codebook** | [`codebook_ppeg_parl_2025v1.pdf`](codebook_ppeg_parl_2025v1.pdf) · [condensed markdown](codebook.md) |
| **Paper** | None — cite the dataset (Harvard Dataverse [DOI](https://doi.org/10.7910/DVN/5OAH7P)) |
| **Maintainer** | Werner Krause, Raphael Döring, Julia Stoppe — WZB Berlin Social Science Center |
| **Coverage** | 73 democracies, 1942–2025; 3,301 parties, 1,100 parliamentary elections |
| **Unit** | Party (or alliance member) × election · CSV / Stata / RDS |
| **Licence** | — (not stated in the codebook) |

## What it contains

One row per party per national lower-house election: `votes`, `v_share`, `seats`, `s_share`,
plus `electorate`, `total_vote`, `valid_vote` and `total_seats`. Party identity travels via
`party_id` and the Manifesto Project code `cmp`, which makes it joinable to MARPOR and
CHES. Alliance fields (`alliance`, `alliance_id`, `alliance_cmp`) record which parties ran
together and under what label.

Four PPEG files exist — parliamentary elections (this one), presidential elections,
governments, and a combined governments-plus-elections file.

## Caveats

- **National totals only.** There is no constituency dimension; the `_2ndtier` columns split
  national figures by electoral tier, not by district. Do not use it as a stand-in for
  district-level data in a districted system.
- `_2ndtier` applies to MMM systems; **MMP systems do not use it**.
- `estimate`/`estimate_2ndtier` mark imputed alliance-member vote shares, not reported ones.
- No global missing-value sentinel is documented; only `party_id` (993–999.5) and
  `cmp_parfam` (999/NA) have special codes.

## Citation

> Krause, Werner; Döring, Raphael; Stoppe, Julia; WZB Berlin, 2025, "PPEG - Political
> Parties, Presidents, Elections and Governments, Version 2025v1",
> https://doi.org/10.7910/DVN/5OAH7P, Harvard Dataverse, V1.

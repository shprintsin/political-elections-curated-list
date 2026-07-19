# LIED — Lexical Index of Electoral Democracy

An ordinal index of electoral democracy built from binary suffrage and election indicators.

| | |
|---|---|
| **Data** | https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/WPKNIT |
| **Codebook** | [`lied_6.8_description.pdf`](lied_6.8_description.pdf) · [condensed markdown](codebook.md) |
| **Paper** | Skaaning, Gerring & Bartuševičius (2015), "A Lexical Index of Electoral Democracy", *Comparative Political Studies* 48(12): 1491–1525 |
| **Maintainer** | Svend-Erik Skaaning, John Gerring, Henrikas Bartuševičius — Aarhus University |
| **Coverage** | Independent countries plus most semi-sovereign polities, colonies and protectorates, 1789–2020 |
| **Unit** | Country-year · XLSX |
| **Licence** | — (not stated in the description document) |

## What it contains

Fifteen binary indicators — `male_suffrage`, `female_suffrage`, `executive_elections`,
`legislative_elections`, `multi_party_legislative_elections`, `competitive_elections`,
`political_liberties`, plus transition, breakdown and turnover markers — aggregated into two
composite indices, `lexical_index` and `lexical_index_plus`.

Its appeal is the cumulative logic: each step up the scale requires a specific, observable
institutional fact rather than a judgement call, which makes the coding unusually
transparent and easy to audit against a country's history.

## Caveats

- **Values describe 31 December of each year**, not an average across the year. An election
  held in March and reversed in November leaves no trace in that year's score.
- `Cow` is the Correlates of War identifier, but **some codes were invented by the authors**
  for polities COW does not cover — a naive join on COW will not match those rows.
- The description text says "14 original indicators" while 15 are individually defined; and
  `Breakdown_type` is described as covering country-years with *transitions*, which reads as
  a copy-paste slip. Both are flagged as printed in the condensed codebook.
- Scores are revised between versions; the authors ask users to always take the newest.

## Citation

> Skaaning, Svend-Erik, John Gerring and Henrikas Bartuševičius. 2015. "A Lexical Index of
> Electoral Democracy." *Comparative Political Studies* 48(12): 1491–1525.

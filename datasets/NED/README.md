# NED — National Elections Database

National presidential and parliamentary election results, one row per election.

| | |
|---|---|
| **Data** | https://www.nationalelectionsdatabase.com/ |
| **Codebook** | [`codebook_elections_database_v2.pdf`](codebook_elections_database_v2.pdf) · [condensed markdown](codebook.md) |
| **Paper** | None stated in the codebook — cite the dataset |
| **Maintainer** | Benjamin Marx, Vincent Pons, Vincent Rollet |
| **Coverage** | 212 countries and territories, 1789–2023; 6,309 elections (1,409 presidential + 4,900 parliamentary) |
| **Unit** | Election (country × year, or × month where two of the same type fall in one year) · Stata |
| **Licence** | — (see the codebook's citation and licence section) |

## What it contains

Two files — `presidential_elections.dta` and `parliamentary_elections.dta` — in wide layout:
each candidate's or party's result is stored in numbered columns (`candidate_i`, `votes1_i`
for i = 1..39 presidential; `party_i`, `seats_i` for i = 1..74 parliamentary), alongside
`country`, `year`, `month`, `type_election`, `date` and `source`. Country identifiers
include `country_abb` and the Correlates of War code `country_cow`.

Parliamentary results cover unicameral parliaments and the lower chamber of bicameral ones,
in both presidential and parliamentary systems.

## Caveats

- **Wide format, not long.** The repeated `_i` columns must be reshaped before most analysis,
  and the index carries no meaning beyond rank order within the election.
- **No numeric missing-value sentinels** are defined; missingness is structural (unused `_i`
  slots are simply empty), so do not expect a `-99`-style convention.
- `month` is populated only where it is needed to disambiguate two same-type elections in one
  year — it is not a general election-date field; use `date` for that.

## Citation

> Marx, Benjamin, Vincent Pons and Vincent Rollet. 2025. National Elections Database,
> Version 2.

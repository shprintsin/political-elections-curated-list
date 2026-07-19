# DPI — Database of Political Institutions

Country-year coding of political and electoral institutions: who governs, under what rules,
and how fragmented the legislature is.

| | |
|---|---|
| **Data** | https://data.iadb.org/dataset/the-database-of-political-institutions-dpi-2023 |
| **Codebook** | [`dpi2023_codebook.pdf`](dpi2023_codebook.pdf) · [condensed markdown](codebook.md) — 8-page excerpt, see Caveats |
| **Paper** | [Cruz, Keefer & Scartascini (2021), *The Database of Political Institutions 2020*](https://doi.org/10.18235/0003049) (IDB-DT-56) |
| **Maintainer** | Cesi Cruz, Philip Keefer, Carlos Scartascini, Alberto Simpser — Inter-American Development Bank |
| **Coverage** | ~180 countries, 1975–2023 (DPI2023 extends DPI2020 by 2021–2022) |
| **Unit** | Country-year · XLSX / Stata DTA / CSV |
| **Licence** | CC BY-NC-ND 3.0 IGO (as stated on the DPI2020 record) |

## What it contains

Institutional structure, government stability, checks and balances, party affiliation and
ideology, and the fragmentation of governing and opposition parties in the legislature.
`SYSTEM` classifies the regime (parliamentary 2, assembly-elected president 1, presidential
0); `EXECRLC` codes executive party ideology (right 1, centre 2, left 3); `YRSOFFC`,
`FINITTRM`, `YRCURNT` and `MULTPL` track executive tenure and term limits.

For this list the relevant block is the legislative one — electoral formula (`HOUSESYS`,
`PLURALTY`), the representation threshold (`THRESH`), seat counts and party seat shares, and
the fractionalisation indices for government and opposition benches. **These variable names
are not confirmed against the archived excerpt** (see Caveats); treat them as a pointer, not
a citation.

## Caveats

- **The archived codebook is partial.** The published PDF runs to 8 pages and stops inside
  the chief-executive variables; it never reaches the legislative or electoral definitions.
  For those, consult the full DPI2020 *Changes and Variable Definitions* (29 pp, IDB-DT-56).
- **DPI is a secondary compilation, not primary returns.** Its own sources are Europa World,
  the Political Handbook of the World, IPU Parline and IFES ElectionGuide. It is a source for
  *rules and institutions*, never for votes or seat truth.
- **Values date to 1 January of each year**, not to election day. Joining DPI to an election
  by year silently attributes the pre-election configuration to the election.
- Missing-value convention: cells are **blank** where no information was available, and
  `NA` or `-999` where the question is not applicable. The two are not interchangeable.
- "House" always means the lower chamber; "Senate" the upper chamber where it exists and has
  power.
- The IDB portal blocks scripted downloads (403 to any non-browser client) — fetch by hand.

## Citation

> Cesi Cruz, Philip Keefer, Carlos Scartascini and Alberto Simpser. 2025. Codebook, Database
> of Political Institutions 2025. Washington, DC: Inter-American Development Bank Research
> Department.

## Local files

```
dpi2023_codebook.pdf   codebook, DPI2023 (8-page excerpt)
```

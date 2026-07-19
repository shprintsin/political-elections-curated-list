# CLEA — Constituency-Level Elections Archive

Constituency-level results for national legislative elections worldwide, harmonised into
one table.

| | |
|---|---|
| **Data** | https://electiondataarchive.org/data-and-documentation/ |
| **Codebook** | [`clea_20251015_codebook.pdf`](clea_20251015_codebook.pdf) |
| **Paper** | None — CLEA has no accompanying journal article; cite the dataset itself |
| **Maintainer** | University of Michigan (Kollman, Hicken, Caramani, Backer, Lublin) |
| **Coverage** | ~190 countries, 1789–present; lower chamber, separate upper-chamber release |
| **Unit** | Constituency × party · ~1.4M rows · CSV/Stata/R/SPSS |
| **Licence** | Free for academic use with citation |

## What it contains

One row per party per constituency per election: election `id`, year/month (`yr`, `mn`),
country (`ctr`), constituency (`cst`) and its magnitude (`mag`), party (`pty`), party votes
(`pv1`), candidate votes (`cv1`), and seats won (`seat`), plus turnout and electorate.

The only source combining global breadth with sub-national granularity, so it is the
standard input for reconstructing an electoral system rather than reading off national
totals. Companion releases: **GRED** (matching district shapefiles) and pre-computed
fractionalisation files (ENEP, ENPP, volatility). Appendix I documents country coverage,
Appendix II the party codes.

## Caveats

- Missing values are sentinels, not blanks: `-990` missing, `-992` unopposed. `pty >= 6000`
  is an independent; `cst >= 900` is an upper-tier PR block, not a geographic district.
- Coverage is uneven — older and non-OECD elections are often national-aggregate only.
- `pv1` and `cv1` are inconsistently populated across years; in FPTP systems use `cv1`.
- Some elections carry provisional rather than court-confirmed counts.

## Citation

> Kollman, Ken, Allen Hicken, Daniele Caramani, David Backer, and David Lublin. 2024.
> *Constituency-Level Elections Archive* [data file and codebook]. Ann Arbor, MI:
> University of Michigan, Center for Political Studies.

## Local files

```
clea_20251015_codebook.pdf        codebook, release 20251015 (current)
clea_20240419_appendix_I.pdf      country and election coverage
clea_20240419_appendix_II.xlsx    party codes
```

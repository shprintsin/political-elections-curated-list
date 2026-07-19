# WhoGov — Who Governs?

Who sits in national cabinets: ministers, portfolios, party affiliation and leaders.

| | |
|---|---|
| **Data** | https://www.whogov.net/ |
| **Codebook** | [`whogov_codebook.pdf`](whogov_codebook.pdf) · [condensed markdown](codebook.md) |
| **Paper** | None stated in the codebook — cite the dataset |
| **Maintainer** | Jacob Nyrup, Stuart Bramwell |
| **Coverage** | Not stated in the codebook; the released files run 1966–2021 |
| **Unit** | Two files — person × year, and country × year · CSV |
| **Licence** | — (not stated in the codebook) |

## What it contains

A within-country file with one row per cabinet member per year (`name`, `position`, `party`,
`portfolio_1`–`portfolio_4`, `prestige_1`–`prestige_4`, `gender`, `birthyear`, and the role
flags `core`, `minister`, `leader`), and a cross-sectional file aggregating those to one row
per country-year (cabinet size, gender composition, retention rates, government spells).

The party column carries a `partyfacts_id`, which bridges cabinet membership to party-level
datasets — the reason it pairs well with election results.

## Caveats

- **Snapshots are July of each year**, except 1966 (September) and 1970 (January). A minister
  who served February–May of a year does not appear in it.
- `deadyear` uses the literal value `A (2020)` for people alive at data collection — it will
  not parse as an integer.
- `leader` follows Archigos but **deliberately departs from it** in ten country-periods
  (Romania post-1990, Finland and Croatia post-2000, Portugal post-1976, and others).
- The codebook contains two source errors, transcribed as printed in the condensed codebook:
  `leaderexperience_continuous` appears twice with different definitions, and the
  `retention_rateadj_*` entries reference the wrong count variable.
- `title` and the military-title counts rest on a single directory with no cross-checking,
  and follow national naming custom — the codebook itself flags them as needing caution.

## Citation

> Nyrup, Jacob and Stuart Bramwell. WhoGov: Global Dataset on Members of Cabinets.
> https://www.whogov.net/ — see the project site for the current citation.

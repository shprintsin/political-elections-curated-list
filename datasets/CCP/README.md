# CCP — Chronology of Constitutional Events

When constitutions were written, amended, suspended and reinstated, country by country.

| | |
|---|---|
| **Data** | http://www.comparativeconstitutionsproject.org |
| **Codebook** | [`ccpcce_v6_codebook.pdf`](ccpcce_v6_codebook.pdf) · [condensed markdown](codebook.md) |
| **Paper** | None stated in the codebook — cite the dataset |
| **Maintainer** | Zachary Elkins, Tom Ginsburg, James Melton |
| **Coverage** | All independent countries, 1789–2025; 20,638 country-years |
| **Unit** | Constitutional event / country-year · TXT, CSV, Stata, XLSX |
| **Licence** | — (not stated in the codebook) |

## What it contains

Six fields: `COWCODE`, `COUNTRY`, `YEAR`, `SYSTID` (constitutional system), `EVNTID`
(constitutional event) and `EVNTTYPE` (what happened — new constitution, amendment, interim,
suspension, reinstatement, non-event).

It answers a question most institutional datasets cannot: *which* constitution was in force
in a given year, and whether that year saw a rupture. The companion file `ccpcnc`
(Characteristics of National Constitutions) codes what those constitutions actually say.

## Caveats

- **`EVNTTYPE` has no closed taxonomy table in the codebook.** The values are described in
  prose and examples; the condensed codebook assembles them and says so explicitly rather
  than presenting an official list.
- **`SYSTID` and `EVNTID` are not stable across versions** — do not treat them as permanent
  keys or join on them between releases.
- Country identifiers shift for successor states (Yugoslavia/Serbia); check `COWCODE`
  continuity before building a country panel.
- In multi-event years the file identifies the first chronological event, usually a `new`
  event — a year with several changes is not fully represented by its row.

## Citation

> Elkins, Zachary, Tom Ginsburg, and James Melton. 2026. "Chronology of Constitutional
> Events, Version 6." Comparative Constitutions Project.

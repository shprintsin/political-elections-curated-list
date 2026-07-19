# NELDA — National Elections Across Democracy and Autocracy

Event-level coding of what happened around every national election, competitive or not.

| | |
|---|---|
| **Data** | https://nelda.co/ (free, by request form) |
| **Codebook** | [`NELDA_Codebook_V6.pdf`](NELDA_Codebook_V6.pdf) · [condensed markdown](codebook.md) |
| **Paper** | [Hyde & Marinov (2012), "Which Elections Can Be Lost?"](https://www.cambridge.org/core/journals/political-analysis/article/which-elections-can-be-lost/0474B124646DF486D1FD9A8E26D31DEC) |
| **Maintainer** | Susan D. Hyde (UC Berkeley) and Nikolay Marinov (Univ. of Houston / Gothenburg) |
| **Coverage** | All independent states (Gleditsch & Ward list), 1945–2020 (v6) |
| **Unit** | Election round — every round coded separately |
| **Licence** | Free with citation |

## What it contains

58 yes/no/N-A/unclear variables per election round (`nelda1`–`nelda58`), each with a
free-text note field, plus `ccode`, `electionid`, `year`, `mmdd` and `type` (executive /
legislative / constituent assembly). The variables cover whether opposition was allowed and
multiple parties legal, whether the incumbent ran and won, pre- and post-election fraud
allegations, opposition boycotts, election-related violence and arrests, cancellation or
annulment, and the presence of international or Western observers.

It is the standard source for "was this election competitive, and what went wrong with
it" — the complement to a results dataset, not a substitute. Directly elected national
bodies only; indirect elections, by-elections and most referenda are excluded.

## Caveats

- No votes and no seats — NELDA codes election *events*, not results.
- Distributed by request form (Google Form), so it cannot be scripted into a pipeline.
- `unclear` is a substantive value meaning sources conflict or are absent — do not
  silently recode it to missing.

## Citation

> Hyde, Susan D., and Nikolay Marinov. 2012. "Which Elections Can Be Lost?"
> *Political Analysis* 20(2): 191–210.

## Local files

```
NELDA_Codebook_V6.pdf   codebook, version 6.0 (Jul 2021)
```

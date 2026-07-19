# Awesome Parliamentary Elections Datasets

A curated list of datasets on national parliamentary / legislative elections — results,
parties, electoral rules, and election quality. Each entry has a page under
[`datasets/`](datasets/) with its coverage, key variables, caveats, and citation.

Codebooks and papers are linked, never redistributed here.

## Election results

### [CLEA — Constituency-Level Elections Archive](datasets/CLEA/)

Constituency-level results for national legislative elections worldwide, harmonised into
one table: votes, seats, district magnitude, and turnout per party per constituency. The
only source combining global breadth with sub-national granularity. Beware the sentinels
(`-990` missing, `-992` walkover) and thin pre-war coverage.

- **Data:** https://electiondataarchive.org/data-and-documentation/
- **Codebook:** [release 20251015](https://electiondataarchive.org/wp-content/uploads/2026/01/clea_20251015_codebook_accessible.pdf)
- **Coverage:** ~190 countries, 1789–present · constituency × party · CSV/Stata/R
- **Cite:** Kollman, Hicken, Caramani, Backer & Lublin (2024), *Constituency-Level Elections Archive*, University of Michigan.

## Election quality and context

### [NELDA — National Elections Across Democracy and Autocracy](datasets/NELDA/)

Event-level coding of what happened around every national election: whether opposition was
allowed, incumbent behaviour, fraud allegations, boycotts, violence, cancellation, and
international observers. The standard source for "was this election competitive" — but it
codes events, not results, and is distributed by request form rather than direct download.

- **Data:** https://nelda.co/
- **Codebook:** [v6](https://nelda.co/#codebook) · **Paper:** [Hyde & Marinov (2012)](https://www.cambridge.org/core/journals/political-analysis/article/which-elections-can-be-lost/0474B124646DF486D1FD9A8E26D31DEC)
- **Coverage:** all independent states, 1945–2020 · election round · 58 coded variables
- **Cite:** Hyde & Marinov (2012), "Which Elections Can Be Lost?", *Political Analysis* 20(2): 191–210.

---

## Adding an entry

Create `datasets/<NAME>/README.md` and add a block here under the right heading:

```markdown
### [NAME — full name](datasets/NAME/)

Two or three sentences: what it contains, what it is good for, the one caveat to know.

- **Data:** <download URL>
- **Codebook:** <URL> · **Paper:** <URL>
- **Coverage:** <countries, years> · <unit of observation> · <formats>
- **Cite:** <Author(s) (Year), *Title*, Publisher.>
```

The dataset page adds a metadata table (data, codebook, paper, maintainer, coverage, unit,
licence), a **What it contains** section on key variables, **Caveats**, and **Citation**.

## Licence

[CC0 1.0](LICENSE) — the list itself is public domain. The datasets it describes carry
their own licences; check each before use.

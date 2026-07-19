---
name: "WhoGov"
id: "whogov"
version: "V3 / V3.1"
date: null
description: "Composition of national cabinets: ministers, portfolios, party affiliation and leader identity."
scope: "Members of national cabinets and government leaders."
years: null
type: "parties"
data_url: "https://www.whogov.net/"
codebook_url: "whogov_codebook.pdf"
paper_title: null
paper_url: null
citation: null
---

# WhoGov — codebook (Nyrup & Bramwell)

Condensed from the official codebook for search and reference. Authoritative source:
[`whogov_codebook.pdf`](whogov_codebook.pdf).

## At a glance
- **Unit of observation:** Two datasets, different units — Appendix A "within-country dataset" is one row per cabinet position-holder per year; Appendix B "cross-sectional dataset" is one row per country-year (aggregated).
- **Coverage:** Not stated in the codebook (this document covers only the two appendices transcribed).
- **Files:** Two schemas: (A) within-country dataset, (B) cross-sectional dataset. The codebook does not give file names.
- **Key identifiers:** `country_isocode` + `year` (both files); `id` (row id, within-country file only); `name` (person, within-country file).

## Missing values and sentinels
| Code | Meaning |
|---|---|
| `A (2020)` | `deadyear` sentinel: person still alive at the time the data was gathered. |

## Variables

### A. Within-country dataset (one row per cabinet position-holder per year)
| Variable | Label | Type | Values / units | Notes |
|---|---|---|---|---|
| `year` | Year | — | — | July for all years except 1966 (September only, data availability) and 1970 (January instead of July). |
| `country_isocode` | Country's alpha-3 ISO code | — | ISO-3166 alpha-3 | — |
| `country_name` | Country name | — | — | — |
| `id` | A row id | — | — | — |
| `position` | The person's position in the cabinet | — | — | — |
| `name` | The person's name | — | — | Standardized across years. |
| `title` | The person's title, e.g. Dr., Gen., Lt. Gen. | — | — | Standardized to the most frequent title used for that person in the original dataset, applied across all years for that person; solely relies on the "Chief of State And Cabinet Members Of Foreign Governments" directory; no extra checks performed; coding follows national customs (e.g. some countries consistently address PhDs as 'Dr.', others not). |
| `gender` | The person's gender | — | — | Primarily coded from the person's name; in some cases looked up or relied on country experts. |
| `birthyear` | The person's year of birth | — | year | Added when available; where only age at a given point in time was available, birthyear = that year minus the age. |
| `deadyear` | The person's year of death | — | year, or sentinel | `A (2020)` if the person is still alive at the time the data was gathered. |
| `party` | Abbreviation for the person's party affiliation | — | — | See Appendix F of the source PDF for further detail (not included in this transcription — page range not read). |
| `party_english` | Name of the party in English | — | — | — |
| `party_otherlanguage` | Name of the party in the local language or another commonly used language | — | — | Prioritizes languages using the Latin alphabet. |
| `core` | Whether the person is a core cabinet member | 0/1 | 1 = core | Core positions = cabinet ministers, prime ministers, presidents, vice presidents, vice prime ministers, members of the politburo, members of a military junta. Coded manually on a country-by-country basis. |
| `minister` | Whether the person is a cabinet minister | 0/1 | 1 = minister | Deputy and junior ministers are NOT coded as ministers. Coded manually on a country-by-country basis. |
| `leader` | Whether the person is the de facto leader of the country for that year | 0/1 | 1 = leader | Coded relying on Archigos (2009), with documented deviations (see Notes). |
| `classification` | A classification of the position | — | — | See Appendix H of the source PDF for further detail (not included in this transcription). |
| `portfolio_1` | A standard category of the portfolio | — | — | See Appendix H. |
| `prestige_1` | The prestige of portfolio_1 | — | — | See Appendix H. |
| `portfolio_2` | A standard category of the portfolio, if the position includes several portfolios | — | — | See Appendix H. |
| `prestige_2` | The prestige of portfolio_2 | — | — | See Appendix H. |
| `portfolio_3` | A standard category of the portfolio, if the position includes several portfolios | — | — | See Appendix H. |
| `prestige_3` | The prestige of portfolio_3 | — | — | See Appendix H. |
| `portfolio_4` | A standard category of the portfolio, if the position includes several portfolios | — | — | See Appendix H. |
| `prestige_4` | The prestige of portfolio_4 | — | — | See Appendix H. |
| `m_finance` | Whether the person is minister of finance | 0/1 | 1 = yes | — |
| `m_defense` | Whether the person is minister of defense | 0/1 | 1 = yes | — |
| `m_agriculture` | Whether the person is minister of agriculture | 0/1 | 1 = yes | — |
| `m_foreignaffairs` | Whether the person is minister of foreign affairs | 0/1 | 1 = yes | — |

### B. Cross-sectional dataset (one row per country-year)
| Variable | Label | Type | Values / units | Notes |
|---|---|---|---|---|
| `year` | Year | — | — | Same July/September(1966)/January(1970) convention as dataset A. |
| `country_isocode` | Country's alpha-3 ISO code | — | ISO-3166 alpha-3 | — |
| `country_name` | Country name | — | — | — |
| `n_total` | Number of entries for the country in the dataset | count | — | Includes unoccupied positions and multiple positions held by the same person. |
| `n_individuals` | Number of unique persons in the cabinet | count | — | Excludes unoccupied positions and positions held by the same person (deduplicated headcount). |
| `n_core` | Number of core members in cabinet | count | — | Excludes unoccupied positions, positions held by the same person, and posts not considered core positions. |
| `n_minister` | Number of cabinet ministers | count | — | Only includes cabinet ministers. |
| `leader` | Name of the person coded as being the de facto leader of the country | — | — | — |
| `leader_start_date` | Day the leader enters office | date | — | Relies on Archigos (2009). |
| `leader_end_date` | Day the leader exits office | date | — | Relies on Archigos (2009). |
| `leader_party` | Party of the leader | — | — | — |
| `leaderexperience_continuous` | Number of years the person has been leader of the country in a row | years | count starts at 1 | Resets if the leader is removed; count starts at 1 when the leader first appears as leader in the dataset; imprecise for leaders who came to power before 1966. |
| `leaderexperience_continuous` (total variant) | Number of years the person has been leader of the country in total | years | count starts at 1 | The codebook lists this second definition under the SAME variable name `leaderexperience_continuous` as the "in a row" version above — see Notes and gotchas. Count starts at 1 when the leader first appears in the dataset; imprecise for leaders who came to power before 1966. |
| `n_female_total` | Number of women in n_total | count | — | — |
| `n_female_core` | Number of women in n_core | count | — | — |
| `n_female_minister` | Number of women in n_minister | count | — | — |
| `n_militarytitle_total` | Number of people in n_total with a military title | count | — | No extra checks performed; solely relies on the "Chief of State And Cabinet Members Of Foreign Governments" directory; based on national customs (some countries consistently use military titles, others do not) — use cautiously. |
| `n_militarytitle_core` | Number of people in n_core with a military title | count | — | Same caveat as n_militarytitle_total. |
| `n_militarytitle_minister` | Number of people in n_minister with a military title | count | — | Same caveat as n_militarytitle_total. |
| `average_total` | Average tenure for people in n_total | — | — | — |
| `average_core` | Average tenure for people in n_core | — | — | — |
| `average_minister` | Average tenure for people in n_minister | — | — | — |
| `retention_rate_total` | Share of people in n_total who were in n_total the previous year | share | — | — |
| `retention_rate_core` | Share of people in n_core who were in n_core the previous year | share | — | — |
| `retention_rate_minister` | Share of people in n_minister who were in n_minister the previous year | share | — | — |
| `retention_rateadj_total` | Share of people in n_total who were in n_total the previous year, adjusted for cabinet-size expansion | share | — | Adjusted so n_total is held constant; retention rate is not influenced by an expansion of the cabinet. |
| `retention_rateadj_core` | Adjusted retention rate, core (as described, text as printed refers to n_minister/n.ministers — likely a codebook copy-paste error, see Notes) | share | — | Text in the source literally reads "share of people in n_minister who were in n.ministers the previous year" under this variable name — see Notes and gotchas. |
| `retention_rateadj_minister` | Share of people in n_minister who were in n_minister the previous year, adjusted for cabinet-size expansion | share | — | Adjusted so n_total (as printed) stays constant; retention rate not influenced by cabinet expansion. |
| `age_total` | Average age for people in n_total | years | — | — |
| `age_core` | Average age for people in n_core | years | — | — |
| `age_minister` | Average age for people in n_minister | years | — | — |
| `age_share` | Share of n_total where age is coded | share | — | — |
| `n_party` | Number of parties represented in the government | count | — | — |
| `party_share` | Share of members in n_total where party is coded | share | — | Excludes UN representative, Ambassadors, and Central Bank governors. |
| `m_finance` | Name of the minister of finance | — | — | — |
| `m_agriculture` | Name of the minister of agriculture | — | — | — |
| `m_defense` | Name of the minister of defense | — | — | — |
| `m_foreignaffairs` | Name of the minister of foreign affairs | — | — | — |
| `govern_name` | Name of the government | — | — | Based on Döring (2019) or Bértoa (2020). |
| `govern_start_date` | Day the government enters office | date | — | Based on Döring (2019) or Bértoa (2020). |
| `govern_end_date` | Day the government exits office | date | — | Based on Döring (2019) or Bértoa (2020). |
| `system_category` | The regime type | — | — | Classified by Cheibub et al. (2010), updated by Bjørnskov and Rode (2018). |

## Notes and gotchas
- **Year convention:** all years use July as the reference month, except 1966 (data only available for September) and 1970 (January used instead of July). This applies to both datasets.
- **`leader` deviates from Archigos (2009)** in the following country-periods (footnote 9): Romania after 1990; Finland after 2000; Croatia after 2000; Portugal after 1976; Bhutan 1998-2007; Syria 1966-1970; Timor Leste 2002-2018; Papua New Guinea (2011, described as "mistake in Archigos"); Somalia 1966-1969 (parliamentary system); Albania 1992-1997 (parliamentary system). Do not assume raw Archigos leader coding holds for these.
- **`title` and `n_militarytitle_*` reliability:** both rely solely on the "Chief of State And Cabinet Members Of Foreign Governments" directory with no additional verification; title/military-title usage follows national custom (inconsistent across countries) — the codebook itself flags these as needing cautious use.
- **`deadyear` sentinel:** value is the literal string/code `A (2020)` when the person was alive as of the 2020 data-gathering date — not a numeric year; do not parse as integer without handling this case.
- **`core` vs `minister`:** these are distinct, not nested by definition in the text — `core` includes prime ministers/presidents/VPs/politburo/junta members in addition to cabinet ministers, while `minister` excludes deputy and junior ministers. Both are coded manually per country.
- **Duplicate variable name `leaderexperience_continuous`:** the source PDF (pages 3-4) presents two different definitions under the identical name — one counting consecutive years as leader ("in a row", resets on removal) and one counting total years as leader ("in total", does not reset). This is transcribed as printed; downstream code should verify which column is actually present in the shipped CSV/dta (likely one is truly named `leaderexperience_total`) rather than assuming the codebook's literal text.
- **`retention_rateadj_core` text anomaly:** as printed, the description under this variable name refers to "n_minister"/"n.ministers" rather than "n_core", and the `retention_rateadj_minister` entry's normalizing reference reads "n_total" rather than "n_minister". These read as copy-paste artifacts in the original codebook (each `retention_rateadj_*` definition appears to have been cloned from the previous one without fully updating the referenced count variable). Transcribed verbatim; verify actual column semantics against the shipped data before use.
- **`party` further detail** is deferred to Appendix F, and **`classification`/`portfolio_n`/`prestige_n`** further detail is deferred to Appendix H — neither appendix's content was in the 6 transcribed pages (only Appendices A and B were present in the source PDF as read).
- **`age_total`/`age_core`/`age_minister`** are only meaningful in light of `age_share` (share of `n_total` where age is actually coded) — averages may be based on partial coverage.
- **`party_share`** excludes UN representatives, Ambassadors, and Central Bank governors from its denominator — relevant when comparing to `n_total`, which does not exclude these.

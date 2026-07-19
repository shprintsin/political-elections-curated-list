---
name: "National Elections Database"
id: "ned"
version: "2"
date: "2025-05"
description: "National presidential and parliamentary election results with candidate- and party-level vote and seat counts."
scope: "National presidential elections and lower-chamber parliamentary elections."
years: "1789-2023"
type: "results"
data_url: "https://www.nationalelectionsdatabase.com/"
codebook_url: "codebook_elections_database_v2.pdf"
paper_title: null
paper_url: null
citation: "Marx, Benjamin, Vincent Pons and Vincent Rollet. 2025. National Elections Database, Version 2."
---

# National Elections Database — codebook (v2)

Condensed from the official codebook for search and reference. Authoritative source:
[`codebook_elections_database_v2.pdf`](codebook_elections_database_v2.pdf).

## At a glance
- **Unit of observation:** one row per election (Country × Year, or Country × Year × Month when two elections of the same type occur in one year — that combination is the proper identifier).
- **Coverage:** 6,309 national elections total (1,409 presidential + 4,900 parliamentary), 1789–2023, across 212 countries and independent territories. Authors: Benjamin Marx, Vincent Pons, Vincent Rollet (May 2025).
- **Files:** two `.dta` files listed in the codebook — `presidential_elections.dta` (1,409 presidential elections) and `parliamentary_elections.dta` (4,900 parliamentary elections; results given for unicameral parliaments and for the lower chamber of multicameral parliaments, in both presidential and parliamentary systems). The codebook does not describe a separate "long" format file or a wide-vs-long distinction — it documents only the wide layout described below (results for each candidate/party stored as numbered `_i` variables, 1 to 39 for presidential candidates, 1 to 74 for parliamentary parties).
- **Key identifiers:** `country`, `year`, `month` (non-missing only when disambiguation is needed), `type_election`, `date`, `source`; `country_abb` (three-letter code) and `country_cow` (Correlates of War code) also included.

## Missing values and sentinels
The codebook does not define explicit numeric sentinel/missing-value codes (e.g., no stated -99/-990 convention). Missingness is instead handled structurally:
| Code | Meaning |
|---|---|
| — | `month` is non-missing only when two elections of the same type occur in the same year (otherwise blank/missing). |
| — | Results for constituent-assembly elections have not been systematically collected (see `flag_constituent`, parliamentary file). |
| — | No other sentinel/missing codes are stated in the codebook. |

## Variables

### Presidential Elections (`presidential_elections.dta`)

**General variables**
| Variable | Label | Type | Values / units | Notes |
|---|---|---|---|---|
| `country` | Country in which the election took place | — | — | — |
| `year` | Year of the election | — | — | — |
| `month` | Month of the election | — | — | Non-missing only when two elections of the same type occur during a single year; Country × Year × Month is then the proper identifier |
| `type_election` | Election type | string | "Presidential" | — |
| `date` | Date of the election | date | — | For a two-round election, the date of the second round is used |
| `source` | Identifier of the source of election results | — | — | — |

**Results variables** (given for each candidate, ordered 1 to 39)
| Variable | Label | Type | Values / units | Notes |
|---|---|---|---|---|
| `candidate_i` | Name of candidate n°i | — | — | i = 1..39 |
| `party_i` | Party of candidate n°i | — | — | i = 1..39 |
| `votes1_i` | Number of votes for candidate n°i during the first (or only) round | numeric | count | i = 1..39 |
| `votes2_i` | Number of votes for candidate n°i during the second round | numeric | count | i = 1..39 |
| `vote_share1_i` | Vote share for candidate n°i during the first (or only) round | numeric | share | i = 1..39 |
| `vote_share2_i` | Vote share for candidate n°i during the second round | numeric | share | i = 1..39 |
| `e_votes_i` | Number of electoral college votes for candidate n°i | numeric | count | i = 1..39 |
| `e_vote_share_i` | Electoral college vote share for candidate n°i | numeric | share | i = 1..39 |

**Flag variables and country codes**
| Variable | Label | Type | Values / units | Notes |
|---|---|---|---|---|
| `flag_two_round` | Flags elections with two rounds | flag | — | — |
| `flag_inconsequential` | Flags inconsequential elections for reasons other than a coup | flag | — | — |
| `flag_inconsequential_note` | Reason why flag_inconsequential is equal to 1 | string | e.g., election postponed, canceled, etc. | — |
| `flag_coup` | Flags elections that were shortly followed by a coup or revolution | flag | — | — |
| `flag_plebiscite` | Flags elections that took the form of a plebiscite or referendum | flag | — | — |
| `flag_unopposed` | Flags elections in which only one candidate ran | flag | — | — |
| `flag_indirect` | Flags elections where the president is indirectly elected | flag | — | — |
| `country_abb` | Three-letter country code | string | — | — |
| `country_cow` | Correlates of War country code | — | — | — |

### Parliamentary Elections (`parliamentary_elections.dta`)

**General variables**
| Variable | Label | Type | Values / units | Notes |
|---|---|---|---|---|
| `country` | Country in which the election took place | — | — | — |
| `year` | Year of the election | — | — | — |
| `month` | Month of the election | — | — | Non-missing only when two elections of the same type occur during a single year; Country × Year × Month is then the proper identifier |
| `type_election` | Election type | string | "Parliamentary" | — |
| `date` | Date of the election | date | — | For a two-round election, only the second round's date is considered |
| `source` | Identifier of the source of election results | — | — | — |
| `total_seats` | Total number of seats | numeric | count | Includes vacant and appointed seats |

**Results variables** (given for each party, ordered 1 to 74)
| Variable | Label | Type | Values / units | Notes |
|---|---|---|---|---|
| `party_i` | Name of party or coalition n°i | — | — | i = 1..74 |
| `seats_i` | Number of seats gained by party or coalition n°i | numeric | count | i = 1..74 |
| `seats_share_i` | Share of the seats of parliament won by party or coalition n°i | numeric | share | i = 1..74 |

**Flag variables and country codes**
| Variable | Label | Type | Values / units | Notes |
|---|---|---|---|---|
| `flag_constituent` | Flags constituent assembly | flag | — | Based on V-Dem's identification of constituent-assembly elections |
| `flag_inconsequential` | Flags inconsequential elections for reasons other than a coup | flag | — | — |
| `flag_inconsequential_note` | Reason why flag_inconsequential is equal to 1 | string | e.g., election postponed, canceled, etc. | — |
| `flag_coup` | Flags elections that were shortly followed by a coup or revolution | flag | — | — |
| `flag_vacant_seats` | Flags elections that left vacant seats in parliament | flag | — | — |
| `flag_vacant_seats_nb` | Number of vacant seats in parliament | numeric | count | — |
| `flag_appointed` | Flags elections in which some seats were not elected directly | flag | — | Includes seats appointed by the government, a foreign government, indirectly elected, reserved for people holding a specific office, or reserved for a special ethnic group |
| `flag_appointed_nb` | Number of seats for which MPs were not elected directly | numeric | count | — |
| `flag_non_partisan` | Flags elections with no parties | flag | — | i.e., with only independent candidates |
| `country_abb` | Three-letter country code | string | — | — |
| `country_cow` | Correlates of War country code | — | — | — |

## Notes and gotchas
- **Data sources (both files), priority order for identifying elections:** V-Dem; PARLGOV; Manifesto Project (MP); Nohlen books; Database of Political Institutions (DPI); Global Elections Database (GLOBAL); Constituency-Level Elections Archive (CLEA); Adam Carr's Election Archive (Psephos, AC); African Elections Database (AED); European Elections Database (EED); Political Database of the Americas (PDA); IPU PARLINE; IFES Election Guide; USA Presidential Elections Database; Wikipedia (used only when academic sources were lacking).
- **Presidential results priority order:** Nohlen ≻ AC ≻ AED ~ EED ~ PDA ~ USA ≻ IFES ≻ Wikipedia. **Presidential date-recovery priority order:** V-Dem ≻ Wikipedia ≻ AC ≻ IFES ≻ Wikidata.
- **Parliamentary results priority order:** PARLGOV ≻ MP ≻ Nohlen ≻ DPI ≻ GLOBAL ≻ AC ≻ AED ~ PDA ≻ IPU ≻ IFES ≻ Wikipedia. **Parliamentary date-recovery priority order:** V-Dem ≻ PARLGOV ≻ MP ≻ Wikipedia ≻ AC ≻ IFES ≻ Wikidata.
- **Indirect presidential elections** are included only when (a) the president was selected by an electoral college elected solely to choose the president, AND (b) manipulation of vote shares was made difficult by the electoral rules. Specifically excluded: indirect elections with multiple rounds (multi-round structure lets parties build alliances and manipulate the outcome), and indirect elections with unpledged electors where the electoral college had fewer than 1,000 electors. Exception: the U.S. Electoral College is included despite its size because its 538 electors are pledged.
- **Collective presidencies** (a collective body appointed to the presidency, e.g. Bosnia and Herzegovina) are excluded entirely from the database.
- **Candidate ranking (presidential):** candidates are ranked first by electoral college score (if applicable), then by second-round score (if applicable), then by first-round score.
- **Party ranking (parliamentary):** parties are ranked by seat share, then by vote share at the second round, then by vote share at the first round.
- **Coalitions (parliamentary):** the database distinguishes *ex ante* coalitions (officially formed before the election, e.g. the CDU/CSU coalition in Germany) from *ex post* coalitions (formed after the election based on results, e.g. Germany's Große Koalition of CDU/CSU + SPD). Ex ante coalition members are merged and stored as a single party/coalition row; ex post coalition members are kept as separate party rows. Full identification/classification method is in the Data Appendix of Marx et al. (2024), Section A.4.
- **Constituent assemblies:** defined as bodies whose sole function is to draft and adopt a new constitution; assemblies with additional roles (legislating, electing the president, managing the budget) are NOT considered constituent assemblies. V-Dem is the source used to identify and flag these (`flag_constituent`). Results for constituent-assembly elections have not been systematically collected.
- **Appointed seats:** reported results correspond only to the elected seats; `flag_appointed` / `flag_appointed_nb` record whether/how many seats in that parliament were appointed rather than elected (by the head of state, a foreign government, indirectly elected, reserved for an office-holder, or reserved for a specific ethnic group).
- **Two-round elections:** for both presidential and parliamentary two-round elections, the recorded `date` is the date of the second round only; first- and second-round votes/shares are kept as separate variables (`votes1_i`/`votes2_i`, `vote_share1_i`/`vote_share2_i`) for presidential races. For parliamentary races only the second round is considered for date purposes (no explicit first/second-round seat-share split is defined at the general-variable level beyond `seats_i`/`seats_share_i`).
- **Source-selection method:** sources were prioritized by frequency of use, fewer internal inconsistencies, and broader geographic/time coverage; internal consistency of each source was verified before use. Full extraction methodology is in the Data Appendix (Section A) of Marx, Pons, and Rollet's "Electoral Turnovers" (2024), the paper that Version 1.0 of this dataset supported.
- **Version history:** v1.0 covered 1946–2018 and included turnover-analysis variables (e.g., whether an election was associated with an electoral turnover) that are **not** carried into v2.0 — for those, use v1.0. v2.0 (this codebook) expands coverage to 1789–2023, adds COW country codes and country abbreviations, and improves data quality.
- **License:** Creative Commons Attribution 4.0 International. Citation: Marx, B., Pons, V., & Rollet, V. (2025). *National Elections Database (Version 2.0)*. www.nationalelectionsdatabase.com.

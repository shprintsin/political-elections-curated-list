---
name: "Political Parties, Presidents, Elections and Governments"
id: "ppeg"
version: "2025v1"
date: null
description: "Party-level results for national lower-house elections, with alliance structure and second-tier splits."
scope: "National lower-house elections in 73 democracies; party and electoral-alliance level."
years: "1942-2025"
type: "results"
data_url: "https://www.ppeg.wzb.eu"
codebook_url: "codebook_ppeg_parl_2025v1.pdf"
paper_title: null
paper_url: "https://doi.org/10.7910/DVN/5OAH7P"
citation: "Krause, Werner; Doering, Raphael; Stoppe, Julia; WZB Berlin, 2025, \"PPEG - Political Parties, Presidents, Elections and Governments, Version 2025v1\", https://doi.org/10.7910/DVN/5OAH7P, Harvard Dataverse, V1."
---

# PPEG — codebook (parliamentary file, 2025v1)

Condensed from the official codebook for search and reference. Authoritative source:
[`codebook_ppeg_parl_2025v1.pdf`](codebook_ppeg_parl_2025v1.pdf).

## At a glance
- **Unit of observation:** one row per political party (or electoral alliance / alliance member) per national lower-house election.
- **Coverage:** 73 democracies in Africa, the Americas, Asia, Australia, and Europe; period 1942–2025 (Oct 31). Dataset overall (all 4 PPEG files combined) contains 3301 political parties, 1100 parliamentary elections, 402 presidential elections, 2044 governments. Per-country time spans, party counts, election counts, and unique-observation counts are tabulated on pp.3-5 of the source PDF (73 countries, Albania through Venezuela).
- **Key identifiers:** `iso3c`, `iso2c`, `cname_en`, `edate` (election date); `party_id` (alphanumeric, country-prefixed); `cmp` (Manifesto Project party code) for cross-dataset joins.
- **Four PPEG files total:** (1) parliamentary elections (this file), (2) presidential elections, (3) national governments, (4) combined governments + corresponding parliamentary elections. Downloadable at https://www.ppeg.wzb.eu.
- **Citation:** Krause, Werner; Döring, Raphael; Stoppe, Julia; WZB Berlin, 2025, "PPEG - Political Parties, Presidents, Elections and Governments, Version 2025v1", https://doi.org/10.7910/DVN/5OAH7P, Harvard Dataverse, V1. Contact: ppeg@wzb.eu.

## Missing values and sentinels
| Code | Meaning |
|---|---|
| — | The codebook text does not specify a generic numeric missing-value sentinel (e.g. no -99/-999 stated). |
| `party_id` 993 | Special coding, e.g. "Initiative Committee" |
| `party_id` 994 | Spoilt votes |
| `party_id` 995 | Against all candidates |
| `party_id` 996 | Minorities |
| `party_id` 997 | Others/Independent candidates |
| `party_id` 998 | Independent/Non-partisan candidates |
| `party_id` 998.5 | Independent candidates in the cabinet |
| `party_id` 999 | Other parties |
| `party_id` 999.5 | Members of "other parties" in the cabinet |
| `cmp_parfam` 999/NA | Missing information (party family) |

## Variables
| Variable | Label | Type | Values / units | Notes |
|---|---|---|---|---|
| `iso3c` | ISO 3166-1 alpha-3 codes | string | three-letter country code | Per ISO 3166-1. |
| `iso2c` | ISO 3166-1 alpha-2 code | string | two-letter country code | Per ISO 3166-1. |
| `cname_en` | Country name (English) | string | — | — |
| `edate` | Date of national lower house election | date | — | If the election lasted several days, the last date was coded. By-elections for single seats/districts are not considered. |
| `mmm` | Mixed member majoritarian electoral system | binary | yes/no | Indicates whether a mixed member majoritarian (MMM) electoral system was in use (e.g. Italy 1993-2005, Bulgaria 1990 and 2009, Croatia 1993-2001, North Macedonia 1998). |
| `mmm_doc` | Mixed member majoritarian electoral system documented | binary | yes/no | Set to "yes" if either the votes, the seats, or both are documented for both the proportional and the majoritarian tier. |
| `electorate` | Number of eligible voters | numeric | count | In MMM systems: proportional-tier value. In PR-nationwide + multi-member-district systems (Nicaragua, Guatemala): national-constituency value. |
| `electorate_2ndtier` | Number of eligible voters, 2nd tier | numeric | count | MMM: majoritarian-tier value (else missing). PR-nationwide + multi-member-district systems: multi-member-district value. |
| `total_vote` | Total number of votes cast including invalid votes | numeric | count | Tier scoping as for `electorate`/`electorate_2ndtier` above. In panachage systems where only per-party vote totals are available, `total_vote` indicates the actual number of citizens who cast at least one vote or voted invalidly. |
| `total_vote_2ndtier` | Total number of votes cast including invalid votes, 2nd tier | numeric | count | See `electorate_2ndtier` note. |
| `valid_vote` | Total number of valid votes | numeric | count | In panachage systems, reflects the sum of the votes documented per party. |
| `valid_vote_2ndtier` | Total number of valid votes, 2nd tier | numeric | count | — |
| `total_seats` | Total number of seats in the lower chamber | numeric | count | Proportional-tier value in MMM systems; national-constituency value in PR+multi-member-district systems. |
| `total_seats_2ndtier` | Total number of seats in the lower chamber, 2nd tier | numeric | count | Majoritarian-tier / multi-member-district value. |
| `party_id` | Alphanumeric party code | string | iso2c + database-specific numeric code | E.g. FR9 = French Communist Party (PCF). Coding ranges: 1-599 political parties; 600-799 electoral pacts (incl. those that became parties); 800-879 regional/local electoral pacts; 880-989 other parties that are part of an electoral pact; 993 special coding (e.g. "Initiative Committee"); 994 spoilt votes; 995 against all candidates; 996 minorities; 997 others/independent candidates; 998 independent/non-partisan candidates; 998.5 independent candidates in the cabinet; 999 other parties; 999.5 members of "other parties" in the cabinet. |
| `cmp` | Manifesto Project party code | numeric | Manifesto Project code | Join key to Manifesto Project data via `cname_en` + `edate` + `cmp`. Currently linked to Manifesto Project Dataset version 2025a. |
| `cmp_parfam` | Manifesto Project party family coding | categorical | 10 Ecological; 20 Socialist; 30 Social democratic; 40 Liberal; 50 Christian democratic; 60 Conservative; 70 Nationalist; 80 Agrarian; 90 Ethnic and regional; 95 Special issue; 98 Electoral alliances without a dominant party; 999/NA Missing information | — |
| `pinitials` | Party name abbreviation | string | — | — |
| `pname_en` | English translation of party name | string | — | — |
| `pname_or` | Original party name | string | — | — |
| `votes` | Number of votes gained by each party | numeric | count | Proportional-tier value in MMM systems; national-constituency value in PR+multi-member-district systems; first-round votes in two-round systems (e.g. France); voters' first preferences in STV systems; per-party vote total under panachage. |
| `votes_2ndtier` | Number of votes gained by each party, 2nd tier | numeric | count | Majoritarian-tier / multi-member-district value. |
| `v_share` | Share of votes gained by each party | numeric | proportion/percent | Tier-scoped as `votes`. |
| `v_share_2ndtier` | Share of votes gained by each party, 2nd tier | numeric | proportion/percent | Tier-scoped as `votes_2ndtier`. |
| `estimate` | Estimated election results (binary flag) | binary | yes/no | Flags whether the party's vote count and vote share were estimated from an electoral alliance's results. Calculated when a party was part of an electoral alliance and the alliance-members' seat shares were known but not their individual vote shares: `vote_share_p = (seat_p / seat_a) * vote_a`, where `seat_p` = seats won by the party, `seat_a` = seats won by the corresponding electoral alliance, `vote_a` = votes won by the alliance. Also used where two or more parties presented joint lists in single districts (e.g. Belgium 1946-58, Norway 1949-1981): joint-list votes were distributed to individual parties according to their total vote share in the respective election. |
| `estimate_2ndtier` | Estimated election results, 2nd tier | binary | yes/no | Same logic as `estimate`, applied to the 2nd-tier (majoritarian) values. |
| `v_share_wgt` | Weighted share of votes gained by each party | numeric | proportion/percent | Formula: `v_share * prop + v_share_2ndtier * maj`, where `prop = seats/total_seats` and `maj = seats_2ndtier/total_seats` (tier weights by relative size). In non-MMM electoral systems, equals `v_share`. |
| `seats` | Number of seats gained by each party | numeric | count | Tier-scoped as `votes` (proportional tier in MMM; national constituency in PR+multi-member-district systems). In MMP systems the seats document the final distribution in the national parliament including those won by majority vote. |
| `seats_2ndtier` | Number of seats gained by each party, 2nd tier | numeric | count | Majoritarian-tier / multi-member-district value. |
| `s_share` | Share of seats gained by each party | numeric | proportion/percent | Includes seats won in all tiers in the case of segmented electoral systems. |
| `alliance` | Categorical indicator for electoral alliances | categorical | "Electoral alliance" (entry is an electoral alliance) / "Electoral alliance member" (entry is part of an electoral alliance) | For alliance members, see `alliance_id`, `alliance_cmp`, `alliance_initials`, `alliance_en`, `alliance_or` for details of the corresponding electoral pact. |
| `alliance_id` | Alphanumeric electoral alliance code | string | — | Same coding convention as `party_id`. |
| `alliance_cmp` | Manifesto Project party code (for the alliance) | numeric | Manifesto Project code | Join key to Manifesto Project data via `cname_en` + `edate` + `alliance_cmp`. Currently linked to version 2025a. |
| `alliance_initials` | Electoral alliance abbreviation | string | — | — |
| `alliance_en` | English translation of electoral alliance name | string | — | — |
| `alliance_or` | Original electoral alliance name | string | — | — |
| `region` | Region of country | categorical | World Bank Development Indicators regions | — |
| `continent` | Continent of country | categorical | World Bank Development Indicators continents | — |
| `eu_member` | Membership European Union | binary/flag | — | — |
| `eu_east` | East European member of the European Union | binary/flag | — | — |
| `eu_since` | Year of entry in European Union | numeric | year | — |
| `eu_exit` | Year of withdrawal from the European Union | numeric | year | — |
| `oecd` | Membership OECD | binary/flag | — | — |
| `oecd23` | Membership OECD-23 | binary/flag | — | — |
| `oecd_since` | Year of entry in OECD | numeric | year | — |

## Notes and gotchas
- **Unit/aggregation level.** One row = one party (or alliance/alliance-member entry) within one lower-house election in one country. National-level aggregates only — no district/constituency-level rows exist in this file.
- **`_2ndtier` variables exist only for mixed/segmented systems.** They are populated when a country's electoral system has two tiers (MMM: proportional tier = base variables, majoritarian tier = `_2ndtier` variables; or PR-nationwide-constituency + multi-member-district systems like Nicaragua/Guatemala: national-constituency = base variables, multi-member-district = `_2ndtier` variables). In all other (single-tier) systems, the `_2ndtier` variables are set to missing. Affected pairs: `electorate`/`electorate_2ndtier`, `total_vote`/`total_vote_2ndtier`, `valid_vote`/`valid_vote_2ndtier`, `total_seats`/`total_seats_2ndtier`, `votes`/`votes_2ndtier`, `v_share`/`v_share_2ndtier`, `seats`/`seats_2ndtier`, `estimate`/`estimate_2ndtier`. In some MMM cases the data lists vote counts for both tiers but only provides aggregate SEAT counts for the party (i.e. `votes_2ndtier` may be populated while `seats_2ndtier` is not) — check both before assuming a tier is fully documented; `mmm_doc` flags whether either tier's votes/seats/both are documented.
- **`mmm` vs `mmm_doc`.** `mmm` = the country/election actually used a mixed-member-majoritarian system. `mmm_doc` = whether PPEG's sources let them document both tiers for that election. A `mmm == "yes"` election can still have `mmm_doc == "no"` if only aggregate/one-tier data was available.
- **MMP (mixed member proportional) systems** (e.g. Bolivia, Germany, New Zealand, Venezuela) are NOT split across `_2ndtier` variables — proportional-tier voting results are reported in the base variables, and `seats` documents the FINAL distribution in the national parliament, including seats won by majority vote. Do not expect `mmm`/`mmm_doc`/`_2ndtier` fields to describe MMP mechanics — those fields are specific to MMM.
- **Two-round systems** (e.g. France): the data documents first-round votes and the total number of seats gained after the second round — i.e. `votes`/`v_share` are first-round-only, but `seats` reflects the final (post-second-round) outcome. Do not compute an implied "vote-to-seat" ratio treating `votes` as final-round votes.
- **STV systems**: `votes` = voters' first preferences only; `seats` = final distribution after all vote transfers. Same caution as two-round systems — votes and seats are not from the same counting stage.
- **Panachage systems** (voters get as many votes as there are seats to distribute in a district) have heterogeneous vote documentation depending on source availability: Luxembourg provides a "theoretical number of electoral votes per party" since 1994; some countries (e.g. El Salvador after 2015) provide only percentage values based on total voters; where possible (e.g. Honduras after 2005, Mauritius) PPEG provides total votes gained per party. In panachage, `valid_vote` = sum of votes documented per party, and `total_vote` = actual number of citizens who cast at least one vote or voted invalidly — these two are NOT simply additive/consistent across parties the way they are in single-vote systems, because one voter can generate multiple party votes.
- **Alliance handling — what is split and what is not.** `alliance` distinguishes an "Electoral alliance" row (the pact itself, treated like a party) from an "Electoral alliance member" row (a constituent party within the pact). If votes/seats of the SINGLE constituent parties are known, they are documented individually with `alliance_id` etc. pointing to the pact; if that breakdown is unavailable, ONLY the pact's own aggregate election result is documented (no member-level rows). When member vote shares are unknown but member SEAT shares are known, PPEG imputes (`estimate`/`estimate_2ndtier` = "yes") each member's votes/vote-share proportionally from the pact's total votes using each member's seat share: `vote_share_p = (seat_p/seat_a) * vote_a`. Joint lists presented by 2+ parties in single districts (e.g. Belgium 1946-58, Norway 1949-1981) are handled similarly: joint-list votes are distributed to individual parties by their overall vote share in that election, also flagged via `estimate`. Always check the `estimate`/`estimate_2ndtier` flags before treating a member party's `votes`/`v_share` as directly observed.
- **Party inclusion criteria** — a party appears in the dataset only if at least one of: (1) it won a seat in at least one covered election; (2) it fielded a presidential candidate (in fields >10 candidates, contestants below 0.5% of the vote are folded into a residual "Others" category instead of being individually coded); (3) it was part of, or supported, a cabinet during the covered period. This is a coverage filter, not a completeness guarantee — minor parties that never won seats, never ran presidentially, and never joined/supported a cabinet are absent even if they contested elections.
- **Party-identifier linkage to other datasets.** `cmp` (and `alliance_cmp` for pacts) is the Manifesto Project party code; join to Manifesto Project data using the triple `cname_en` + `edate` + `cmp` (or `alliance_cmp`). Currently pinned to Manifesto Project Dataset version 2025a — a version mismatch is a merge trap if Manifesto Project codes are renumbered/added in later releases. `party_id` is PPEG's own alphanumeric code (iso2c + numeric); the numeric ranges 600-999.5 are NOT ordinary parties (electoral pacts, regional pacts, spoilt votes, minorities, independents, "other parties", cabinet-only residual categories) — filter these out before treating `party_id` as an ordinary-party identifier.
- **Sources are hierarchical, not per-row-flagged in this file**: national election commissions/authorities first, then Political Data Yearbook (European Journal of Political Research), Electoral Studies & West European Politics election reports, the Nohlen/Grotz/Hartmann/Stöver "Elections in ..." handbook series, Mackie & Rose (1991), Political Database of the Americas, IPU PARLINE, IFES/electionguide.org, Adam Carr's Election Archive, and Wikipedia — in that priority order. The codebook does not indicate a per-row source variable in this file.
- **By-elections excluded**: single-seat/single-district by-elections are not coded into `edate`/rows — only general lower-house elections.
- **No documented generic missing-value sentinel** (e.g. no -99/-999 pattern) was found in the readable text for the continuous vote/seat/count variables; only `party_id` and `cmp_parfam` have documented special/missing codes (see table above).
- All 13 pages of the source PDF were read; none were unreadable or partial.

TL;DR: Transcribed all 40 documented variables (plus the coverage table of 73 countries) from the 13-page PPEG parliamentary-election codebook into `2-data/1-raw/ppeg_parl_2025v1/codebook.md`. Nothing was left undefined and all pages were readable; the biggest gotchas are the tier-splitting rules for MMM/PR+multi-member-district systems, the two-round/STV vote-vs-seat staging mismatch, and how alliance member votes get imputed/estimated from seat shares.

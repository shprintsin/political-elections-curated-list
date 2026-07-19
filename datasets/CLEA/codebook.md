# CLEA — codebook (release 20251015)

Condensed from the official codebook for search and reference. Authoritative source:
[`clea_20251015_codebook.pdf`](clea_20251015_codebook.pdf).

## At a glance

- **Unit of observation:** one row = one candidate/party within one constituency within one election (constituency-level results); some rows are party-only (no candidate) depending on source reporting.
- **Coverage:** lower-chamber and upper-chamber legislative elections worldwide; 18 dataset releases from 2008-08-15 to 2025-10-15 (current). Countries/territories covered: full list of ~190 countries/territories given in the codebook (see `CTR_N` row) — includes Taiwan, Kosovo, and Somaliland, which are assigned non-UN codes by CLEA since they lack a UN Standard Country Code.
- **Files:** lower and upper chamber results are separate files sharing the same variable list/descriptions — lower-chamber files begin `clea_lc`, upper-chamber files begin `clea_uc`. Supplemental lower-chamber-only files: Indirect Elections (Norway 1822-1903, Sweden 1866-1908), Preferential Vote Counts (Australia, Estonia 1992, Ireland, Malta, Nauru), Latvia Ordinal Ballot Vote Counts, Lebanon Confessional Quota Preference Vote Counts (2018 election only).
- **Key identifiers:** `ID` (election), `CTR`/`CTR_N` (country, UN M49 code except Taiwan=1001/Kosovo=1002/Somaliland=1003), `CST`/`CST_N` (constituency), `PTY`/`PTY_N` (party), `CAN` (candidate). Party codes are matched consistently across lower/upper/presidential elections within a country and persist across elections unless the party changes name, merges, or splits.

## Missing values and sentinels

Global sentinel codes used across most numeric variables (apply per-variable; not every code applies to every variable — see the Notes cell in each row):

| Code | Meaning |
|---|---|
| -990 | Missing Data (information not available / category not applicable) |
| -992 | Uncontested Election (i.e., a single candidate contested the election) |
| -994 | Suspended Election |
| -996 | Disqualified (SEAT only) |
| -997 | Voluntarily Withdrew (SEAT only) |
| -998 | Death (SEAT only) |
| -999 | ID sentinel for U.S. House elections prior to 1880 (no federal timing rules; scheduling varied by state) |

## Variables

| Variable | Label | Type | Values / units | Notes |
|---|---|---|---|---|
| `RELEASE` | Dataset Release | numeric, categorical | 1=2008-08-15; 2=2010-02-03; 3=2010-12-15; 4=2011-09-14; 5=2012-12-17; 6=2013-12-04; 7=2014-08-12; 8=2016-05-23; 9=2016-10-24; 10=2017-05-30; 11=2018-05-07; 12=2018-11-19; 13=2019-06-17; 14=2020-12-16; 15=2022-01-11; 16=2022-09-08; 17=2024-04-19; 18=2025-10-15 | Indicates which release added the constituency-level data. |
| `ID` | Election Identifier | numeric | unique per election | -999 = U.S. House elections before 1880 (no fixed federal schedule). |
| `RG` | Region | categorical | Africa; Asia; Western Europe; Eastern Europe; Latin America; North America; Caribbean; Oceania | Eight regions used in the most recent release. |
| `CTR_N` | Country Name | string | full list in codebook (~190 entries, e.g. Afghanistan … Zimbabwe) | — |
| `CTR` | Country Code | numeric | UN M49 codes (unstats.un.org/unsd/methodology/m49); Taiwan=1001, Kosovo=1002, Somaliland=1003 | Taiwan, Kosovo, Somaliland lack a UN code; CLEA assigns these three itself. |
| `YR` | Election Year | numeric | year | — |
| `MN` | Election Month | numeric, categorical | 01=January … 12=December | Given if available. |
| `SUB` | Sub-National Geographical Unit | string/numeric | -990 Missing; -992 Uncontested; -994 Suspended | Unit above constituency level; only present if the original source data contains it. |
| `CST_N` | Constituency Name | string | — | Name of the area a representative/group of representatives represents. |
| `CST` | Constituency Code | numeric | 001-900 = geographic/lower-tier/majoritarian-tier constituencies; 901-999 = PR tier / upper tier(s) / non-geographic (ethnic, religious, identity, social-class) / additional macro-unit constituencies | Constituencies within a country sorted alphabetically by name then coded; code may or may not persist across elections if redistricting/renaming occurs. Special/minority districts (e.g. pre-1996 NZ Maori seats) or semi-autonomous regions (e.g. Greenland in Danish elections) get the next code after the last alphabetically sorted geographic district. Single-tier systems use only lower-tier codes. |
| `MAG` | District Magnitude | numeric | seats allocated in the constituency; -990 Missing; -992 Uncontested | — |
| `PTY_N` | Party Name | string | original-language name preferred, else transliterated/English name; "Others"/special category labels (e.g. France's "miscellaneous right-wing", "regionalists and separatists"); "Independents" (grouped) or "Independent" (individually reported) | Independents affiliated with but not officially standing under a party's label may be labeled reflecting both (e.g. "Independent Labour"), but are coded as independents. Full list: Appendix II (separate file). |
| `PTY` | Party Code | numeric | 0001-3999 political parties; 3996 None of these candidates; 3997 Elected (Iceland/Sweden early elections, party results unavailable); 3998 No against for uncontested (Denmark); 3999 Unknown; 4000 "Others" (>2 small parties grouped); 4001- special "others" subtypes; 4998 Write-in; 4999 Blank/Scattering; 5001-5999 electoral coalitions/alliances; 6000 "Independents" (>2 grouped); 6001- individual independents/special independent types | Assigned by sorting parties alphabetically by `PTY_N` per country. Same numeric code persists for a party across lower/upper/presidential elections within a country and across time, UNLESS the party renames, merges, or splits (new code then issued to the successor). Codes for "other"/"independent" categories are reassigned per election — NOT stable across elections. India: some elections have 4,000+ independent candidates, given 5-digit party codes. |
| `CAN` | Candidate Name | string | -990 Missing; -992 Uncontested; -994 Suspended | Japan, Taiwan, Thailand, Ukraine use a numeric code instead of the actual name; full candidate-name lists for Japan/Taiwan (original language) available on the CLEA website. |
| `PEV1` | Number Of Eligible Voters (First Round) | numeric | count; -990 Missing; -992 Uncontested; -994 Suspended | If a runoff exists, this is the first-round figure. |
| `VOT1` | Votes Cast (First Round) | numeric | count; -990/-992/-994 | Total votes cast for all candidates in the constituency (first round if runoff). |
| `VV1` | Valid Votes (First Round) | numeric | count; -990/-992/-994 | May exceed `VOT1` or `PEV1` under multiple-vote systems. Sometimes computed as the manual sum of `PV1`/`CV1` when the source lacks a valid-vote total but no party/candidate is confirmed missing. |
| `IVV1` | Invalid Votes (First Round) | numeric | count; -990/-992/-994 | Invalid + spoilt votes; treatment of blank votes depends on how the electoral commission reports them (see blank-vote rule in Notes). |
| `TO1` | Turnout (First Round) | numeric | fraction; -990/-992/-994 | CLEA's own calculation = `VOT1`/`PEV1`, NOT an officially reported turnout rate; can exceed 1 when reported votes cast exceed reported eligible voters. |
| `CV1` | Candidate Votes (First Round) | numeric | count; -990/-992/-994 | Most useful when >1 candidate from the same party runs in a constituency. In preferential systems = first-preference votes (see Preferential Vote Counts file). In ordinal-ballot systems (Latvia) = party-list votes plus/minus candidate-specific votes (see Latvia Ordinal Ballot Vote Counts file). |
| `CVS1` | Candidate Vote Share (First Round) | numeric | fraction; -990/-992/-994 | Can be ≥1 depending on officially reported `CV1` totals. |
| `PV1` | Party Votes (First Round) | numeric | count; -990/-992/-994 | Sum of votes for all candidates from the same party in the constituency; repeated across each of that party's candidate rows. |
| `PVS1` | Party Vote Share (First Round) | numeric | fraction; -990/-992/-994 | Computed as `PV1`/`VV1` (or sum of party votes if `VV1` unavailable) when source doesn't report it or has evident errors. Repeated per candidate row of the same party, so per-constituency sum of `PVS1` can exceed 1. |
| `PEV2` | Number Of Eligible Voters (Second Round) | numeric | count; -990/-992/-994; set to Missing if no runoff | — |
| `VOT2` | Votes Cast (Second Round) | numeric | count; -990/-992/-994; Missing if no runoff | — |
| `VV2` | Valid Votes (Second Round) | numeric | count; -990/-992/-994; Missing if no runoff | — |
| `IVV2` | Spoilt/Invalid Votes (Second Round) | numeric | count; -990/-992/-994; Missing if no runoff | — |
| `TO2` | Turnout (Second Round) | numeric | fraction; -990/-992; Missing if no runoff | CLEA's own calculation = `VOT2`/`PEV2`; can exceed 1. |
| `CV2` | Candidate Votes (Second Round) | numeric | count; -990/-992/-994 | Most useful with >1 same-party candidate. |
| `CVS2` | Candidate Vote Share (Second Round) | numeric | fraction; -990/-992/-994 | Can be ≥1 depending on officially reported `CV2`. |
| `PV2` | Party Votes (Second Round) | numeric | count; -990/-992/-994; Missing if no runoff | Repeated per candidate row of the same party. |
| `PVS2` | Party Vote Share (Second Round) | numeric | fraction; -990/-992/-994; Missing if no runoff | Repeated per candidate row of the same party; per-constituency sum can be ≥1. |
| `SEAT` | Seats Won | numeric | number of seats (PR) or win/no-win indicator (SMP/MMP); -990 Missing; -992 Uncontested; -994 Suspended; -996 Disqualified; -997 Voluntarily Withdrew; -998 Death | — |
| `ELEC` (lower-chamber supplemental: Indirect Elections file) | Number of Electors | numeric | count | Number of electors chosen in the indirect election. Applies only to Norway (1822-1903) and Sweden (1866-1908). |
| `EV` (lower-chamber supplemental: Indirect Elections file) | Electors Won By Party | numeric | count | Number of votes for elected candidates cast by electors in the indirect election. Applies only to Norway (1822-1903) and Sweden (1866-1908). |
| `COUNT2`-`COUNT37` (lower-chamber supplemental: Preferential Vote Counts file) | Preferential Vote Counts | numeric | count per counting stage | Australia, Ireland, Malta (and Estonia 1992, Nauru): votes counted by order of preference. `CV1` = first-preference votes. When a candidate reaches quota with seats remaining, surplus votes transfer per preferences; at each stage the lowest candidate is eliminated and votes transferred based on preferences. |
| `PLUS`/`MINUS` (lower-chamber supplemental: Latvia Ordinal Ballot Vote Counts file) | Positive/Negative Candidate Votes | numeric | count | Latvia: voters select a party list and may mark candidates with positive (+) or negative (-) preference votes. `CV1` = party-list votes plus/minus candidate-specific votes. `PLUS` = positive votes received; `MINUS` = negative votes received. |
| `MA_CST_N` (lower-chamber supplemental: Lebanon Confessional Quota file) | Major Constituency Name | string | — | Lebanon 2018: 7 of the 15 "major" constituencies are divided into ≥2 "minor" constituencies for confessional-quota preference votes. |
| `MA_CST` (lower-chamber supplemental: Lebanon Confessional Quota file) | Major Constituency Code | numeric | sorted alphabetically by name, then coded | — |
| `MI_CST_N` (lower-chamber supplemental: Lebanon Confessional Quota file) | Minor Constituency Name | string | — | See `MA_CST_N`. |
| `MI_CST` (lower-chamber supplemental: Lebanon Confessional Quota file) | Minor Constituency Code | numeric | sorted alphabetically by name within each major constituency, then coded | — |
| `RLG` (lower-chamber supplemental: Lebanon Confessional Quota file) | Religious Community | categorical | — | Confessional affiliation of each candidate; values not enumerated in the codebook body (see supplemental file). |

## Notes and gotchas

- **Two chamber files, one schema.** Lower- and upper-chamber data are separate files (`clea_lc*` / `clea_uc*`) but share the exact same variable list and descriptions — merging/joining logic can be identical across chambers.
- **Party codes are stable identifiers, not labels.** The same `PTY_N` string in two different countries gets different `PTY` codes (e.g. "Democratic Party" in Albania ≠ Australia) — never join on `PTY_N` across countries. Within a country, a party keeps one `PTY` code across elections and across chambers/presidential races, EXCEPT the "other"/"independent" residual codes (4000+/6000+), which are reassigned fresh each election and do NOT identify the same minor party or independent across elections.
- **Blank-vote handling under `IVV1` depends entirely on how the electoral commission itself classified blank votes** — the codebook gives an explicit decision tree: if blanks are reported separately AND treated as valid by the commission, CLEA adds a separate row with `PTY=4999` and folds blanks into `VV1`; `IVV1` = the commission's own invalid total. If blanks are reported separately but the commission does NOT count them as valid, CLEA does not add a separate row — instead `IVV1` = commission's invalid total (if that total already includes blanks) or invalid+blank summed by CLEA (if it doesn't). This is a common source of vote-total mismatches when cross-checking against a country's own official report.
- **Turnout (`TO1`/`TO2`) is NOT the officially reported rate.** It's CLEA's own `VOT/PEV` division and can validly exceed 1 when official sources report more votes cast than eligible voters.
- **Multi-vote systems can push `VV1` above `VOT1` or even above `PEV1`** — expected behavior when voters cast more than one vote, not a data error.
- **`PV1`/`PVS1`/`PV2`/`PVS2` are repeated per candidate row.** When more than one candidate from the same party contests a constituency, the party-level vote figure is duplicated on every one of that party's candidate rows — summing these columns naively across all rows in a constituency will double-count and can push the constituency total (and `PVS` sum) above 1. Always deduplicate by party before aggregating.
- **`CST` numbering convention for multi-tier/mixed systems**: codes 001-900 are the geographic/majoritarian/lower PR tier; 901-999 is reserved for the PR tier, upper tier(s), non-geographic (ethnic/religious/identity/class-based) constituencies, or additional macro-unit representatives overlapping the 001-900 range (example given: Uganda).
- **`CST` codes are not guaranteed stable across elections** — they depend on alphabetical sort of constituency names within each election, so redistricting or renaming can shift a constituency's code between elections. Special/minority districts and semi-autonomous regions (pre-1996 NZ Maori seats; Greenland in Danish elections) are appended after the last alphabetical geographic code, not sorted alphabetically themselves.
- **India independent candidates**: some elections have 4,000+ independent candidates, forcing 5-digit `PTY` codes — a schema edge case for any fixed-width parsing assumption.
- **Country/candidate-name encoding**: Japan, Taiwan, Thailand, and Ukraine store `CAN` as a numeric code rather than a name string; original-language candidate name lists for Japan and Taiwan are published separately on the CLEA website, not in this file.
- **Non-UN country codes**: Taiwan (1001), Kosovo (1002), Somaliland (1003) use CLEA-assigned codes outside the UN M49 standard because they lack official UN country codes — any crosswalk keyed purely on UN M49 will fail to match these three.
- **`ID = -999`** is reserved specifically for U.S. House elections before 1880, because there was no federal law standardizing timing and scheduling varied by state.
- **Supplemental files are lower-chamber only** and apply to a short, explicit list of countries/periods: Indirect Elections (Norway 1822-1903, Sweden 1866-1908), Preferential Vote Counts (Australia, Estonia 1992, Ireland, Malta, Nauru), Latvia Ordinal Ballot Vote Counts, and Lebanon Confessional Quota Preference Vote Counts (2018 election only, 7 of 15 major constituencies split into minor constituencies). No upper-chamber equivalents are documented.
- **`RLG` (Religious Community, Lebanon supplemental)**: the codebook text does not enumerate the actual category values/codes for this variable — left as `—` in the table above per the transcription rule; consult the supplemental file itself if the coded categories are needed.
- **Appendices I (Country Descriptions) and II (Party Codes) are NOT included in this PDF** — the codebook body states "(SEE SEPARATE FILES)" and provides no content for them here. This condensed file cannot reproduce full country descriptions or the full party-code list; go to the separate appendix files distributed alongside the codebook.

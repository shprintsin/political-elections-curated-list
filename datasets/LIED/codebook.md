---
name: "Lexical Index of Electoral Democracy"
id: "lied"
version: "6.8"
date: null
description: "Ordinal index of electoral democracy built from binary suffrage, election and competitiveness indicators."
scope: "Independent countries plus most semi-sovereign polities, colonies and protectorates."
years: "1789-2020"
type: "quality"
data_url: "https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/WPKNIT"
codebook_url: "lied_6.8_description.pdf"
paper_title: "Skaaning, Svend-Erik, John Gerring and Henrikas Bartusevicius. 2015. \"A Lexical Index of Electoral Democracy.\" Comparative Political Studies 48(12): 1491-1525."
paper_url: null
citation: "Skaaning, Svend-Erik, John Gerring and Henrikas Bartusevicius. 2015. \"A Lexical Index of Electoral Democracy.\" Comparative Political Studies 48(12): 1491-1525."
---

# LIED — codebook (version 6.8)

Condensed from the official dataset description for search and reference. Authoritative
source: [`lied_6.8_description.pdf`](lied_6.8_description.pdf).

## At a glance
- **Unit of observation:** country-year.
- **Coverage:** all independent countries and most semi-sovereign polities and overseas colonies/protectorates, 1789–2020; scores also assigned to units under short-term foreign occupation.
- **Timing convention:** each indicator reflects the status of a country on the last day of the calendar year (31 December) — not the mean value across the preceding 364 days.
- **Key identifiers:** `Countryn` (polity name), `Cow` (Correlates of War country ID — some codes invented by LIED authors for countries not covered by COW), `Vdem` (Varieties of Democracy country ID).
- **Content:** 14 original indicators (per the description text) and two original composite indices (`lexical_index`, `lexical_index_plus`). Coding decisions are based on country-specific sources. All original coding done by Svend-Erik Skaaning (skaaning@ps.au.dk); Henrikas Bartusevicius was in charge of coding linked to an inter-coder reliability test described in the dataset paper.
- **Citation for theoretical background/motivation:** Skaaning, Svend-Erik; John Gerring & Henrikas Bartusevicius (2015). "A Lexical Index of Electoral Democracy." *Comparative Political Studies*, Vol. 48, No. 12, pp. 1491–1525.
- **Version note:** minor revisions of scores are sometimes made from version to version based on new information — users are advised to always use the newest version.

## The lexical index
`Lexical_index` operationalizes electoral democracy as a series of necessary-and-sufficient conditions arrayed in an ordinal scale (0 to 6), built from six binary variables (`legislative_elections`, `executive_elections`, `multi_party_legislative_elections`, `competitive_elections`, `male_suffrage`, `female_suffrage`). Each level identifies a unique and theoretically meaningful regime type (classificatory function) as well as a discriminating function. Criteria, in order:

- **0** — `legislative_elections=0` & `executive_elections=0`. Regime type: **non-electoral autocracies**.
- **1** — `legislative_elections=1` or `executive_elections=1` & `multi_party_legislative_elections=0`. Regime type: **one-party autocracies** (few cases where executive elections are on track but there is no functioning elected parliament).
- **2** — `legislative_elections=1` & `multi_party_legislative_elections=1` & `executive_elections=0`. Regime type: **multiparty autocracies without elected executive** (generally because a monarch influences government appointment/removal, or foreign powers dominate political decision-making or hold significant veto powers).
- **3** — `legislative_elections=1` & `multi_party_legislative_elections=1` & `executive_elections=1` & `competitive_elections=0`. Regime type: **multiparty autocracies**.
- **4** — `legislative_elections=1` & `multi_party_legislative_elections=1` & `executive_elections=1` & `competitive_elections=1` & `male_suffrage=0`. Regime type: **exclusive democracies**.
- **5** — `legislative_elections=1` & `multi_party_legislative_elections=1` & `executive_elections=1` & `competitive_elections=1` & `male_suffrage=1` & `female_suffrage=0`. Regime type: **male democracies**.
- **6** — `legislative_elections=1` & `multi_party_legislative_elections=1` & `executive_elections=1` & `competitive_elections=1` & `male_suffrage=1` & `female_suffrage=1`. Regime type: **electoral democracies**.

`Lexical_index_plus` (LIED+) adds an extra layer at the upper end of LIED in the form of `political_liberties`, to distinguish electoral democracies from polyarchies. Levels 0–5 are identical in meaning to LIED; levels 6 and 7 are:

- **6** — same as LIED level 6 conditions (`legislative_elections=1` & `multi_party_legislative_elections=1` & `executive_elections=1` & `competitive_elections=1` & `male_suffrage=1` & `female_suffrage=1`) & `political_liberties=0`. Regime type: **electoral democracies**.
- **7** — same as above & `political_liberties=1`. Regime type: **polyarchies**.

## Variables
| Variable | Label | Type | Values / units | Notes |
|---|---|---|---|---|
| `Countryn` | Country name | string | — | Name of the polity. |
| `Cow` | Correlates of War country ID | numeric/code | COW codes | Additional codes invented by LIED authors for countries not covered by the COW project. |
| `Vdem` | V-Dem country ID | numeric/code | V-Dem codes | Varieties of Democracy country identifier. |
| `Male_suffrage` | Universal male suffrage | binary | 1=present, 0=absent | Indicates whether virtually all male citizens are allowed to vote in national elections. Legal restrictions on age, criminal conviction, incompetence, and local residency are NOT considered. Informal restrictions (e.g., American South prior to 1965) are also not considered. |
| `Female_suffrage` | Universal female suffrage | binary | 1=present, 0=absent | Indicates whether virtually all female citizens are allowed to vote in national elections. Similar coding rules to male_suffrage apply. |
| `Executive_elections` | Chief executive (in)directly elected | binary | 1=present, 0=absent | Indicates whether the chief executive is either directly or indirectly elected (chosen by people who have been elected). Accounts for whether executive power is responsible to an elected parliament if the executive is not directly elected (relevant for some historical/contemporary monarchies and principalities). Episodes of international supervision/domination following intervention, occupation, or colonization (i.e., polity does not exercise self-government) are also disqualifying. |
| `Legislative_elections` | Legislative elections on track | binary | 1=present, 0=absent | Indicates whether a legislative body/parliament issues at least some laws and does not perform executive functions. The lower house (or unicameral chamber) is at least partly elected. The legislature has not been closed. |
| `Multi_party_legislative_elections` | Multi-party legislative elections | binary | 1=present, 0=absent | Indicates whether the lower house (or unicameral chamber) is at least in part elected by voters facing more than one choice. Specifically, parties are not banned and (a) more than one party, including opposition parties, are allowed to compete, or (b) candidates run without party labels but represent distinct political positions. |
| `Competitive_elections` | Genuinely contested elections | binary | 1=present, 0=absent | Chief executive offices and legislative seats are filled by elections characterized by uncertainty — sufficiently free, in principle, to enable the opposition to gain power with sufficient support. Presumes: control over key executive/legislative offices is determined by elections; executive and legislature members have not been unconstitutionally removed; legislature not dissolved. On process: constitutional timing of elections not violated (more than marginally), non-extremist parties not banned, opposition candidates generally free to participate, little systematic voter coercion, electoral fraud does not determine who wins. On outcome: declared winner reflects votes cast, as near as can be determined from extant sources. Incumbent turnover (as a result of multi-party elections) is a strong indicator of competition but neither necessary nor sufficient. Coding also relies on outside-observer reports (books, articles, country reports). Does NOT take into account level playing field, equal access to funding/media, unbiased media coverage, civil liberties, or other features associated with fully free-and-fair elections. |
| `Political_liberties` | Freedom of expression/assembly/association | binary | 1=present, 0=absent | Freedom of expression, freedom of assembly, and freedom of association are respected. All groups that are not openly anti-democratic are allowed to organize freely and assemble peacefully; free speech (including critique of government/state authorities) is tolerated and practiced freely by individuals and groups, including private and public media outlets. |
| `Lexical_index` | Lexical Index of Electoral Democracy | ordinal | 0–6 | Built from the six binary variables above; see "The lexical index" section for exact level criteria. |
| `Lexical_index_plus` | Lexical Index of Electoral Democracy+ (LIED+) | ordinal | 0–7 | Adds `political_liberties` as an extra layer at the top of LIED to distinguish electoral democracies (6) from polyarchies (7); levels 0–5 identical to LIED. |
| `Democratic_transition` | Democratic transition occurred | binary | 1=present, 0=absent | Indicates whether a democratic transition took place in a given year, signified by a change in `competitive_elections` from 0 in the previous year to 1 in the current year. |
| `Transition_type` | Mode of democratic transition | categorical | 1=conversion (incumbent-led); 2=cooperative (pact between incumbents and opposition/balanced influence); 3=collapse (opposition-led); 4=foreign supervision (imposition by foreign power based on intervention or highly asymmetrical partial/full decolonization); 5=foreign liberalization (democracy reemerges after occupational power has lost war to foreign powers) | Coded for all country-years with democratic transitions. Country-years without democratic transitions are scored 0. |
| `Democratic_breakdown` | Democratic breakdown occurred | binary | 1=present, 0=absent | Indicates whether a democratic breakdown took place in a given year, signified by a change in `competitive_elections` from 1 in the previous year to 0 in the current year. |
| `Breakdown_type` | Mode of democratic breakdown | categorical | 1=implicit regression induced by incumbents; 2=military coup; 3=foreign occupation; 4=self-coup (incumbents close down parliament unduly and take full political control); 5=coup or civil conflict headed by opposition party/movement; 6=coup headed by monarch | Coded for all country-years with democratic transitions [as stated in source — see Notes]. Country-years without democratic breakdowns are scored 0. |
| `Turnover_event` | Government turnover via multi-party election | binary | 1=present, 0=absent | Indicates whether partisan control over government power alternated from an elected chief executive to another party/coalition/candidate representing the opposition, as a consequence of a multi-party election in a particular country-year. Multi-party legislative and (direct or indirect) executive elections are necessary conditions for a genuine turnover. |
| `Turnover_period` | Period following a first turnover | binary | 1=present, 0=absent | Indicates whether a particular country-year is part of a period between an initial electoral government alternation (a turnover event) in a multi-party electoral regime and an interruption of that same regime (indicated by a score of 0 on `executive_elections` or `multi_party_legislative_elections`). If another turnover event happens later in the same polity, a new turnover period begins. |
| `Two_turnover_period` | Period following a second turnover | binary | 1=present, 0=absent | Indicates whether a particular country-year is part of a period between a second electoral government alternation (a turnover event) in a multi-party electoral regime and an interruption of that same regime (indicated by a score of 0 on `executive_elections` or `multi_party_legislative_elections`). If two more turnover events happen later in the same polity under a new multi-party electoral regime, a new two-turnover period begins. |
| `Sovereign` | Sovereign polity status | binary | 1=separate unit in the international system of states, 0=subjected to foreign colonization or occupation with formal loss of autonomy | — |

## Notes and gotchas
- Indicators are inspired by similar variables developed by Adam Przeworski et al. for the Political Institutions and Events (PIPE) dataset (i.e., LEGSELEC, EXSELEC, OPPOSITION, MALE SUFFRAGE, FEMALE SUFFRAGE dataset), per a footnote in the source.
- `Male_suffrage`/`Female_suffrage`: only formal/legal universality of suffrage among the respective sex matters. Legal restrictions on age, criminal conviction, incompetence, and local residency are explicitly excluded from consideration, as are informal restrictions (the source's own example: the American South prior to 1965).
- `Legislative_elections` and `Multi_party_legislative_elections` are both scoped to the lower house (or unicameral chamber) only — upper-house electoral status is not part of these definitions per the source text.
- `Competitive_elections` explicitly does NOT factor in level playing field, equal funding/media access, unbiased media coverage, or civil liberties — those are captured separately (if at all) via `political_liberties`, not folded into competitiveness.
- `Lexical_index` and `Lexical_index_plus` are indices built strictly from the binary indicators via the necessary-and-sufficient condition ladder in "The lexical index" section above — do not treat them as freely coded variables.
- `Lexical_index_plus` levels 0–5 are identical in definition/meaning to `Lexical_index` levels 0–5; only 6 and 7 differ, splitting LIED's level-6 "electoral democracies" into "electoral democracies" (political_liberties=0) and "polyarchies" (political_liberties=1).
- `Democratic_transition` is mechanically defined as `competitive_elections` flipping 0→1 year over year; `Democratic_breakdown` is the mirror flip 1→0.
- The source text describes `Breakdown_type` as coded "for all country-years with democratic transitions" — this appears to be a copy-paste artifact in the original PDF (breakdown_type logically pairs with democratic_breakdown, not democratic_transition); transcribed as written since the source is silent on any correction.
- `Turnover_event` requires BOTH multi-party legislative elections AND (direct or indirect) executive elections as necessary conditions for a genuine turnover — a turnover cannot be coded from a legislative-only or executive-only multi-party election.
- `Turnover_period` and `Two_turnover_period` are sequential/cumulative: a `turnover_period` starts at a first turnover event and ends when `executive_elections` or `multi_party_legislative_elections` drops to 0; if a new turnover event follows later in the same polity, a new turnover period begins (potentially repeatedly). `Two_turnover_period` is the analogous window keyed to the second turnover event, and likewise can restart under a new multi-party electoral regime.
- The dataset's variable-count claim ("14 original indicators and original two indices") in the introductory paragraph does not exactly match the count of indicators explicitly defined with their own subsection later in the PDF (15 non-index indicators were found with individual definitions: male_suffrage, female_suffrage, executive_elections, legislative_elections, multi_party_legislative_elections, competitive_elections, political_liberties, democratic_transition, transition_type, democratic_breakdown, breakdown_type, turnover_period, turnover_event, two_turnover_period, sovereign). This is transcribed as-is from the source without reconciling the discrepancy.
- Scores reflect country status as of 31 December of the year, not an average/mode over the year — relevant when merging by year against data sourced with a different within-year reference point.
- Users are explicitly advised to always use the newest LIED version, since minor score revisions occur across versions based on new information.
- Page 5 of the source PDF contains only the closing sentence of the citation/versioning note (see above) and is otherwise blank.

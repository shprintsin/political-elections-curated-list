# DPI — codebook (DPI2023, partial)

Condensed from the official codebook for search and reference. Authoritative source:
[`dpi2023_codebook.pdf`](dpi2023_codebook.pdf).

> **This codebook is incomplete.** The published PDF runs to 8 pages and stops at
> `EXECRLC` (Chief Executive party orientation), including its extended coding notes and
> an Inglehart-Huber cross-check table (cut off after the first two rows on page 8).
> Legislative and electoral variables (HOUSESYS, PLURALTY, THRESH, seat shares,
> fractionalisation indices, etc.) are not documented here — see the full DPI2020
> *Changes and Variable Definitions* (IDB-DT-56).

## At a glance

- **Unit of observation:** country-year (chief-executive-year, as of January 1).
- **Coverage:** DPI2023 extends DPI2020 through 2023, adding data for 2021 and 2022.
- **Reference date:** all data refer to January 1 of each year.
- **Upstream sources (as listed in the PDF):** Europa World Online (Routledge); Political
  Handbook of the World 2010 (Banks, Muller, Overstreet — CQ Press, 2017); Political
  Handbook of the World Online Edition (CQ Press); Parline Database (Inter-Parliamentary
  Union); IFES Election Guide (International Foundation for Electoral Systems).

## Changes from the previous version (DPI2020 → DPI2023)

- Extends the panel through 2023 (adds 2021, 2022).
- Substantial cross-country/cross-variable corrections for consistency and accuracy.
- Continues updating the gender quota variables introduced in DPI2020.
- Key revision areas:
  - **Recoding:** reelection eligibility (`reelect`), party ideology/nationalism
    (`execrlc`, `execnat`, etc.), electoral timing alignment, appointment status of local
    executives.
  - **Missing data:** gaps for underreported countries/years filled via hand-coding and
    external sources, particularly ideological variables and local government indicators.
  - **Cross-verification/documentation:** all coding changes cross-checked against
    national/international sources; added notes on complex cases (caretaker governments,
    indirect elections, mixed systems).
- A full list of recoding decisions, country-level corrections, and source references is
  said to be in an "accompanying update document" — not included in this PDF.

## Missing values and sentinels

| Code | Meaning |
|---|---|
| *(blank cell)* | No information was available (the default for missing data). |
| `NA` | Not applicable (numeric or categorical variable) — see cases below. |
| `-999` | Not applicable, used specifically for **numeric** variables in place of `NA`. |

`NA` is recorded when: the country is a colony (even with internal self-government within
a commonwealth); for Soviet Republics while part of the USSR; for countries in the midst
of civil war or political crisis.

## Variables (as documented in this PDF)

| Variable | Label | Values | Notes |
|---|---|---|---|
| `SYSTEM` | Regime type of the chief executive | Parliamentary (2); Assembly-elected President (1); Presidential (0) | Unelected executives (scoring 2 or 3 on the Executive Index of Political Competitiveness, EIEC — defined elsewhere, not in this PDF) get 0. Directly/electoral-college-elected presidents with no PM also get 0. Where both a PM and a president exist, classify presidential if (a) veto power needing a supermajority override is true, OR (b) AND (c) are both true: (b) president can appoint and dismiss PM/ministers, (c) president can dissolve parliament and call elections. If (a)/(b)/(c) are unknown or ambiguous, fall back to (d): which office sources mention more often (examples: Romania, Kyrgyzstan, Estonia, Yugoslavia). Legislature-elected chief executives are parliamentary (2), except if the executive cannot be easily recalled (needs a 2/3 impeachment vote, or the assembly must dissolve itself to force the executive out) — then it is 1 (assembly-elected president). |
| `YRSOFFC` | Years the chief executive has been in office | integer | Years counted where the executive was in power as of Jan 1, OR was elected but hadn't yet taken office as of Jan 1 (recorded as "1" the year following election). Example: Bush was president Jan 1 1992 → recorded 4 for 1992 (4th year), despite losing the Nov 1992 election; Clinton, elected Nov 1992/took office Jan 1993, is president-elect as of Jan 1 1993 → recorded 1 for 1993. Colony→independence transitions date tenure from independence, not internal self-government (e.g., Timor-Leste 2003); Soviet-era republics track from full independence (exception to that rule). Counts the de jure executive, but the executive must actually be in the country. A coup followed by return to power within the same calendar year counts as a "failed" coup — tenure unbroken. A parliamentary government that resigns and is re-appointed counts as a new government. For Communist states, tracks the Communist Party general secretary regardless of who holds the president/premier title. |
| `FINITTRM` | Is there a finite term in office? | 1 = yes, 0 = no | Based on a constitutional limit on years served before new elections must be called. Deviating from convention: recorded as 0 if no limit is explicitly stated. Also 0 where a constitution with year limits is suspended or unenforced. |
| `YRCURNT` | Years left in current term | integer | Only full years counted: "0" in an election year, and n-1 in the year after an election, where n = length of the term. |
| `MULTPL` | Can the executive serve additional term(s) beyond the current one? | 1 = yes, 0 = no, NA = no formal term limit | Only applies where the term is constitutionally limited (NA if `FINITTRM`=0, i.e. `MULTPL`=NA when `FINITTRM`=0). "Additional" wording added in 2004 for clarity only, no rule change. Deviating from convention: recorded as 1 if a term limit is not explicitly stated. Only limits on *immediate* reelection count. Prime ministers always get "1". |
| `MILITARY` | Is the chief executive a military officer? | 1 = yes, 0 = no | "1" if the source (Europa or Political Handbook/Banks) includes a military rank in the executive's title, "0" otherwise. Executives described as officers with no indication of formal retirement upon taking office are listed as officers for their full term. Formally retired military officers upon taking office get 0. |
| `DEFMIN` | Is the defense minister a military officer? | 1 = yes, 0 = no, NA | Same coding convention as `MILITARY`. "NA" if no one in the cabinet holds that responsibility, or there are no armed forces. If there is no defense minister but the chief executive controls the military directly, `DEFMIN` = same value as `MILITARY`. |
| `PERCENT1` | President's % of votes in the 1st/only round | percentage, NA | NA if `SYSTEM` = 1 or 2, and (for presidential systems) NA in cases scoring a 2 on the EIEC (Executive Index of Electoral Competition — definition not in this PDF). Where a PM is the chief executive but a president with some powers also exists (e.g., France), the president's vote % is still recorded. In non-election years, records the most recent election. A vice president completing a president's term gets the same score as the former president. A president prevented from taking office who later returns without a new election (within the original term's limits) gets the same score as the original election. |
| `PERCENTL` | President's % of votes in the final round | percentage, NA | NA for the same reasons as `PERCENT1`, or if there was no runoff. In non-election years, records the most recent election. |
| `PRTYIN` | How long the chief executive's party has been in office | integer, NA | Same counting rules as `YRSOFFC`. NA if there are no parties, if the chief executive is an independent, or if the "party" is the army. Counting generally restarts from 1 when a party's name changes; exception: where sources indicate leadership, membership, and platform were unchanged across the name change, the count did not restart (such cases noted in the database). |
| `EXECME` | Name of party, if any | text; "Independent" | "Independent" if the chief executive is independent, a monarch, in the military, or if there are no parties. |
| `EXECRLC` | Party orientation (economic policy) | Right (1); Center (2); Left (3); No information (0); NA = no executive | Right: parties described as conservative, Christian democratic, or right-wing. Left: parties described as communist, socialist, social democratic, or left-wing. Center: parties described as centrist, or whose position is best described as centrist (e.g., advocating strengthened private enterprise in a social-liberal context) — but *not* centrist merely because competing internal factions "average out" (e.g., a party of "right-wing Muslims and Beijing-oriented Marxists" is not Center). 0: cases that don't fit the above (platform doesn't focus on economic issues, or there are competing wings), or no information. NA: cases with no executive. In the STATA version the labels are R/L/C with R=1, L=3, C=2. |

### EXECRLC — extended coding notes (pp. 7–8)

1. Where party orientation was not obvious from name/description in the handbooks, the
   coders consulted `agora.stm.it/elections/parties.htm` for one-word orientation
   descriptions. Cross-checks between the two sources showed high agreement. Since Agora
   had no historical information, party position was assumed unchanged over time and
   applied to all years; Agora was used only occasionally before 2006 and not after. Since
   the 2006 update, the Political Handbook has been sufficient on its own.
2. Website terms "liberal", "progressive", "authoritarian", "xenophobic" were handled as
   follows: "liberal" → Right (using the European definition, since the site is
   Europe-based); "progressive", "authoritarian", "xenophobic" → coded 0 (none of the
   above) unless additional information allowed placement on the left-right spectrum.
3. Party orientations were further spot-checked against *Political Parties of Africa and
   the Middle East* and *Political Parties of Eastern Europe and the Successor States*
   (Longman Current Affairs series). Where sources conflicted, coders went with the
   description of the party's economic platform (from any source).
4. Where the executive deviated considerably from the party's stated orientation (e.g., a
   socialist/social-democratic party's executive pursuing austerity), the *executive's*
   orientation is recorded, not the party's. If the executive is independent, the
   executive's own orientation is recorded.
5. Codings were compared against Inglehart and Huber (1995); overlap was high. Where
   codings differed, sources were revisited; in most cases DPI's coding was kept. In some
   cases it was changed — those changes are listed in a table, of which only the first
   two rows are visible before the PDF ends:

| Country | Party | Before DPI2000 | After DPI2000 | Reason for change |
|---|---|---|---|---|
| Brazil | PDS | L | R | PHW indicates the presence of many right-wing members of the former MDB. |
| Brazil | PSDB | R | L | Our sources indicate this is a center-left party. |

*(The table is cut off at the bottom of page 8, the last page of the PDF; further rows, if any, are not captured here.)*

## Notes and gotchas

- **January-1 reference convention:** every DPI variable is a snapshot as of January 1 of
  the given year, not the calendar year as a whole. Executives elected late in a year (as
  in the Clinton example) are not credited with that year until the following January 1.
- **Blank vs. `NA`/`-999`:** blank means no information was available (a genuine data
  gap); `NA` (or `-999` for numeric fields) means the question does not apply to that
  country-year (colony, USSR-era Soviet republic, civil war/political crisis, or a
  variable-specific "not applicable" condition such as no executive for `EXECRLC`). Do not
  treat blank and NA/-999 as interchangeable when filtering or merging.
- **House vs. Senate:** "House" always means the lower house (e.g., House of
  Representatives, House of Commons, Bundestag). "Senate" means the upper house, but only
  where it exists *and* has some defined power (e.g., Senate, House of Lords, Bundesrat) —
  the codebook does not spell out that power threshold within these 8 pages.
- **Upstream sources are secondary compilations**, not primary electoral-authority data:
  Europa World Online, the Political Handbook of the World (print and online), the IPU
  Parline database, and the IFES Election Guide. Treat DPI fields as derived from these
  handbooks/directories, with the coders' own judgment calls layered on top (see the
  `EXECRLC` extended notes above) — not as independently verified primary-source counts.
- Binary variables generally follow "1" = yes, "0" = no, but several fields deviate from
  the naive default when information is silent (`FINITTRM` defaults to 0 if unstated,
  `MULTPL` defaults to 1 if unstated) — read the specific variable's notes rather than
  assuming a uniform missing-value convention.

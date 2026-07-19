---
name: "CCP Chronology of Constitutional Events"
id: "ccpcce"
version: "6"
date: "2026-04-06"
description: "Chronology of constitutional events: new constitutions, amendments, suspensions and reinstatements."
scope: "Constitutional systems and events for all independent countries."
years: "1789-2025"
type: "rules"
data_url: "http://www.comparativeconstitutionsproject.org"
codebook_url: "ccpcce_v6_codebook.pdf"
paper_title: null
paper_url: null
citation: "Elkins, Zachary, Tom Ginsburg, and James Melton. 2026. \"Chronology of Constitutional Events, Version 6.\" Comparative Constitutions Project."
---

# CCP Chronology of Constitutional Events — codebook (v6)

Condensed from the official codebook for search and reference. Authoritative source:
[`ccpcce_v6_codebook.pdf`](ccpcce_v6_codebook.pdf).

## At a glance
- **Unit of observation:** country-year (for characteristics coding); the chronology file records constitutional events, identifying the first chronological event in a year with multiple events (most commonly a 'new' event).
- **Coverage:** All years 1789–2025 for all independent countries; 20,638 country-years as of v6. List of independent countries based on Ward and Gleditsch (2020 [1999]), supplemented by Correlates of War "State System Membership List." As of 2025, every independent state in the world had a constitution in force by the authors' definition (some, e.g. Israel and Saudi Arabia, have unconventional forms). Some countries had a constitution in place at independence; these have system numbers even though the start date precedes the observation window.
- **Key identifiers:** COWCODE (Correlates of War country code), COUNTRY, YEAR, SYSTID (constitutional system ID), EVNTID (constitutional event ID).
- **Data files:** `ccpcce_v6.txt` (tab-delimited), also available as CSV, Stata (.dta), and Excel (.xlsx).
- **Citation:** Elkins, Zachary, Tom Ginsburg, and James Melton. 2026. "Chronology of Constitutional Events, Version 6." Comparative Constitutions Project. Last modified: April 6, 2026 [first edition published 2009]. http://www.comparativeconstitutionsproject.org.

## Event types
The codebook does not provide a single closed taxonomy table of event-type codes; EVNTTYPE values are transcribed here as they appear throughout the document (Sample section + version-history tables).

| Code (EVNTTYPE value) | Meaning |
|---|---|
| new | A new constitution (e.g., "new constitution" events like Algeria 2020, Guinea 2020, Kyrgyz Republic 2021) |
| amendment | A constitutional amendment |
| interim | An interim constitution (e.g., Mali 2020, Burkina Faso 2022, Syria 2025) |
| suspension | Suspension of the constitution (e.g., Chad 2021, Sudan 2019, Syria 2025) |
| reinstated | Reinstatement of a (previously suspended/replaced) constitution |
| non-event | Reclassification bucket for years found NOT to constitute a constitutional event (e.g., Indonesia 1955, Nauru 2015/2018, Switzerland 2007/2008/2016/2018) |

Note: "A constitutional event is any change to a country's constitution, including adoption, amendment, suspension, or reinstatement." (Concepts section, verbatim.) The document also references "All event type classifications standardized to lowercase for consistency" (v5→v6 changelog), implying EVNTTYPE values are stored lowercase in the data file.

## Variables
| Variable | Label | Type | Values / units | Notes |
|---|---|---|---|---|
| `COWCODE` | Correlates of War country code | — | see www.correlatesofwar.org | — |
| `COUNTRY` | Country name | — | — | — |
| `YEAR` | Year | — | 1789–2025 | Refers to the year the constitutional event was promulgated |
| `SYSTID` | Unique identification number for the constitutional system | — | integer | A constitutional system spans the period a constitution is in force, bracketed by year of adoption and year of replacement or suspension |
| `EVNTID` | Unique identification number for the constitutional event | — | integer | — |
| `EVNTTYPE` | Event type | — | e.g. amendment, new (see Event types table above) | — |

Note: this is the full and only variable list given in the "List of Variables" section of the codebook (6 variables total). No additional variables (e.g., interim/provisional flags, suspension dates as separate fields) are documented as distinct columns.

## Notes and gotchas
- **Constitutional system vs. constitutional event.** A *constitutional system* = the period a constitution is in force, bracketed by its adoption year and the year of any replacement or suspension. A *constitutional event* = any change to a country's constitution (adoption, amendment, suspension, reinstatement). One system can contain multiple events (e.g., the US has had 2 systems: 1781-89 and 1789-present; the second has one event per year an amendment was promulgated).
- **Multi-event years.** When coding constitution *characteristics* for a country-year with multiple events, the authors code the content of the constitution as it stood in force at the END of the year (e.g., if amended the same year it was adopted, the amended version is coded). The chronology file itself, however, identifies such years by the event that occurred FIRST chronologically — most commonly a 'new' event. This is a merge trap: don't assume the chronology's EVNTTYPE for a year reflects the constitution's end-of-year state used elsewhere in CCP characteristics data.
- **Country identifiers / cowcode caveats.** COWCODE is the Correlates of War code. Yugoslavia and Serbia share a common COW code and country name "Yugoslavia (Serbia)" as of v3 (reflecting shared history); later renamed "Serbia and Montenegro" (2003–2006) then "Serbia" after Montenegrin independence in 2006 — same underlying code across these name changes. v6 changelog also notes "Corrected Correlates of War country codes where applicable" — codes have been revised across versions, so don't assume cowcode stability across CCP dataset versions without checking version notes.
- **Interim/provisional cases.** EVNTTYPE = "interim" is used for interim/provisional constitutions (examples: Argentina 1966/1976; Czechoslovakia 1918; Mali 2020; Burkina Faso 2022; Syria 2025). Some interim-constitution years were later reclassified (e.g., Sudan 2019 changed from 'interim' to 'suspension' "to reflect the political situation").
- **Non-event reclassifications.** A meaningful share of past "amendment" or "new" codings were later downgraded to "non-event" after further research (e.g., Indonesia 1955 new→non-event; Nauru 2015/2018 amendment→non-event; Switzerland 2007/2008/2016/2018 amendment→non-event) — and the reverse also happens (non-event→amendment, e.g., Israel 2009, Moldova 2013/2018, Senegal 1961, Singapore 2019, Tonga 1977/1982/1984/2006, Turkmenistan 2017, Tuvalu 2018, Uzbekistan 2018/2019, all reclassified "based on improved documentation"). Treat EVNTTYPE as revised/versioned, not fixed truth — check which codebook version a downstream file was built against.
- **System/event ID instability across versions.** SYSTID and EVNTID values have been changed/swapped between versions for specific country-years (e.g., Uganda 1966/1967 systid+evntid swapped in v2; South Africa 1996/1997 evntid swapped in v3; Honduras/Liberia/Mexico/Uruguay evntid corrections in v3; v6 changed systid for Benin 1977–1978, Dominican Republic 1855–1857, Haiti 1947–1948, Tuvalu 2023). **Merge pitfall:** do not treat SYSTID/EVNTID as permanent, order-independent keys across dataset versions — always join/compare within one version, or re-derive from the current release.
- **Country-list churn.** The set of countries covered changes with the underlying Ward & Gleditsch / Correlates of War independent-states list: San Marino was removed (v3, not classified as independent by Ward & Gleditsch 2013); Greece 1827 and Slovenia 1991 observations were deleted (v3) to reflect independence-year changes; Croatia 1991 deleted (v4); Lesotho 2022 and Maldives 2020 deleted (v6, "based on further research"). Kiribati (1980-2019) and Nauru (1969-2013) country-year coverage was completed only in v5.
- **Sample boundary growth.** The sample has been extended year-by-year across versions (through 2013 in v3, 2019 in v4, 2023 in v5, 2025 in v6) — always check which version's year-coverage a downstream extract uses.
- **No system_family/system-boundary variable beyond SYSTID.** The dataset does not include separate start/end-date columns for a system in the variable list — system boundaries must be inferred from the sequence of EVNTID/EVNTTYPE rows sharing a SYSTID within a country.
- **Companion dataset warning.** This "Chronology of Constitutional Events" file is distinct from the CCP's core dataset on the *characteristics* of national constitutions, which is released as a separate file with its own separate documentation — do not conflate variable definitions between the two.

TL;DR:
- 6 variables total (COWCODE, COUNTRY, YEAR, SYSTID, EVNTID, EVNTTYPE); no closed EVNTTYPE code table exists in the codebook — values (new, amendment, interim, suspension, reinstated, non-event) were assembled from prose and version-history examples.
- Biggest gotchas: EVNTTYPE codings get revised across versions (non-event ⇄ amendment ⇄ interim/suspension reclassifications), and SYSTID/EVNTID values have been changed/swapped for specific country-years across releases — never assume ID or event-type stability across CCP versions.

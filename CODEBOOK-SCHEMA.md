# Codebook schema

Every dataset folder carries a `codebook.md` in one fixed shape, so the whole set can be
parsed programmatically: YAML frontmatter for the dataset-level metadata, then a variables
table with one row per variable.

## Frontmatter

All thirteen keys are always present and always in this order. A key whose value the source
does not state is `null` — never omitted, never guessed.

```yaml
---
name: "Constituency-Level Elections Archive"   # full dataset name
id: "clea"                                     # short slug, lowercase, stable
version: "20251015"                            # release as the maintainers label it
date: "2025-10-15"                             # release date, ISO (YYYY, YYYY-MM or YYYY-MM-DD)
description: "One sentence: what the data contains."
scope: "What the dataset covers — units, chambers, level of aggregation."
years: "1789-2025"                             # temporal coverage, "START-END"
type: "results"                                # results | parties | rules | quality | regional
data_url: "https://..."                        # where the data is downloaded
codebook_url: "clea_20251015_codebook.pdf"     # authoritative source doc: local file or URL
paper_title: null                              # reference article, or null if none exists
paper_url: null
citation: "Verbatim from the maintainers."
---
```

`type` values: **results** (votes and seats) · **parties** (party identity, ideology,
positions) · **rules** (electoral systems and institutions) · **quality** (integrity,
conduct, regime context) · **regional** (single-region or official national sources).

## Body

```markdown
# NAME — codebook (version)

Condensed from the official codebook for search and reference. Authoritative source:
[`<file>`](<file>).

## At a glance
- **Unit of observation:** / **Coverage:** / **Key identifiers:**

## Missing values and sentinels
| Code | Meaning |

## Variables
| Variable | Label | Type | Values / units | Notes |

## Notes and gotchas
- Coding rules, edge cases, merge traps.
```

Sections may be added where a dataset needs them (an ordinal scale, a policy-category
table, an event taxonomy). `## Variables` and the frontmatter are the fixed parts.

## Rules

1. **One row per variable, one line per cell.** A grep for a variable name must return
   exactly one line carrying its definition. Wrapped cells break that. Variable names are
   wrapped in backticks (`` `pv1` ``) so a row is recognisable by pattern as well as name.
2. **Transcribe, never invent.** Every name, label and value code appears in the source
   document; `—` marks what the source leaves undefined.
3. **Flag, don't fix.** Where the official codebook contradicts itself, transcribe it as
   printed and note the contradiction — do not silently correct it.
4. **State incompleteness.** If the source is partial, say so at the top of the body.
5. **Source content only.** No commentary about surrounding projects, and no process
   narration.

## Long codebooks

Completeness is the goal only while the source is small enough to transcribe. Past roughly
60 pages or 300 variables, the file becomes a **digest of the main content** rather than a
full transcription:

- Identifiers, sentinels and `Notes and gotchas` stay complete — never abridged.
- The variable families the dataset is used for are transcribed in full and named.
- Templated families collapse to one row for the pattern (`per101`-`per706`,
  `candidate_i` for i = 1..39), with distinct member meanings moved to their own table.
- Long enumerations available in the source (country lists, party-code appendices) become
  a one-line pointer, not a transcription.

A digest **states its own boundary** directly under the title: what is covered in full,
what is summarised, what is omitted, and where to find the rest. Silent truncation is not
acceptable — an unannounced digest reads as a complete codebook and gets trusted as one.

## Parsing

```python
import yaml, pathlib
for p in pathlib.Path("datasets").glob("*/codebook.md"):
    meta = yaml.safe_load(p.read_text(encoding="utf-8").split("---")[1])
    print(meta["id"], meta["version"], meta["type"], meta["years"])
```

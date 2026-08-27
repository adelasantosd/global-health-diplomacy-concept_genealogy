# A relational database of the global health diplomacy literature

**13 linked tables · 42,063 rows · 404 documented variables**

This is the data layer of a systematic review of how global health diplomacy (GHD) is
written about: who is said to act, what they are said to do, which concepts are used to
describe it, and what evidence each claim rests on.

It is not a bibliography with codes attached. The central table records **one attribution
about one actor in one document per row**, with role, action, health issue, diplomatic
arena, partner, power source, objective and outcome coded as separate fields, so a user
can ask which actors are credited with which mechanisms and on what evidentiary basis,
rather than only counting publications.

## Contents

| Table | Rows | Columns | One row is |
|---|---:|---:|---|
| `documents.csv` | 3,395 | 41 | one document |
| `fulltext_inventory.csv` | 2,474 | 37 | one Corpus A document |
| `concepts_definitions.csv` | 253 | 29 | one definition instance as stated in one source |
| `actors.csv` | 381 | 24 | one normalised actor |
| `actor_document_mentions.csv` | 9,816 | 24 | one actor in one document |
| `actor_claims_long.csv` | 14,779 | 41 | one claim about one actor in one document |
| `diplomatic_actions.csv` | 2,876 | 18 | one action code in one document |
| `frames.csv` | 6,018 | 12 | one frame-actor-action co-occurrence in one document |
| `power_mechanisms.csv` | 892 | 15 | one power mechanism attributed to one actor in one sentence |
| `causal_claims.csv` | 635 | 21 | one causal claim in one sentence |
| `middle_power_attributions.csv` | 140 | 40 | one middle-power attribution to one country by one source |
| `middle_power_matrix.csv` | 43 | 49 | one country |
| `funding_power_claims.csv` | 361 | 53 | one funding-power claim in one passage |

Alongside the tables, `reference/` holds the codebook (404 variables with allowed
values and missingness), the entity-resolution log, the screening decisions, the search
log, the referential-integrity report and the reliability audit. `datapackage.json` is a
Frictionless tabular-data-package descriptor with a SHA-256 for every file.

`scripts/` contains the code that produced this release from the internal working copy:
`redact.py` (withholds verbatim source text), `build_metadata.py`, `build_readme.py` (this
file) and `verify_deposit.py`. The last one runs 173 assertions and exits non-zero if
any figure in this README or in `datapackage.json` disagrees with the tables, if a withheld
passage reappears anywhere in a non-bibliographic column, or if a hash fails to reproduce
its source passage. Run it before trusting a modified copy:

```bash
python scripts/verify_deposit.py <internal-working-copy> .
```

## Three corpora, never pooled

Corpus A is scholarly literature (2,474 records). Corpus B is institutional and policy
documents (859 records, WHO IRIS and the UN Digital Library). Corpus C is think-tank
output (62 records). B and C were found through separate repository and web searches, not
through the bibliographic-index flow that produced A, so **they share no sampling frame
and must not be added together**. Every proportion in the review uses a single corpus as
its denominator.

## Verbatim source text is withheld

Each coded passage was individually capped below 25 words. Aggregated per source document,
however, the quotation amounted to substantial republication of third-party text: across
963 documents the coded passages total
166,249 unique words, with up to
1,795 words from a single article and
102 documents above 500 words. A large share of those
sources carry non-open licences.

Publishing that under CC BY would mean granting rights over text that is not ours to
license. So in this release **22,028 passage cells across
12 columns are replaced** by three fields:

- the position of the passage in the source (character offset, sentence id, or a location
  label such as `abstract` or `body @40% of text`),
- its word count,
- the first 16 hex characters of the SHA-256 of the passage after whitespace collapse,
  strip and casefold.

A reader with legitimate access to a source can go to the recorded position, take the
passage, hash it the same way and confirm byte-for-byte that they found the passage we
coded. Verification survives; redistribution does not.

| Table | Column | Cells | Unique words (within column) | Longest | Locators retained |
|---|---|---:|---:|---:|---|
| `actor_claims_long.csv` | `source_statement` | 10,038 | 141,698 | 32 | passage_char_start; passage_location |
| `actor_claims_long.csv` | `supporting_passage` | 10,038 | 119,001 | 24 | passage_char_start; passage_location |
| `causal_claims.csv` | `sentence` | 635 | 22,806 | 104 | sent_id; char_start |
| `power_mechanisms.csv` | `source_sentence` | 892 | 13,339 | 84 | sent_id |
| `funding_power_claims.csv` | `supporting_passage` | 288 | 5,030 | 24 | char_start; passage_id |
| `middle_power_attributions.csv` | `supporting_passage` | 119 | 1,256 | 22 | supporting_passage_location |
| `concepts_definitions.csv` | `definition_text_or_close_paraphrase` | 8 | 148 | 22 | source_location; source_doi_or_id |
| `middle_power_attributions.csv` | `behavioural_criterion` | 4 | 50 | 18 | row identifiers |
| `middle_power_attributions.csv` | `material_positional_criterion` | 2 | 28 | 20 | row identifiers |
| `middle_power_attributions.csv` | `evidence_provided` | 1 | 27 | 27 | row identifiers |
| `middle_power_attributions.csv` | `identity_self_identification_criterion` | 2 | 23 | 12 | row identifiers |
| `middle_power_attributions.csv` | `exact_terminology_used` | 1 | 8 | 8 | row identifiers |

**Do not sum that last column.** Each figure is deduplicated within its own column, but the
columns overlap: in `actor_claims_long.csv`, `source_statement` contains
`supporting_passage` for the same claim. Adding them gives
303,414 words and double-counts that containment; counting
every row separately gives 579,896 and double-counts passages that recur
across claim rows. The figure to quote is **166,249 unique
words**, computed by pooling every redacted column, deduplicating exact repeats, and
dropping any passage that is a substring of a longer passage from the same source document.
All four totals, and which one to use, are in `REDACTION_TOTALS.json`.

`REDACTION_LOG.csv` records this per column, including which cells were left as paraphrase.
`REDACTION_EXPOSURE_BY_DOCUMENT.csv` gives the per-source-document exposure that motivated
the decision. Three points of detail, because they are the kind of thing that is easy to get
wrong and hard to spot:

1. In `concepts_definitions.csv` only the 8
   rows flagged `is_verbatim_quote` are redacted. The remaining
   245
   rows are our own paraphrase of a definition and are published in full.
2. A residual sweep redacts any other cell that exactly duplicates a withheld passage, so
   the deposit never withholds a string in one column while publishing it in another.
3. Bibliographic metadata (title, authors, keywords, venue) stays even where a passage was
   coded from the title, because a title is citation-essential and remains a title.

**The unredacted coding file can be shared with researchers for verification of the
coding.** Contact the author through the Zenodo record.

## Limits that bind reuse

**Coding tiers are uneven, and the skew is measured rather than assumed.** Of the 2,474
Corpus A records, 339 are full-text deep-coded
(13.7%), 1,375 are
abstract-only and 760 are metadata-only. The dominant
driver is document type, not author region. Sentence-level tables
(`power_mechanisms.csv`, `causal_claims.csv`) exist for deep-tier documents only.

**Coding method is recorded per row and is mostly deterministic.** In
`actor_claims_long.csv`, 14,764 rows carry
`rule_based_v1` and 15 carry LLM-assisted coding.
Anyone treating the claim table as human-coded content analysis would be wrong; the
`coding_method` column exists so that assumption cannot be made silently.

**Reliability is reported, including where it is weak.** Sampled passages are 100%
verbatim-verified in the source text (300 sampled) and
mention strings resolve at 98.3% strict
(100.0% after whitespace normalisation).
Role intercoder agreement is 76.0% on
200 sampled claims, which is moderate; role
assignments should be treated as indicative rather than settled.

**The field's own terminology is looser than it looks.** Of 2,876 coded diplomatic
actions, 928 (32.3%) are explicitly called diplomacy by their own
source, and 1,383 (48.1%) are diplomacy by analytical inference
only. That distinction is a column, not a footnote.

**Negative findings are in the data.** `middle_power_matrix.csv` covers 43 countries
and deliberately includes those checked against the literature and never labelled a middle
power. Absence of a label is evidence about the literature, not missing data.

**Databases that were never searched.** Web of Science, Scopus, JSTOR, ProQuest, PAIS
International, HeinOnline and Google Scholar were all licence-gated and unreachable from
the analysis environment. Recall of non-indexed, non-English and grey literature is
unquantified, and every coverage claim is bounded by that.

**No full text was obtained for any non-English work.** Characterisations of the Lusophone,
Hispanophone, Francophone, Germanophone and Sinophone literatures rest on titles,
abstracts, authors and venues.

**One unresolved discrepancy, left visible.** The full-text denominator is reported as 425
in one review output and 426 in another. The reconciliation was not completed. It is
recorded here rather than silently harmonised.

## Suggested uses

The claim table supports actor-level questions that publication counts cannot answer:
which actors are credited with which power mechanisms, how often a claim is supported by
source-explicit evidence versus analytical inference, and how the actor set changes across
health issues and diplomatic arenas. `concepts_definitions.csv` supports concept work,
since each definition carries its unit of analysis, which is what makes definitions
comparable at all.

Anyone recomputing published figures should start from `reference/product14_research_codebook.csv`
for the denominators and read the limits above first.

## Citation

Cite the Zenodo DOI of this record. Attribution must preserve the limits stated in this
README; they are what make the database usable rather than decorative.

## Licence

Data and documentation: Creative Commons Attribution 4.0 International (CC BY 4.0).
Bibliographic metadata for the underlying sources is factual reference information; the
sources themselves remain under their own publishers' terms and are not redistributed here.

# Global Health Diplomacy: The Genealogy of a Concept

An interactive visual essay tracing the terminology, conceptual branches, parallel traditions, and disputes associated with global health diplomacy (GHD) in the literature.

**Visual essay:** https://globalhealthdiplomacy.visualargument.org/

## About

This project reconstructs the genealogy of global health diplomacy from a systematic review of the literature. It follows the appearance and development of medical diplomacy, health as a bridge for peace, health and foreign policy, health security and trade, the consolidation of "global health diplomacy" as a term, related linguistic and intellectual traditions, vocabularies of power and state roles, and conceptual disputes within the field.

The visualization places these developments in a common temporal and relational structure. The scroll-driven network focuses on different parts of the genealogy while retaining their connections to the larger graph.

## Data behind the genealogy

The visual essay draws on a relational database of the global health diplomacy literature developed through the systematic review.

The current data release contains:

- **13 linked tables**
- **42,063 rows**
- **404 documented variables**
- **3 separately constructed corpora**

The genealogy uses primarily the concept and definition records in the database. Other tables contain data on actors, diplomatic actions, frames, power mechanisms, causal claims, middle-power attributions, and funding-power claims.

The research data and accompanying documentation are archived on Zenodo. The deposit includes the codebook, screening decisions, search documentation, entity-resolution materials, reliability audit, and reproducibility files.

### Dataset

**Santos, Adela. (2026). _The Genealogy of Global Health Diplomacy: Terminological Descent, Conceptual Branching, and Contestation_ (Version V1.0) [Dataset]. Zenodo.**

**DOI:** https://doi.org/10.5281/zenodo.22127805

The Zenodo release contains 13 relational tables:

| Table | Rows | One row represents |
|---|---:|---|
| `documents.csv` | 3,395 | one document |
| `fulltext_inventory.csv` | 2,474 | one Corpus A document |
| `concepts_definitions.csv` | 253 | one definition instance as stated in one source |
| `actors.csv` | 381 | one normalised actor |
| `actor_document_mentions.csv` | 9,816 | one actor in one document |
| `actor_claims_long.csv` | 14,779 | one claim about one actor in one document |
| `diplomatic_actions.csv` | 2,876 | one action code in one document |
| `frames.csv` | 6,018 | one frame-actor-action co-occurrence in one document |
| `power_mechanisms.csv` | 892 | one power mechanism attributed to one actor in one sentence |
| `causal_claims.csv` | 635 | one causal claim in one sentence |
| `middle_power_attributions.csv` | 140 | one middle-power attribution to one country by one source |
| `middle_power_matrix.csv` | 43 | one country |
| `funding_power_claims.csv` | 361 | one funding-power claim in one passage |

The corpora were assembled separately and have different sampling frames:

- **Corpus A:** scholarly literature — 2,474 records
- **Corpus B:** institutional and policy documents — 859 records
- **Corpus C:** think-tank output — 62 records

Proportions are calculated within individual corpora. The three corpora are not pooled to produce a common denominator.

Full documentation of the coding, denominators, search coverage, coding tiers, reliability assessment, and reuse limitations is included in the Zenodo deposit.

## Reproducibility and source text

The public release withholds verbatim passages when redistribution would reproduce substantial amounts of third-party copyrighted text. For these passages, the dataset retains source locators, word counts, and cryptographic hashes. Researchers with legitimate access to the original publication can use this information to locate and verify the coded passage.

Analytical paraphrases and bibliographic metadata remain in the public files.

The unredacted coding file can be shared with researchers for verification of the coding. Requests can be made through the contact information associated with the Zenodo record.

## How to read the genealogy

Dates indicate the **earliest located anchor source in the reviewed material** for each concept, term, tradition, or dispute. An anchor year does not establish the first use or historical origin of a term unless the cited evidence supports that conclusion.

Edges record relationships identified through the reviewed literature and the coding process.

Historical events are included as contextual information. Their presence on the timeline indicates the political or institutional setting in which the literature developed. Temporal proximity to a concept or publication does not establish a causal relationship.

The resulting genealogy reflects the literature located through the review and the relationships documented in the underlying data.

## Limits and considerations

The review did not search Web of Science, Scopus, JSTOR, ProQuest, PAIS International, HeinOnline, or Google Scholar because these databases were inaccessible from the analysis environment. Coverage of non-indexed literature, grey literature, and literature outside the searched sources is therefore unknown.

No full text was obtained for non-English works. The Lusophone, Hispanophone, Francophone, Germanophone, and Sinophone branches are characterised from the bibliographic information, titles, abstracts, authors, and venues available for those records.

Coding depth varies within Corpus A. Of its 2,474 records, 339 were full-text deep-coded, 1,375 were coded from abstracts, and 760 from metadata. Sentence-level tables apply to documents for which the required level of text was available and coded.

The dataset documentation reports the remaining methodological limitations and reliability results.

## Corrections and contributions

Corrections, additional literature, and proposed conceptual relationships are welcome. References are especially useful when proposing a new node, connection, date, or correction to an existing claim.

Suggestions can be submitted through the project repository or by contacting the author.

## Citation

### Visual essay

Santos, Adela. (2026). _Global Health Diplomacy: The Genealogy of a Concept_. Visual Argument. https://globalhealthdiplomacy.visualargument.org/

### Dataset

Santos, Adela. (2026). _The Genealogy of Global Health Diplomacy: Terminological Descent, Conceptual Branching, and Contestation_ (Version V1.0) [Dataset]. Zenodo. https://doi.org/10.5281/zenodo.22127805

## Author

**Adela Santos**

Postdoctoral Visiting Fellow  
Global Health Centre  
Geneva Graduate Institute

Swiss Government Excellence Scholarship holder

Contact: adela.santos@graduateinstitute.ch

## Licence

Data and documentation in the Zenodo deposit are released under the **Creative Commons Attribution 4.0 International (CC BY 4.0)** licence.

The publications and source materials referenced in the database remain subject to their respective copyright and licensing terms.

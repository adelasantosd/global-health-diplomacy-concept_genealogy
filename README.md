# Global Health Diplomacy: The Genealogy of a Concept

An interactive visual essay tracing the terminological descent, conceptual branching, parallel traditions, and disputes that have shaped the literature on global health diplomacy (GHD).

**Visual essay:** https://globalhealthdiplomacy.visualargument.org/

## About

How did health become a language of diplomacy, and what happened when different actors began to contest what it meant to do diplomacy through health?

This project reconstructs a genealogy of global health diplomacy from the located and coded literature. Rather than assuming a single origin or a linear development of the concept, the genealogy traces several partially connected histories: medical diplomacy, health as a bridge for peace, health and foreign policy, health security and trade, the consolidation of "global health diplomacy" as a term, parallel linguistic and intellectual traditions, later vocabularies of power and state roles, and areas of conceptual contestation.

The interactive essay uses a scroll-driven network to move through these relationships while preserving the temporal and relational structure of the genealogy.

## Data behind the genealogy

The visual essay draws on a relational database of the global health diplomacy literature developed through a systematic review.

The current data release contains:

- **13 linked tables**
- **42,063 rows**
- **404 documented variables**
- **3 separately constructed corpora**

The genealogy visualized in the essay is built primarily from the concept and definition layer of this larger database. The complete database extends beyond conceptual genealogy to actors, diplomatic actions, frames, power mechanisms, causal claims, middle-power attributions, and funding-power claims.

The underlying research data, codebook, screening decisions, search documentation, entity-resolution materials, reliability audit, and reproducibility files are archived on Zenodo.

### Dataset

**Adela Santos. (2026). _The Genealogy of Global Health Diplomacy: Terminological Descent, Conceptual Branching, and Contestation_ (Version V1.0) [Dataset]. Zenodo.**

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

The three corpora have separate sampling frames and are not pooled for proportions:

- **Corpus A:** scholarly literature — 2,474 records
- **Corpus B:** institutional and policy documents — 859 records
- **Corpus C:** think-tank output — 62 records

See the Zenodo deposit for the complete data documentation, codebook, denominators, coding tiers, reliability results, search coverage, and reuse limitations.

## Reproducibility and source text

The public dataset does not redistribute substantial amounts of third-party copyrighted source text.

Verbatim source passages that could not appropriately be redistributed are withheld while retaining source locators, word counts, and cryptographic hashes that allow researchers with legitimate access to the original source to verify the coded passage.

Paraphrased analytical coding is retained. Bibliographic metadata remains available for source identification.

An unredacted coding file may be made available to researchers for verification of the coding. Contact the author through the Zenodo record.

## How to read the genealogy

Dates in the visualization represent the **earliest located anchor source in the reviewed material** for a concept, term, tradition, or dispute. They should not be interpreted as claims of first use, invention, or historical origin unless explicitly supported by the cited source.

Edges represent relationships documented or analytically coded from the reviewed literature. Historical events provide context for the intellectual and policy environment in which particular vocabularies appeared; temporal proximity alone is not treated as evidence of causation.

The genealogy is therefore a reconstruction from the located literature, not a claim to a complete or definitive intellectual history of global health diplomacy.

## Limits and considerations

Coverage is bounded by the databases and sources accessible during the review. Web of Science, Scopus, JSTOR, ProQuest, PAIS International, HeinOnline, and Google Scholar were not searched because they were inaccessible from the analysis environment.

Recall of non-indexed, non-English, and grey literature is therefore unquantified.

No full text was obtained for non-English works. Characterisations of Lusophone, Hispanophone, Francophone, Germanophone, and Sinophone literatures rely on available titles, abstracts, authors, venues, and other accessible metadata.

Coding depth also varies across the scholarly corpus. Of 2,474 Corpus A records, 339 were full-text deep-coded, 1,375 were abstract-only, and 760 were metadata-only. Sentence-level analyses therefore apply only to the relevant coding tier.

For the complete limitations and reliability documentation, consult the archived dataset.

## Corrections and contributions

This genealogy is intended to remain open to revision as additional literature and conceptual relationships are identified.

Corrections, missing literature, alternative conceptual connections, and suggestions for improving the genealogy are welcome.

When suggesting an addition, please provide the bibliographic reference or source whenever possible so that the proposed node, relationship, or correction can be evaluated against the same evidentiary principles used for the existing genealogy.

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

The research data and documentation deposited on Zenodo are released under the **Creative Commons Attribution 4.0 International (CC BY 4.0)** licence.

The underlying publications and other source materials remain subject to their respective copyright and licensing terms and are not redistributed as part of the public dataset.

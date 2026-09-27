# **ML Challenge 2026: Business Entity Resolution Solution** 

**Team Name:** EVARA 

**Team Members:** Anusha YK, Ashutosh Srivastava, Ananya P, Akash A **Submission Date:** 27 September 2026 

## **1. Executive Summary** 

EVARA developed a business entity-resolution pipeline to identify records across three large business datasets that refer to the same real-world business entity. The solution combines data normalization, candidate generation through blocking, similarity-based feature engineering, and machine-learning-based classification. 

The approach focuses on reducing the extremely large comparison space while using multiple signals from business names, addresses and country information to distinguish matching and non-matching entities. 

## **2. Methodology** 

### **2.1 Problem Analysis** 

The challenge requires matching each Source 1 business entity to zero, one, or multiple corresponding records from Source 2 and Source 3. 

Dataset sizes: 

- Source 1: 2,206,821 records 

- Source 2: 5,034,616 records 

- Source 3: 5,285,603 records 

- Ground Truth: 2,206,821 records 

All source datasets contain entity_id, business_name, business_address and country. The ground-truth dataset contains source1_entity_id and matched_entity_ids. 

EDA identified noise in capitalization, punctuation, Unicode representation, whitespace, abbreviations, spelling, address formatting and missing information. The large dataset size makes exhaustive pairwise comparison computationally impractical. 

Business-name normalization included lowercase conversion, Unicode normalization, punctuation handling, whitespace normalization and missing-value handling. The normalized value was stored as name_normalized. 

The test set also contains France in addition to the countries present in training data, so country was treated as an open-set label. 

### **2.2 Solution Strategy** 

Approach Type: Blocking + Machine Learning Classifier 

Core Innovation: Candidate generation combined with name, address and country-based features so detailed matching is performed on a reduced candidate space instead of every possible pair. 

Pipeline: 

Source Data → Data Normalization → Candidate Generation / Blocking → Feature Engineering → Machine Learning Model → Matching Decision → Output Generation. 

Evaluation uses macro F₀ ₅. , which places greater importance on precision. 

## **3. Candidate Generation (Blocking)** 

Blocking was used to reduce the comparison space before applying the matching model. 

Blocking key: Normalized business name. 

Block statistics: 

- Source 1 unique blocks: 375 

- Source 2 unique blocks: 2,624 

- Source 3 unique blocks: 2,596 

- Common Source 1–Source 2 blocks: 375 

The initial configuration produced an estimated 93,205,788,932 Source 1–Source 2 candidate pairs, approximately 93.21 billion. The largest individual block, s_5, produced approximately 6.29 billion candidate pairs. 

This showed that the initial blocking strategy was too broad and required further refinement. Candidate generation was designed to retain potentially matching records before the more selective matching stage. 

## **4. Matching Model** 

Name features: 

- name_similarity 

- name_length_diff 

Address features: 

- address_similarity 

- address_length_diff 

Other: 

- country_match 

The current feature list therefore contains five core features: 

1. name_similarity 

2. address_similarity 

3. country_match 

4. name_length_diff 

5. address_length_diff 

Additional approaches identified during feature development include Jaccard similarity, TF-IDF cosine similarity, Levenshtein distance and token overlap score. 

Models evaluated: 

- Logistic Regression 

- Random Forest 

- XGBoost 

- LightGBM 

The models use the engineered matching features to determine whether a candidate record corresponds to the Source 1 entity. 

Final selected model: The supplied model documentation does not record the final selected model; the final implementation should be treated as authoritative. 

Threshold selection: The supplied model documentation lists Accuracy, Precision, Recall and F1; the challenge evaluates submissions using macro F₀ ₅. . 

## **5. Results & Error Analysis** 

The team evaluated approaches using Accuracy, Precision, Recall and F1. The challenge's official metric is macro F₀ ₅. , which gives twice as much weight to precision. 

F₀ ₅. Score (macro): The supplied project documentation does not contain the final validation F₀ ₅. value. 

Common false positives (wrong merges): Different businesses with highly similar names or addresses, especially common names or records with limited identifying information. 

Common false negatives (missed matches): The same business represented using substantially different names or addresses, including abbreviations, spelling variations, transliteration differences or missing components. 

Normalization and multiple matching signals were used to reduce these errors. 

## **6. Conclusion** 

EVARA's solution uses a scalable entity-resolution pipeline combining normalization, blocking, feature engineering and machine-learning-based matching. 

EDA demonstrated that exhaustive comparison is impractical at this scale and that blocking quality is critical. The feature set combines business-name similarity, address similarity, country agreement and length-based signals. 

## **Appendix A. Code Artefacts** 

The solution is organized into notebooks, source code and supporting documentation. 

Main artefacts: 

- notebooks/01_EDA.ipynb — exploratory analysis and blocking investigation. 

- notebooks/01_baseline_pipeline.ipynb — baseline pipeline. 

- notebooks/LightGBM_Model.ipynb — LightGBM implementation. 

- notebooks/XGBoost_Model.ipynb — XGBoost implementation. 

- notebooks/Model_Comparison.ipynb — model comparison. 

- src/ — reusable source implementation. 

- docs/ — EDA, feature and model documentation. 

- requirements.txt — dependencies. 

Reproduction flow: 

Load data → Normalize → Generate candidates → Calculate features → Train/apply model → Generate predictions → Generate candidate_pairs.tsv → Generate matching_results.tsv. 

## **Appendix B. Additional Results** 

EDA observations: 

- Source 1 — 2,206,821 records 

- Source 2 — 5,034,616 records 

- Source 3 — 5,285,603 records 

- Normalized-name blocking produced 375 Source 1 blocks, 2,624 Source 2 blocks and 2,596 Source 3 blocks. 

- The analysed Source 1–Source 2 configuration produced approximately 93.21 billion candidate pairs. 

- The largest analysed block produced approximately 6.29 billion candidate comparisons. 

Core features: 

name_similarity, address_similarity, country_match, name_length_diff and address_length_diff. 

Models evaluated: 

Logistic Regression, Random Forest, XGBoost and LightGBM. 



<!-- Start of picture text -->
(Blocking)<br><!-- End of picture text -->



<!-- Start of picture text -->
(Train / Apply)<br><!-- End of picture text -->


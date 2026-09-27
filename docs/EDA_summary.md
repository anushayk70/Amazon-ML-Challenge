# EDA Summary

## 1. Dataset Overview

The Amazon ML Challenge training dataset consists of three source datasets and one ground-truth dataset.

| Dataset | Number of Records |
|---|---:|
| Source 1 | 2,206,821 |
| Source 2 | 5,034,616 |
| Source 3 | 5,285,603 |
| Ground Truth | 2,206,821 |

### Source Dataset Attributes

All three source datasets contain the following attributes:

- `entity_id`
- `business_name`
- `business_address`
- `country`

The ground-truth dataset contains:

- `source1_entity_id`
- `matched_entity_ids`

---

## 2. Data Normalization

Business names were normalized before performing blocking analysis.

The normalization process included:

- Converting text to lowercase
- Unicode normalization
- Removing punctuation while preserving letters and numbers
- Normalizing whitespace
- Handling missing values

The normalized business name was stored in the `name_normalized` column.

---

## 3. Blocking Analysis

A strong blocking key was created using the normalized business name.

The resulting block statistics were:

| Dataset | Unique Blocks |
|---|---:|
| Source 1 | 375 |
| Source 2 | 2,624 |
| Source 3 | 2,596 |

The number of common blocks between Source 1 and Source 2 was:

**375**

---

## 4. Candidate-Pair Estimation

Using the current strong-blocking strategy, the estimated number of Source 1–Source 2 candidate pairs is:

**93,205,788,932**

Approximately:

**93.21 billion candidate pairs**

The largest blocks individually produce billions of potential comparisons.

For example, the `s_5` block produces approximately:

**6.29 billion candidate pairs**

---

## 5. Key Findings

### Dataset Scale

The source datasets contain millions of records. Therefore, exhaustive pairwise comparison between the datasets would be computationally impractical.

### Name Normalization

Business-name normalization is required before matching because variations in case, punctuation, Unicode representation and whitespace can affect entity matching.

### Blocking

Blocking provides a way to reduce the search space by grouping records that may correspond to the same entities.

### Current Blocking Limitation

The current strong-blocking strategy is still too broad.

The estimated candidate space of approximately **93.21 billion S1–S2 pairs** is too large for direct candidate-pair generation.

---

## 6. Recommendation for the Next Stage

The candidate-generation stage should refine the blocking strategy before generating candidate pairs.

Possible directions include:

- More selective blocking keys
- Multiple blocking strategies
- Multi-stage blocking
- Handling oversized blocks separately
- Reducing unnecessary candidate comparisons

The candidate-generation stage should aim to produce a manageable candidate set while retaining likely true matches.

---

## 7. EDA Handoff

The EDA stage provides the following information to the downstream team:

- Dataset sizes and structure
- Data normalization approach
- Ground-truth structure
- Blocking statistics
- Candidate-pair estimate
- Limitation of the current blocking strategy

The next stage can use these findings to design a more selective candidate-generation strategy.

# Candidate Generation

Purpose:
Reduce the search space before entity matching.

Input:
- Source 1 records
- Source 2 records
- Source 3 records

Output:
candidate_pairs.tsv

Strategy:
- Name normalization
- Address normalization
- Blocking on country
- Similarity based filtering

The generated candidate pairs are passed to the ML matching models.

# Raw Dataset

The original Amazon ML Challenge training dataset is not stored directly
in this repository because the complete dataset is too large for normal
GitHub file storage.

## Dataset Files

The raw training dataset consists of:

- `train_source1.tsv`
- `train_source2.tsv`
- `train_source3.tsv`
- `train_ground_truth.tsv`

## Dataset Location

The complete dataset is stored separately as a compressed archive:

`amazon_ml_datasets.zip`

The archive contains the four original training files.

## Using the Dataset

1. Obtain `amazon_ml_datasets.zip` from the team's shared Google Drive.
2. Extract the archive.
3. Place the four `.tsv` files inside this directory:

```text
data/raw/
├── train_source1.tsv
├── train_source2.tsv
├── train_source3.tsv
└── train_ground_truth.tsv

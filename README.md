# Business Entity Resolution Challenge

## Project Overview

This project aims to identify and match business entities across multiple data sources.

The objective is to determine whether records from different datasets refer to the same real-world business despite variations in naming, formatting, abbreviations, or address structure.

---

## Dataset

The project consists of:

- Source 1
- Source 2
- Source 3
- Ground Truth

Each source contains:

- entity_id
- business_name
- business_address
- country

---

## Project Workflow

Raw Data
↓
EDA
↓
Data Cleaning
↓
Normalization
↓
Candidate Generation
↓
Feature Engineering
↓
Machine Learning Models
↓
Prediction
↓
Submission Generation

---

## Repository Structure

```text
src/
│
├── candidate_generation/
├── models/
├── evaluation/
└── submission/

notebooks/
docs/
outputs/
data/
```

## Machine Learning Models

Implemented Models:

- Logistic Regression
- Random Forest
- XGBoost
- LightGBM

Evaluation Metrics:

- Accuracy
- Precision
- Recall
- F1 Score

---

## Documentation

Project documentation can be found in:

```text
docs/
├── EDA_Summary.md
├── Feature_List.md
└── model_notes.md
```

---

## Team Responsibilities

### Data Analysis Team

- Dataset exploration
- EDA
- Data quality assessment

### Feature Engineering Team

- Text normalization
- Candidate generation
- Similarity feature creation

### Machine Learning Team

- Model training
- Model evaluation
- Prediction generation
- Submission preparation

---

## Current Status

Completed:

- Repository setup
- EDA analysis
- Baseline ML pipeline
- Random Forest model
- XGBoost framework
- LightGBM framework
- Evaluation module

Pending:

- Candidate pair generation
- Feature engineering
- Final model training
- Submission generation

---

## Submission Outputs

Expected outputs:

- candidate_pairs.tsv
- matching_results.tsv

---

## Technologies Used

- Python
- Pandas
- NumPy
- Scikit-learn
- XGBoost
- LightGBM
- Google Colab
- GitHub


# Data Science with Python — Internship Projects

**Author:** Devarakonda Vignesh Varsha
**GitHub:** [@VigneshVarsha](https://github.com/PrinceExile)

## About This Project

This repository contains six weekly projects completed as part of a **Virtual Data
Science with Python** internship. Each week builds on the last — starting with raw
data acquisition and cleaning, moving through exploratory analysis and unsupervised
learning, and finishing with supervised learning, deep learning, and a full
end-to-end capstone pipeline.

Every notebook here is fully executable and was run end-to-end to produce the
outputs checked into it — nothing is a placeholder or a "this is what the result
would look like" description. Each week also has a companion Word report
(`Week_N_Report.docx`) with the full write-up: reasoning behind each decision,
evaluation metrics, discussion of limitations, and what I'd improve next.

## Overview

| Week | Folder | Task | Key result |
|------|--------|------|------------|
| 1 | [`week1_data_cleaning/`](week1_data_cleaning) | Data acquisition, cleaning & preprocessing (Titanic dataset) | 891 rows cleaned, 0 duplicates, model-ready feature set built |
| 2 | [`week2_eda_visualization/`](week2_eda_visualization) | Exploratory data analysis & visualization (Wine dataset) | Identified strongest class-separating features and a key multicollinearity risk (r = 0.865) |
| 3 | [`week3_clustering/`](week3_clustering) | Unsupervised learning & clustering (Iris dataset) | K-Means (k=3) vs true species: ARI 0.620, NMI 0.660 |
| 4 | [`week4_supervised_learning/`](week4_supervised_learning) | Supervised classification (Breast Cancer dataset) | 98.25% test accuracy, ROC-AUC 0.995 |
| 5 | [`week5_deep_learning/`](week5_deep_learning) | Deep learning application (MNIST digits) | 97.89% test accuracy after 10 epochs |
| 6 | [`week6_capstone/`](week6_capstone) | Integrative capstone (customer segmentation + spend prediction) | 4 customer segments; regression R² ≈ 0.93 |

## About Each Week

### Week 1 — Data Acquisition, Cleaning & Preprocessing
Dataset: **Titanic** (891 passengers, Kaggle).
Covers the full cleaning pipeline: missing-value analysis (Age, Cabin, Embarked),
duplicate and consistency checks, IQR-based outlier screening, median/mode
imputation, a `CabinKnown` indicator in place of guessing missing cabin values,
and a 99th-percentile fare cap to tame extreme outliers without deleting them.
Ends with a clean, model-ready, fully numeric feature set.

### Week 2 — Exploratory Data Analysis & Visualization
Dataset: **Wine Recognition** (178 samples, 13 chemical features, 3 cultivars).
Univariate and bivariate analysis, class-wise boxplots, a full correlation
heatmap, and class-level feature-mean comparisons. The standout finding: Total
Phenols and Flavanoids are strongly correlated (r = 0.865) — a concrete
multicollinearity risk flagged for any future linear model trained on this data.

### Week 3 — Unsupervised Learning & Clustering
Dataset: **Iris** (150 samples, 3 species).
K-Means with elbow + silhouette analysis to pick k, PCA visualization, a
hierarchical clustering cross-check, and a distance-to-centroid outlier check
within each cluster. Clusters are compared against the true species labels
*after* fitting — setosa separates perfectly (100% match), while versicolor and
virginica overlap, measured with Adjusted Rand Index (0.620) and Normalized
Mutual Information (0.660).

### Week 4 — Supervised Learning Model Implementation
Dataset: **Breast Cancer Wisconsin (Diagnostic)** (569 samples).
Logistic Regression inside a `Pipeline` (scaler + classifier) to avoid data
leakage, validated with 5-fold stratified cross-validation before touching the
test set. Result: 98.25% test accuracy, ROC-AUC 0.995, with only 2
misclassifications out of 114 test cases — including a close look at which
error (false negative vs. false positive) actually matters more in a medical
context.

### Week 5 — Deep Learning Application
Dataset: **MNIST** (60,000 train / 10,000 test handwritten digits).
A feed-forward neural network (Dense → Dropout → Dense → Softmax) built in
TensorFlow/Keras. Tracks training/validation accuracy and loss across all 10
epochs, evaluates per-class precision/recall, and identifies the specific digit
pairs the model confuses most (9↔4, 7↔2, 5↔3). Includes a network fallback so
the dataset still loads on networks that block Google's default MNIST host.

### Week 6 — Integrative Capstone Project
Project: **Customer segmentation + spending prediction** on retail transaction
data. Combines everything from the previous five weeks into one pipeline: data
cleaning, RFM feature engineering (Recency, Frequency, Monetary), K-Means
customer segmentation, and a Random Forest regressor predicting customer spend.
Four customer segments emerge, with a small high-value segment driving a
disproportionate share of revenue; the regression explains ~93% of spend
variance. *(See the dataset note below — this week uses a structurally
identical synthetic dataset.)*

Each folder contains:
- A `.ipynb` notebook with the runnable code and outputs
- The corresponding `Week_N_Report.docx` with the full write-up, reasoning, and discussion

## Setup

```bash
pip install -r requirements.txt
```

Then open any notebook with Jupyter:

```bash
jupyter notebook week1_data_cleaning/week1_titanic_cleaning.ipynb
```

All notebooks use public, freely available datasets loaded directly via `scikit-learn`
or a public URL — no manual downloads required, **except Week 6** (see note below).

## Tools & Tech Stack

Python · Pandas · NumPy · Matplotlib · Seaborn · Scikit-learn · SciPy · TensorFlow/Keras

## Note on Week 6's Dataset

The Week 6 capstone is built around the structure of the well-known UCI/Kaggle
**Online Retail** dataset. That specific file wasn't reachable from the environment
this was built in, so the notebook generates a synthetic transaction dataset with the
same column structure and the same realistic data-quality issues (missing customer
IDs, cancelled orders, zero-price rows) instead. This is disclosed in the notebook
and in `Week_6_Report.docx`. Every number reported is a real, computed result — just
on the synthetic stand-in rather than the original file. To reproduce with the real
dataset, download `Online Retail.xlsx` from UCI or Kaggle and swap out the data-loading
cell; the rest of the pipeline runs unchanged.

## Note on Week 5's Dataset

`tf.keras.datasets.mnist.load_data()` downloads from Google's storage, which can be
blocked on some networks. The Week 5 notebook falls back to an identical mirrored copy
of MNIST if that host is unreachable, so it runs in restricted-network environments too.

## Author

**Devarakonda Vignesh Varsha**
B.Tech CSE (AI & ML), Sri Chaitanya Institute of Technology & Research
[GitHub](https://github.com/PrinceExile)
```

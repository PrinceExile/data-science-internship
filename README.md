# Data Science with Python — Internship Projects

Six weekly projects completed as part of a Virtual Data Science with Python internship.
Each week has a runnable Jupyter notebook plus a detailed Word report covering the
reasoning, evaluation, and discussion behind the code.

## Structure

| Week | Folder | Task | Key result |
|------|--------|------|------------|
| 1 | [`week1_data_cleaning/`](week1_data_cleaning) | Data acquisition, cleaning & preprocessing (Titanic dataset) | 891 rows cleaned, 0 duplicates, model-ready feature set built |
| 2 | [`week2_eda_visualization/`](week2_eda_visualization) | Exploratory data analysis & visualization (Wine dataset) | Identified strongest class-separating features and a key multicollinearity risk (r = 0.865) |
| 3 | [`week3_clustering/`](week3_clustering) | Unsupervised learning & clustering (Iris dataset) | K-Means (k=3) vs true species: ARI 0.620, NMI 0.660 |
| 4 | [`week4_supervised_learning/`](week4_supervised_learning) | Supervised classification (Breast Cancer dataset) | 98.25% test accuracy, ROC-AUC 0.995 |
| 5 | [`week5_deep_learning/`](week5_deep_learning) | Deep learning application (MNIST digits) | 97.89% test accuracy after 10 epochs |
| 6 | [`week6_capstone/`](week6_capstone) | Integrative capstone (customer segmentation + spend prediction) | 4 customer segments; regression R² ≈ 0.93 |

Each folder contains:
- A `.ipynb` notebook with the runnable code and outputs
- The corresponding `Week_N_Report.docx` with full write-up, reasoning, and discussion

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

## Tools used

Python, Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn, SciPy, TensorFlow/Keras.

## Note on Week 6's dataset

The Week 6 capstone is built around the structure of the well-known UCI/Kaggle
**Online Retail** dataset. That specific file wasn't reachable from the environment
this was built in, so the notebook generates a synthetic transaction dataset with the
same column structure and the same realistic data-quality issues (missing customer
IDs, cancelled orders, zero-price rows) instead. This is disclosed in the notebook
and in `Week_6_Report.docx`. Every number reported is a real, computed result — just
on the synthetic stand-in rather than the original file. To reproduce with the real
dataset, download `Online Retail.xlsx` from UCI or Kaggle and swap out the data-loading
cell; the rest of the pipeline runs unchanged.

## Note on Week 5's dataset

`tf.keras.datasets.mnist.load_data()` downloads from Google's storage, which can be
blocked on some networks. The Week 5 notebook falls back to an identical mirrored copy
of MNIST if that host is unreachable, so it runs in restricted-network environments too.


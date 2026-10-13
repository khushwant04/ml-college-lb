# ML College Lab

Machine learning lab experiments (college coursework), one Jupyter notebook per experiment, using
scikit-learn, pandas, matplotlib and seaborn.

## Experiments

| Notebook | Topic | Data | Printed result |
|----------|-------|------|----------------|
| `exp_1_california_housing.ipynb` | EDA: histograms, box plots, IQR outlier report | California Housing (`sklearn`) | - |
| `exp_2_california_plot.ipynb` | Correlation matrix, heatmap, pair plot | California Housing | - |
| `exp_3_pca.ipynb` | PCA to 2 components, loadings | Iris | 95.8% variance explained |
| `exp4_find_s_algorithm.ipynb` | Find-S concept learning | `data/training_data.csv` (EnjoySport) | see note below |
| `exp_5_knn.ipynb` | k-NN from scratch on 1-D synthetic data, k = 1, 3, 5, 20 | random (seed 42) | - |
| `exp_6_locally_weighted_regression.ipynb` | Locally weighted regression (Gaussian kernel, tau = 0.5) | noisy sine | - |
| `exp_7_linear_polynomial_regression.ipynb` | Linear and polynomial regression | Boston Housing (OpenML), Auto MPG (UCI) | R² 0.543 / 0.595 |
| `exp_8_decision_tree_breast_cancer.ipynb` | Decision tree classifier + tree plot | Breast Cancer Wisconsin | 94.74% test accuracy |
| `exp_9_naive_bayes_olivetti.ipynb` | Gaussian Naive Bayes on face images | Olivetti Faces | 80.83% test, 87.25% 5-fold CV |
| `exp_10_kmeans_breast_cancer.ipynb` | K-Means (k=2) + PCA visualisation | Breast Cancer Wisconsin | see note below |

## Getting started

```bash
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
jupyter notebook
```

Most datasets are downloaded on first run through `sklearn.datasets` (California Housing,
Olivetti Faces, OpenML Boston) or directly from the UCI repository (Auto MPG), so experiments 1, 2,
7 and 9 need internet access. Run `exp4_find_s_algorithm.ipynb` from the repository root so it
finds `data/training_data.csv`.

## Notes

- **Find-S:** `data/training_data.csv` originally had no header row, so pandas used the first
  example as column names and the notebook trained on only 3 rows. A header row has been added;
  the saved notebook outputs predate that fix. Re-running gives the textbook hypothesis
  `['Sunny', 'Warm', '?', 'Strong', '?', '?']`.
- **K-Means:** cluster IDs are arbitrary, and the notebook compares them directly with the true
  labels, so the printed classification report shows 9% "accuracy". The printed confusion matrix
  (`[[36, 176], [339, 18]]`) corresponds to about 90.5% agreement once the two cluster IDs are
  swapped.
- `ml_dos.zip` (~8 MB) holds HTML exports of the ten labs and the lab record as PDF and DOCX. It
  duplicates the notebooks and is not needed to run anything.

## Project structure

```
exp_*.ipynb, exp4_*.ipynb   # one notebook per experiment
data/training_data.csv      # Find-S training examples
ml_dos.zip                  # lab record and HTML exports
requirements.txt
```

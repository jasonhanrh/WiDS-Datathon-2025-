# 🧠 WiDS Datathon++ 2025: Predicting Brain Age and Exploring Sex Differences

This repository contains our solution to the **WiDS Datathon++ 2025 University Challenge**, where the goal is to predict chronological age from fMRI-derived functional brain connectivity data and investigate sex-based differences in prediction performance and neural network structure.

---

## 📌 Project Overview

Adolescent brain development varies across individuals and may follow distinct patterns by sex. This project focuses on two key objectives:

1. **Accurately predict brain age** using a combination of functional connectome features (~20,000 dimensions) and rich metadata (demographics, psychological traits).
2. **Explore sex differences** in model performance and connectome structure through statistical testing and network-based analysis.

---

## 📂 Dataset

The dataset is derived from the **Healthy Brain Network (HBN)** initiative and includes:

- 🧠 **Connectome features**: 200×200 resting-state fMRI correlation matrices vectorized into upper-triangular feature vectors.
- 👥 **Metadata**: Includes age, sex, BMI, race, handedness, parental education, psychological factor scores (e.g., p-factor, internalizing, externalizing, attention).

Total samples: **1,104 participants**, aged **5–21 years**.

---

## ⚙️ Methods

### 🔢 Preprocessing
- PCA for connectome dimensionality reduction (retaining 90% variance).
- Metadata imputation and one-hot encoding.
- Lasso regression for feature selection.

### 🤖 Modeling
- **Ridge Regression** (with and without metadata selection).
- **XGBoost** with **Bayesian Optimization**.
- **Ensembling**: Weighted average and Stacking.
- **Evaluation Metric**: Root Mean Squared Error (RMSE).

### 🧪 Sex Differences Analysis
- RMSE and residuals by sex and age group.
- PCA distribution testing.
- Partial Dependence Plots (PDP) and SHAP value comparison.
- Network analysis of top 50 sex-differentiated connectome edges.

---

## 📈 Key Results

| Model                     | Validation RMSE |
|--------------------------|------------------|
| Ridge Regression (Full)  | 6.80             |
| Ridge (5-Fold Averaging) | 5.94             |
| XGBoost (Tuned)          | 2.69             |
| Weighted Ensemble        | 2.24             |
| Stacked Ensemble         | **1.74**         |

- **PC1** from connectome PCA showed significant sex differences *(p = 0.0106)*.
- Ridge residuals showed mild but consistent sex-specific prediction bias.
- Network analysis revealed concentrated sex-based divergence in connectivity, especially around Nodes 61 and 192.

---

## 📁 Repository Structure

```
├── data/                      # Input data files (not included here due to privacy)
├── scripts/                   # Supporting scripts for modeling & visualization
├── report/                    # R Markdown report (.Rmd + HTML output)
├── figs/                      # Output plots and graphs
├── models/                    # Saved model objects (optional)
├── README.md                  # Project summary and usage
└── requirements.txt           # R package dependencies (for renv or manual install)
```

---



## 🧑‍💻 Team

- **Ruihang (Jason) Han** – Lead developer; responsible for modeling, connectome analysis, sex differences evaluation, and final report writing  
- **Chenran Zhang** – Exploratory data analysis (EDA) ,visualization


Affiliation: *Boston University – MSSP Program*

---

## 📜 License

This project is licensed under the MIT License – see the `LICENSE` file for details.

---

## 📬 Acknowledgments

This work was conducted as part of the [WiDS Datathon++ 2025 University Challenge](https://www.widsconference.org/datathon.html). We thank the organizers and the Healthy Brain Network (HBN) for providing the dataset.

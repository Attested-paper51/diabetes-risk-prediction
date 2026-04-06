# Early Diabetes Risk Prediction Using Machine Learning on CDC Health Indicators

## Executive Summary

> **Best model**: Logistic Regression + SMOTE and XGBoost + `scale_pos_weight` — both achieve **F1 = 0.47, AUC-ROC = 0.82, Recall = 0.76** on the held-out test set, confirmed stable by 5-fold cross-validation (F1 = 0.469 ± 0.003).
> **Key finding**: Balancing the training data matters more than model choice — recall jumps from 0.21 (raw) to 0.76 (balanced) across all model families.
> **Explainability**: SHAP analysis identifies **GenHlth, BMI, Age, and HighBP** as the dominant risk factors, consistent across both model architectures and aligned with EDA correlations.

---

## Team Members
- Muhammed Bilal
- Yousef Ebrahim
- Juan Franco Boeta

## Overview
This project uses machine learning to predict Type 2 diabetes risk using the CDC's Behavioral Risk Factor Surveillance System (BRFSS) dataset. We focus on two core challenges: handling severe class imbalance in health data, and using SHAP explainability to identify the most important risk factors driving predictions.

## Dataset
CDC BRFSS 2015 Health Indicators Dataset — 253,680 records, 21 features, binary target (diabetes vs no diabetes).
- Source: [Kaggle](https://www.kaggle.com/datasets/alexteboul/diabetes-health-indicators-dataset)
- Class split: 84% healthy, 16% diabetic (severe imbalance)

## Project Structure

```
diabetes-risk-prediction/
├── 01_eda.ipynb              # EDA, preprocessing, train/test split, scaling, saves arrays
├── 02_modeling.ipynb         # All model training, balancing experiments, SHAP analysis
├── Data/
│   ├── X_train.npy           # Raw unscaled training features
│   ├── X_test.npy            # Raw unscaled test features
│   ├── X_train_scaled.npy    # StandardScaler training features
│   ├── X_test_scaled.npy     # StandardScaler test features
│   ├── y_train.npy           # Training labels
│   ├── y_test.npy            # Test labels
│   ├── feature_names.csv     # Feature column names
│   ├── X_train_smote.npy     # SMOTE-balanced training features (from scaled)
│   ├── y_train_smote.npy
│   ├── X_train_under.npy     # Undersampled training features (from scaled)
│   ├── y_train_under.npy
│   ├── shap_summary_plot.png
│   ├── shap_bar_plot.png
│   ├── shap_waterfall_diabetic.png
│   ├── shap_waterfall_healthy.png
│   ├── shap_xgb_summary.png
│   ├── shap_lr_vs_xgb.png
│   ├── precision_recall_curves.png
│   ├── confusion_matrices.png
│   ├── threshold_optimisation.png
│   └── eda_feature_importance.png
├── CS 6140 Project Proposal.pdf
├── PROJECT_ABSTRACT.md
└── README.md
```

## How to Reproduce

1. Download the dataset from Kaggle and place the CSV in `Data/`
2. Run `01_eda.ipynb` top to bottom — this generates all `.npy` array files
3. Run `02_modeling.ipynb` top to bottom — this trains all models and generates plots

> **Note:** Paths use `Data/` (capital D). Both notebooks must be run from the repo root directory.

## Models Evaluated

| Model | Best Config | F1 | AUC-ROC | Recall |
|---|---|---|---|---|
| Random Forest | Raw (baseline) | 0.30 | 0.79 | 0.21 |
| XGBoost | scale_pos_weight | 0.47 | 0.82 | 0.76 |
| **Logistic Regression** | **SMOTE** | **0.47** | **0.82** | **0.76** |
| KNN (k=5) | Undersampling | 0.43 | 0.76 | 0.74 |

## Key Findings
- Class balancing (SMOTE or undersampling) improved recall from 0.21 → 0.76 across all models
- Logistic Regression + SMOTE and XGBoost + scale_pos_weight are the top performers
- SHAP identifies **GenHlth, BMI, Age, HighBP** as the primary risk drivers — consistent across both LR and XGBoost, and aligned with EDA findings

## Tools and Libraries
- Python, scikit-learn, XGBoost, imbalanced-learn, SHAP
- pandas, numpy, matplotlib, seaborn

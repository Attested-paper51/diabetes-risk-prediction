# Project Abstract

## Project Title
Early Diabetes Risk Prediction Using Machine Learning on CDC Health Indicators

## Abstract
Diabetes is one of the most common chronic diseases worldwide, and early detection of at-risk individuals can significantly improve outcomes through lifestyle intervention and early treatment. The core challenge with real health datasets is that diabetic patients are heavily outnumbered by healthy individuals — an 84/16 split in this dataset — which causes models trained naively to achieve high accuracy while completely failing to catch the patients who actually need attention.

This project uses the CDC BRFSS 2015 dataset (253,680 survey responses, 21 health features) to investigate how class imbalance techniques affect a model's ability to detect at-risk patients, and applies SHAP explainability analysis to identify the health and lifestyle factors that drive predictions. We train and evaluate four model families — Logistic Regression, K-Nearest Neighbours, Random Forest, and XGBoost — across multiple balancing strategies (SMOTE, random undersampling, and built-in class weighting), evaluating with F1-score, AUC-ROC, and precision-recall curves rather than accuracy.

The key finding is that **balancing the training data matters more than model choice**: all models converge to recall ≈ 0.21 on raw data, while balanced models achieve recall ≈ 0.76. The best models are Logistic Regression + SMOTE and XGBoost with scale_pos_weight, both reaching F1 = 0.47 and AUC-ROC = 0.82. SHAP analysis confirms that **GenHlth, BMI, Age, and HighBP** are the dominant risk drivers, consistent across both model architectures and aligned with EDA findings — validating that the models have learned genuine medical signal.

## Scope of the Work

### Muhammed
- Project setup and coordination (GitHub repo, documentation)
- Exploratory Data Analysis: feature distributions, correlations, visualisations
- Data preprocessing and cleaning
- Model training and evaluation: Random Forest, XGBoost (baseline and balanced)

### Yousef
- Model training and evaluation: Logistic Regression, KNN
- Balancing experiments: SMOTE and undersampling on scaled data
- SHAP explainability analysis (Logistic Regression and XGBoost)
- Performance metrics, comparison tables, and visualisations

### Juan
- Implementing class imbalance techniques (SMOTE, SMOTE-ENN, undersampling)
- Precision-recall curve analysis and threshold discussion
- Confusion matrix visualisations
- Final conclusions and limitations

### Shared
- Literature review and related work
- Writing and editing the final report
- Presentation slides and delivery

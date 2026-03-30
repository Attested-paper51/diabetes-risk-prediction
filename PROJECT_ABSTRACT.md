# Project Abstract

## Project Title
Early Diabetes Risk Prediction Using Machine Learning on CDC Health Indicators

## Abstract
Diabetes is one of the most common chronic diseases worldwide, and early detection of at-risk individuals can make a big difference in outcomes through lifestyle changes and early treatment. The challenge with real health datasets is that diabetic patients are heavily outnumbered by healthy individuals, which causes models to look accurate on paper while completely failing to catch the people who actually need attention. This project uses the CDC BRFSS dataset (250k+ survey responses, 21 health features) to investigate how different class imbalance techniques affect a model's ability to detect at-risk patients, and applies SHAP explainability analysis to uncover which health and lifestyle factors drive predictions the most. We compare baseline models (Logistic Regression, KNN) against stronger models (Random Forest, XGBoost) across multiple balancing strategies, evaluating with metrics like F1-score, AUC-ROC, and precision-recall curves instead of relying on accuracy alone.

## Scope of the Work

### Muhammed
- Project setup and coordination (GitHub repo, documentation)
- Exploratory Data Analysis (EDA): understanding feature distributions, correlations, visualizations
- Data preprocessing and cleaning
- Model training and evaluation: implementing Random Forest, XGBoost

### Yousef
- Model training and evaluation: implementing Logistic Regression, KNN
- Hyperparameter tuning
- Running experiments comparing model performance across different balancing strategies
- Generating performance metrics and comparison tables/figures

### Juan
- Implementing class imbalance techniques (SMOTE, SMOTE-ENN, undersampling)
- SHAP explainability analysis on best-performing models
- Creating visualizations for feature importance and model interpretability

### Shared
- Literature review and related work
- Writing and editing the final report
- Presentation slides and prep
- Presentation practice and delivery

![Python](https://img.shields.io/badge/Python-3.10-blue)
![ML](https://img.shields.io/badge/Machine%20Learning-Project-green)
# Machine Learning Assessment — Assignment 4 (A + B)

# Overview

This repository contains solutions for **Assignment 4**, covering both technical machine learning implementation (**Part A**) and business case analysis (**Part B**).

The assignment demonstrates end-to-end capabilities including:

* Supervised Learning
* Unsupervised Learning
* Feature Engineering & ML Pipelines
* Business-Oriented Analysis

---

# Repository Structure

``````
ml-assessment-shlok-sonawane/
│
├──|part_a|
│   ├── q1_supervised.ipynb
│   ├── q2_unsupervised.ipynb
│   └── q3_feature_engineering.ipynb
│
├──|part_b|
│   └── business_analysis.md
│
└── |datasets|
     ├── q1_heart_disease.csv
     ├── q2_customers.csv
     └── q3_retail_promotions.csv
``````

-------

# Part A — Machine Learning Implementation

## Q1: Supervised Learning — Heart Disease Prediction

* Built classification models to predict heart disease
* Models used:

  * Decision Tree
  * Random Forest
  * Gradient Boosting
* Evaluation using:

  * Confusion Matrix
  * Precision, Recall, F1-score
* **Best Model:** Random Forest (highest F1-score)
* Performed hyperparameter tuning using GridSearchCV

------

##  Q2: Unsupervised Learning — Customer Segmentation

* Applied **K-Means clustering** for segmentation
* Used **Elbow Method** → Optimal K = 4
* Interpreted clusters in business terms
* Applied **PCA** for dimensionality reduction
* Visualized clusters in 2D space

------

# Q3: Feature Engineering & Regression Pipeline

* Built a **scikit-learn pipeline** for predicting `items_sold`
* Performed:

  * Date feature engineering
  * Temporal train-test split
  * ColumnTransformer preprocessing
* Models used:

  * Linear Regression
  * Random Forest Regressor

# Results:

* **Linear Regression outperformed Random Forest**

  * RMSE: 39.64 vs 42.88
  * MAE: 29.30 vs 33.87

# Key Drivers:

* Day of week
* Store size
* Location type
* Competition density
* Seasonal trends

------

# Part B — Business Case Analysis

# Scenario:

Optimizing promotional strategies across 50 retail stores to maximize sales.

# Key Components:

* Problem formulation as a regression task
* Data strategy (multi-table joins & aggregation)
* EDA planning and imbalance handling
* Model evaluation using time-based splits
* Deployment strategy with monitoring

#  Insights:

* Sales are influenced by both **business factors** and **temporal patterns**
* Different store types require **customized strategies**
* Proper target selection is critical for meaningful predictions

------

#  Technologies Used

* Python
* Pandas, NumPy
* Scikit-learn
* Matplotlib, Seaborn

------

#  Key Takeaways

* End-to-end ML workflow from data → model → business insights
* Importance of proper evaluation metrics (F1, RMSE, MAE)
* Value of combining technical models with business understanding
* Real-world considerations like data leakage and deployment

------

#  Author

**Shlok Sonawane bit_som_BA_2511721**
Machine Learning & Data Analytics Enthusiast

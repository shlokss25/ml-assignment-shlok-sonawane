# Business Case Analysis

#Promotion Effectiveness at a Fashion Retail Chain

---

#  B1. Problem Formulation

# (a) Machine Learning Problem

The goal is to predict the **number of items sold** for each store under different promotional strategies.

* **Target Variable:** `items_sold`

* **Input Features:**

  * Promotion type (Flat Discount, BOGO, etc.)
  * Store attributes (store size, location type)
  * Competition density
  * Temporal features (month, weekend, festival)
  * Customer behavior (footfall, past sales trends)

* **Problem Type:** Supervised Learning — Regression

# Justification:

The target variable (`items_sold`) is continuous, making this a regression problem. The model learns from historical labeled data to predict future outcomes.

---

# (b) Why Items Sold > Revenue

Using **items sold (volume)** is more reliable than revenue because:

* Revenue can be distorted by pricing changes or discounts
* Promotions directly influence volume, not necessarily profit
* Volume reflects **customer demand more accurately**

# Broader Principle:

- The target variable must align with the **business objective**.
Choosing the wrong target can lead to misleading models, even if predictions are accurate.

---

# (c) Alternative Modelling Strategy

Instead of a single global model, use:

## **Segmented / Hierarchical Models**

* Separate models by **location type** (urban, rural, semi-urban)
  OR
* Include **store-level features + interaction effects**

# Justification:

Different stores respond differently to promotions due to:

* Customer demographics
* Competition
* Buying behavior

This improves model accuracy and personalization.

---

#  B2. Data and EDA Strategy

# (a) Data Joining Strategy

We combine four tables:

* Transactions
* Store attributes
* Promotion details
* Calendar data

# Join Method:

* Join on **store_id** and **date**

# Final Dataset Grain:

**One row = one store per month**

# Aggregations:

* Total `items_sold` per store per month
* Average basket size
* Total transactions
* Promotion applied in that month
* Festival/weekend indicators

---

# (b) EDA Strategy

# 1. Promotion vs Sales (Bar Plot)

* Compare average items sold by promotion type
  -  Helps identify most effective promotions

---

# 2. Time Series Trend

* Monthly sales trends
  -  Detect seasonality and demand patterns

---

# 3. Sales by Location Type

* Urban vs rural vs semi-urban
  - Understand regional differences

---

# 4. Correlation Heatmap

* Identify relationships between features
  - Helps feature selection

---

# 5. Distribution of Items Sold

* Check skewness and outliers
  - Decide scaling or transformation

---

# (c) Promotion Imbalance (80% no promotion)

# Problem:

* Model may learn bias toward “no promotion”
* Promotions may appear less effective than they are

# Solution:

* Use **balanced sampling**
* Add **promotion indicator features**
* Evaluate model separately on promotion vs non-promotion cases

---

# B3. Model Evaluation and Deployment

# (a) Train-Test Split & Metrics

## Split Strategy:

* Use **time-based split**
* Train on earlier months, test on recent months

# Why NOT random split:

* Causes **data leakage**
* Uses future data to predict past

---

# Metrics:

* **RMSE:** Measures large errors → penalizes big mistakes
* **MAE:** Measures average error → easy to interpret
* **R²:** Measures explained variance

- Lower RMSE & MAE = better predictions

---

# (b) Explaining Model Decisions

To understand why different promotions are recommended:

# Use Feature Importance

Example:

* December → High importance of **month + festival**
* March → Lower demand → discount works better

# Communication:

Explain to stakeholders:

* Seasonal demand differences
* Customer behavior changes
* Promotion effectiveness varies by time

---

# (c) Deployment Strategy

# 1. Save Model

* Use `joblib` or `pickle` to store trained pipeline

---

# 2. Monthly Prediction Workflow

* Collect new monthly data
* Apply same preprocessing pipeline
* Generate predictions for all stores

---

# 3. Monitoring

Track:

* RMSE over time
* Prediction drift
* Data drift (feature distribution changes)

---

# 4. Retraining Trigger

Retrain when:

* Model performance drops significantly
* New patterns emerge (e.g., new promotions, market changes)

---

# Final Conclusion

* Machine learning can optimize promotion strategies
* Sales volume is the correct target for decision-making
* Store-level differences require tailored modelling
* Time-aware evaluation ensures realistic performance
* Deployment and monitoring are essential for long-term success

This approach enables data-driven, scalable decision-making for maximizing retail sales.

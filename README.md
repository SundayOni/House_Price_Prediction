NB: Work in progress...

# 🏡 Machine Learning-Based House Price Prediction: A Case Study in West Yorkshire, UK.

A machine learning project to predict UK house prices using various regression models including Linear Regression, Random Forest, and XGBoost, with detailed EDA, preprocessing, and hyperparameter tuning.

---

## 📌 Table of Contents

* [Overview](#overview)
* [Problem Statement](#problem-statement)
* [Rationale & Stakeholder Relevance](#rationale-stakeholder-elevance)
* [Dataset](#dataset)
* [EDA & Preprocessing](#eda--preprocessing)
* [Modeling](#modeling)
* [Evaluation](#evaluation)
* [Hyperparameter Tuning](#hyperparameter-tuning)
* [Recommendations](#recommendations)
* [Conclusion](#conclusion)

---

## 🔍 Overview

This project aims to build a predictive model for house prices using a dataset scraped from Zoopla. It includes:

* Cleaning and feature engineering
* Exploratory Data Analysis (EDA)
* Building and comparing ML models
* Hyperparameter tuning for better performance
* Feature importance analysis

---

## 📌 Problem Statement

Accurately estimating house prices is crucial for buyers, sellers, developers, and policy makers in the real estate market. However, due to numerous influencing factors (e.g., location, property type, proximity to amenities), predicting house prices can be complex. This project seeks to build a reliable machine learning model to predict house prices in West Yorkshire, UK, using publicly available property listings data.

---

## 💡 Rationale & Stakeholder Relevance

This project is valuable for:

- Buyers: Understanding fair market prices.

- Estate Agents: Supporting accurate valuations and listing strategies.

- Policy Makers: Identifying housing trends across boroughs.

- Data Scientists: Demonstrating end-to-end ML workflows on real-world tabular data.

By combining data preprocessing, EDA, and multiple ML models (Linear Regression, Random Forest, XGBoost), this project aims to produce accurate, explainable results with practical use cases.

---

## 📂 Dataset

* **Source**: [Zoopla](https://www.zoopla.co.uk/)
* **Size**: \~X records with features like location, property type, number of rooms, distances to amenities, etc.
* **Target Variable**: `price`

---

## 📊 EDA & Preprocessing

* Handled missing values and dropped irrelevant columns
* Grouped categorical values (e.g. towns → boroughs, property types → property groups)
* Conducted:

  * **Univariate analysis**: distributions, value counts
  * **Bivariate analysis**: price vs. features using barplots, boxplots, scatterplots
* Scaled numerical features and one-hot encoded categorical ones using `ColumnTransformer` and `Pipeline`

---

## 🤖 Modeling

Used three main models:

1. **Linear Regression**
2. **Random Forest Regressor**
3. **XGBoost Regressor**

Each model was wrapped in a pipeline and trained using the same train/test split for fair comparison.

---

## ⚙️ Hyperparameter Tuning

* **Random Forest**:

  * Tuned `n_estimators`, `max_depth`, `min_samples_split`
  * Used `GridSearchCV`
* **XGBoost**:

  * Tuned `n_estimators`, `max_depth`, `learning_rate`, `colsample_bytree`
  * Used `GridSearchCV`

---

## 📈 Evaluation

Metrics used:

* **R-squared (R²)**
* **Root Mean Squared Error (RMSE)**
* **Mean Absolute Error (MAE)**

| Model                 | R²   | RMSE    | MAE     |
| --------------------- | ---- | ------- | ------- |
| Linear Regression     | 0.XX | XXXX.XX | XXXX.XX |
| Random Forest (Tuned) | 0.XX | XXXX.XX | XXXX.XX |
| XGBoost (Tuned)       | 0.XX | XXXX.XX | XXXX.XX |

---

## 🧪 Feature Importance

* Plotted feature importances for Random Forest and XGBoost
* Key predictors: `rooms`, `propertyGroup`, `borough`, `distance_to_school`, etc.

---

## ✅ Conclusion

* **XGBoost** performed best in terms of accuracy and generalization
* Feature engineering (e.g., borough and property group) significantly improved model performance
* Regularization and hyperparameter tuning helped reduce overfitting

---

## 🚀 Next Steps

* Try advanced techniques like stacking or ensemble averaging
* Integrate Ridge/Lasso regression for additional comparison
* Deploy the best model via a simple web app (e.g., Streamlit)

---

Thanks for checking out the project! 🚀 Feel free to fork or reach out with suggestions!

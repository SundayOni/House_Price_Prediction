# 🏡 House Price Prediction — West Yorkshire, UK

A machine learning project to predict house prices using property listings data scraped from Zoopla. Covers end-to-end ML workflow including EDA, preprocessing, model building, and hyperparameter tuning.

---

## 📌 Project Overview

Accurately estimating house prices is crucial for buyers, sellers, and policy makers. This project builds and compares regression models to predict house prices across the five West Yorkshire metropolitan boroughs using features such as property type, number of rooms, tenure, and proximity to amenities.

---

## 📂 Project Structure
```
House_Price_Prediction/
├── data/
│   └── house_prices_west_yorkshire.csv   # Raw Zoopla listings data
├── notebooks/
│   ├── 01_preprocessing_and_eda.ipynb    # Data cleaning, feature engineering, EDA
│   └── 02_modelling.ipynb                # Model building, evaluation, tuning
├── requirements.txt
└── README.md
```

---

## 📊 Dataset

- **Source**: Zoopla property listings (scraped via API)
- **Coverage**: West Yorkshire — Leeds, Bradford, Wakefield, Kirklees, Calderdale
- **Target variable**: `price`
- **Key features**: `rooms`, `numBaths`, `numRecepts`, `propertyGroup`, `MetBoroughs`, `tenure`, `listingCondition`, `ditsnace_to_school`, `ditsnace_to_train`

---

## 🔧 Methodology

### Preprocessing
- Converted data types for count variables (`numBaths`, `numRecepts`)
- Engineered `MetBoroughs` feature by mapping postcodes to West Yorkshire boroughs
- Grouped 20+ granular property types into 6 broader categories (`propertyGroup`)
- Handled missing values: median imputation for numeric fields, proportional imputation for `tenure`
- Dropped irrelevant columns (free text, identifiers, redundant location fields)

### Modelling
- Built sklearn `Pipeline` objects combining `ColumnTransformer` preprocessing with each model
- `StandardScaler` for numerical features, `OneHotEncoder` for categorical features
- Compared three models: Linear Regression (baseline), Random Forest, XGBoost

---

## 📈 Results

### Before Hyperparameter Tuning

| Model | R² | RMSE | MAE |
|---|---|---|---|
| Linear Regression | 0.5909 | £125,866 | £78,358 |
| Random Forest | 0.6532 | £115,891 | £71,711 |
| XGBoost | 0.6718 | £112,749 | £68,932 |

### After Hyperparameter Tuning (GridSearchCV, 5-fold CV)

| Model | R² | RMSE | MAE |
|---|---|---|---|
| Random Forest (Tuned) | 0.6694 | £113,147 | £69,475 |
| XGBoost (Tuned) | 0.6511 | £116,241 | £69,492 |

> **Note:** Hyperparameter tuning did not improve performance in this case. The baseline XGBoost remains the best model (R² = 0.67). This is a known outcome when GridSearchCV overfits to cross-validation folds on limited data.

---

## 🏆 Best Model

**XGBoost (Baseline)** — R² = 0.67, RMSE = £112,749, MAE = £68,932

Key predictors: number of rooms, property group, borough, and distance to amenities.

---

## 🚀 Setup
```bash
git clone https://github.com/SundayOni/House_Price_Prediction.git
cd House_Price_Prediction
pip install -r requirements.txt
```

Run notebooks in order:
1. `notebooks/01_preprocessing_and_eda.ipynb`
2. `notebooks/02_modelling.ipynb`

---

## 🔮 Future Improvements

- Apply log transformation to price target to improve model fit
- Explore ensemble stacking and Ridge/Lasso regression
- Deploy best model as a Streamlit web app
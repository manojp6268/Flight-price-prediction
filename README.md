# ✈️ Flight Price Prediction

> *Cutting through airline pricing complexity — predicting ticket costs before you book.*

[![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=flat-square&logo=python&logoColor=white)](https://python.org)
[![Scikit-learn](https://img.shields.io/badge/Scikit--learn-RandomForest-F7931E?style=flat-square&logo=scikit-learn&logoColor=white)](https://scikit-learn.org)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=flat-square&logo=jupyter&logoColor=white)](https://jupyter.org)

---

## What this does

Flight ticket pricing is notoriously volatile — the same seat can vary by hundreds of euros depending on airline, timing, stops, and duration. This project builds a regression pipeline that learns from historical flight data to predict ticket prices based on journey features.

What makes this pipeline more robust than a standard regression model: **ExtraTreesRegressor is used for feature importance analysis first**, identifying which variables actually drive price — then a **tuned RandomForestRegressor** is trained on the most impactful features.

---

## The approach

```
Flight Dataset
   │
   ▼
Exploratory Data Analysis
   │  ├── Price distribution across airlines and routes
   │  ├── Impact of stops, duration, and timing on price
   │  └── Outlier detection and treatment
   │
   ▼
Data Preprocessing
   │  ├── Date/time feature extraction
   │  │     (departure hour, arrival hour, journey day/month)
   │  ├── Encoding categorical variables
   │  │     (airline, source, destination, additional stops)
   │  └── Train/test split
   │
   ▼
Feature Selection — ExtraTreesRegressor
   │  ├── Computes feature importances across all variables
   │  └── Identifies top drivers of ticket price
   │
   ▼
RandomForestRegressor + Hyperparameter Tuning
   │  ├── RandomizedSearchCV for optimal parameters
   │  │     (n_estimators, max_depth, min_samples_split, etc.)
   │  └── Final model trained on selected features
   │
   ▼
Evaluation → MAE · RMSE · R²
```

---

## Why ExtraTrees for feature selection?

ExtraTreesRegressor is particularly effective at feature selection because:
- It builds fully randomised trees, reducing overfitting bias in importance scores
- It handles both numerical and categorical features cleanly
- It runs faster than standard RandomForest for importance ranking purposes

This two-stage approach — **select with ExtraTrees, predict with tuned RandomForest** — produces a leaner, more accurate final model than training on all features blindly.

---

## Key features in the dataset

| Feature | Description |
|---|---|
| `Airline` | Carrier operating the flight |
| `Source` | Departure city |
| `Destination` | Arrival city |
| `Dep_Time` | Departure time (hour extracted) |
| `Arrival_Time` | Arrival time (hour extracted) |
| `Duration` | Total flight duration |
| `Total_Stops` | Number of layovers (non-stop to 4 stops) |
| `Additional_Info` | Extra details (meal, no info, etc.) |
| `Date_of_Journey` | Journey date (day/month extracted) |
| `Price` | Target — ticket price in INR |

---

## Hyperparameter tuning

RandomizedSearchCV was used to tune the following parameters:

```python
param_grid = {
    'n_estimators'      : [100, 200, 300, 500],
    'max_depth'         : [None, 10, 20, 30],
    'min_samples_split' : [2, 5, 10],
    'min_samples_leaf'  : [1, 2, 4],
    'max_features'      : ['auto', 'sqrt', 'log2']
}
```

---

## Project structure

```
Flight-price-prediction/
│
├── flight_price.ipynb        ← Full EDA, feature selection & model training
├── Data_Train.xlsx           ← Training dataset
├── Test_set.xlsx             ← Test dataset
└── README.md
```

---

## Results

| Metric | Baseline RF | Tuned RF |
|--------|------------|----------|
| R²     | 0.798      | 0.812    |
| MAE    | ₹1,172     | ₹1,165   |
| RMSE   | ₹2,085     | ₹2,016   |
| Normalised RMSE | — | 2.7%  |

*Normalised RMSE: 0.027 - meaning the error is only 2.7% of the full price range.*

---

## Run it locally

**Step 1 — Clone the repo**
```bash
git clone https://github.com/manojp6268/Flight-price-prediction.git
cd Flight-price-prediction
```

**Step 2 — Install dependencies**
```bash
pip install pandas numpy scikit-learn matplotlib seaborn jupyter openpyxl
```

**Step 3 — Launch the notebook**
```bash
jupyter notebook flight_price.ipynb
```

---

## Tech stack

- **Python** — core language
- **Scikit-learn** — ExtraTreesRegressor (feature selection) + RandomForestRegressor (prediction)
- **RandomizedSearchCV** — hyperparameter optimisation
- **Pandas / NumPy** — data processing and feature engineering
- **Matplotlib / Seaborn** — visualisation
- **Jupyter Notebook** — exploration and training environment

---

## What this demonstrates

This project goes beyond basic regression — it shows a deliberate, two-stage ML pipeline with principled feature selection and systematic hyperparameter optimisation. These are exactly the techniques used in production ML systems where model efficiency and interpretability matter alongside raw accuracy.

---

## Author

**Manoj Prakash** — Data Scientist & AI/ML Engineer
M.Sc. Data Science @ Universität Trier · ex-Oracle Cerner · ex-Huawei

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=flat-square&logo=linkedin)](https://linkedin.com/in/manoj-p-a95b7b1a2)
[![Email](https://img.shields.io/badge/Email-manojp6268@gmail.com-1A2B4A?style=flat-square&logo=gmail)](mailto:manojp6268@gmail.com)

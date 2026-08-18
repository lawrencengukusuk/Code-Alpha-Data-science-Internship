# CodeAlpha Data Science Internship

## Data Science Projects Portfolio

This repository contains the data science projects completed during my Data Science Internship at CodeAlpha.

The projects demonstrate practical experience across two core areas of data science:

1. Unemployment Analysis in India
2. Car Price Prediction Using Machine Learning

Together, these projects demonstrate my ability to work through different stages of the data science workflow, from data cleaning and exploratory analysis to statistical analysis, machine learning, model evaluation, and communicating insights.

---

## Projects Overview

| No. | Project | Type | Primary Focus |
|---|---|---|---|
| 1 | Unemployment Analysis in India | Data Analysis | Impact of COVID-19 on India's labour market |
| 2 | Car Price Prediction | Machine Learning | Predicting used-car selling prices |

---

# 1. Unemployment Analysis in India

## Project Overview

This project analyzes the impact of the COVID-19 pandemic on unemployment in India.

The analysis uses unemployment, estimated employment, and labour-force participation data across Indian regions to compare labour-market conditions before and during the initial COVID-19 period.

The objective was to quantify the magnitude of the shock, identify regional differences, compare rural and urban labour markets, and examine the early recovery following the peak of the disruption.

### Dataset Scope

- 740 valid observations
- 28 Indian regions
- May 2019 – June 2020
- Monthly observations
- Rural and urban labour-market data
- 536 pre-COVID observations
- 204 COVID-period observations

## Key Findings

### Unemployment increased by 86.9%

Average unemployment increased from:

9.51% to 17.77%

This represents:

- 8.26 percentage-point increase
- 86.9% relative increase

The monthly unemployment rate reached a peak of 24.88% in May 2020, compared with 9.96% in February 2020.

### Employment declined by 12.7%

Average estimated employment decreased from approximately:

7.47 million to 6.52 million

This represents an estimated reduction of:

948,825 employed persons (-12.7%)

### Labour-force participation declined

Average labour-force participation decreased from:

43.89% to 39.33%

This represents a 4.56 percentage-point decline.

### Rural vs Urban

Rural unemployment:

- Pre-COVID: 8.09%
- COVID: 16.18%
- Increase: 8.09 percentage points
- Relative increase: 99.9%

Urban unemployment:

- Pre-COVID: 10.84%
- COVID: 19.28%
- Increase: 8.43 percentage points
- Relative increase: 77.8%

Although urban unemployment was higher in absolute terms, rural unemployment almost doubled relative to its baseline.

### Regional Impact

The COVID-period increase in unemployment varied substantially across regions.

| Region | Increase |
|---|---:|
| Puducherry | +37.36 pp |
| Tamil Nadu | +22.57 pp |
| Jharkhand | +22.07 pp |
| Bihar | +17.80 pp |
| Karnataka | +12.05 pp |

Puducherry recorded the largest observed increase, with unemployment rising from 1.59% to 38.96%.

### Early Recovery

Monthly unemployment:

| Month | Unemployment |
|---|---:|
| February 2020 | 9.96% |
| March 2020 | 10.70% |
| April 2020 | 23.64% |
| May 2020 | 24.88% |
| June 2020 | 11.90% |

From the May peak to June, unemployment declined by 12.98 percentage points, representing approximately a 52.2% reduction from the May peak.

### Statistical Analysis

A Welch two-sample t-test produced:

- t-statistic: -7.52
- p-value: 1.10 × 10⁻¹²

This provides strong statistical evidence of a difference between the pre-COVID and COVID-period unemployment observations under the test specification.

Note: This is evidence of a period difference, not proof of causality. The data contain repeated regional and time observations, so a panel-based model would provide stronger causal inference.

### Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- SciPy
- Jupyter Notebook

View project:

[Unemployment Analysis in India](./Project-1-Unemployment-Analysis-India/)

---

# 2. Car Price Prediction

## Project Overview

This project develops a machine learning regression model to predict used-car selling prices based on vehicle characteristics.

The project demonstrates an end-to-end supervised machine learning workflow, including data cleaning, exploratory analysis, feature engineering, model comparison, cross-validation, hyperparameter optimization, and model evaluation.

### Dataset Scope

After data cleaning:

- 299 observations
- 9 variables
- 2 duplicate records removed

### Features

The model uses vehicle characteristics including:

- Present price
- Driven kilometres
- Fuel type
- Selling type
- Transmission
- Previous owners
- Car age

A new car age feature was engineered from the vehicle year.

## Models Evaluated

Four regression algorithms were compared:

1. Linear Regression
2. Decision Tree Regressor
3. Random Forest Regressor
4. Gradient Boosting Regressor

## Model Performance

The initial test-set evaluation produced:

| Model | MAE | RMSE | R² |
|---|---:|---:|---:|
| Linear Regression | 1.473 | 2.525 | 0.753 |
| Decision Tree | 1.451 | 3.110 | 0.625 |
| Random Forest | 1.532 | 3.695 | 0.470 |
| Gradient Boosting | 1.125 | 2.515 | 0.755 |

### Best Initial Model

Gradient Boosting Regressor

Performance:

- MAE: 1.125
- RMSE: 2.515
- R²: 0.755

The model explained approximately 75.5% of the variation in the held-out test data.

## Cross-Validation

Five-fold cross-validation was used to assess model stability.

| Model | Mean CV RMSE |
|---|---:|
| Gradient Boosting | 1.431 |
| Random Forest | 1.668 |
| Linear Regression | 1.871 |
| Decision Tree | 1.894 |

Gradient Boosting produced the lowest mean cross-validation RMSE among the evaluated models.

## Hyperparameter Optimization

RandomizedSearchCV was used to optimize the Gradient Boosting model.

The search evaluated:

- 30 parameter combinations
- 5-fold cross-validation

The optimized model achieved a best cross-validation RMSE of approximately 1.217.

The final tuned model achieved:

- MAE: 1.191
- RMSE: 2.614
- R²: 0.735

## Feature Importance

Feature importance analysis showed that Present Price and Car Age accounted for approximately 97% of total feature importance.

This indicates that these two variables dominated the predictive decisions of the fitted model.

## Machine Learning Workflow

```text
Raw Dataset
     ↓
Data Quality Checks
     ↓
Duplicate Removal
     ↓
Data Cleaning
     ↓
Exploratory Data Analysis
     ↓
Feature Engineering
     ↓
Train/Test Split
     ↓
Categorical Encoding
     ↓
Model Training
     ↓
Cross-Validation
     ↓
Hyperparameter Optimization
     ↓
Model Evaluation
     ↓
Feature Importance
     ↓
Prediction

# Executive Summary — Car Price Prediction Model

## Project Overview

This project developed a supervised machine learning regression solution for predicting used-car selling prices from vehicle characteristics.

The objective was to determine whether historical vehicle attributes could provide a reliable basis for automated price estimation and to identify the machine learning algorithm that offered the strongest predictive performance.

The project followed an end-to-end workflow covering data preparation, exploratory analysis, feature engineering, model benchmarking, cross-validation, hyperparameter optimization, model diagnostics, feature importance analysis, and model serialization.

## Dataset and Approach

After cleaning, the modelling dataset contained **299 observations across 9 variables**, with **2 duplicate records removed**.

Key predictors included:

- Present Price
- Driven Kilometres
- Fuel Type
- Selling Type
- Transmission
- Previous Owners
- Car Age

The vehicle-age variable was engineered from the original vehicle year.

An **80/20 train-test split** with `random_state=42` was used, while categorical variables were processed using `OneHotEncoder`.

## Model Benchmarking

Four regression algorithms were evaluated:

- Linear Regression
- Decision Tree Regressor
- Random Forest Regressor
- Gradient Boosting Regressor

Gradient Boosting produced the strongest initial test-set performance:

| Metric | Result |
|---|---:|
| MAE | 1.125 |
| RMSE | 2.515 |
| R² | 0.755 |

The **R² of 0.755** indicates that approximately **75.5% of the variation in selling price was explained** by the model on the held-out test data.

## Model Validation

Five-fold cross-validation was used to evaluate model stability.

Gradient Boosting achieved the lowest mean CV RMSE:

**1.431**

compared with:

- Random Forest: 1.668
- Linear Regression: 1.871
- Decision Tree: 1.894

This provided additional evidence that Gradient Boosting was the strongest candidate among the evaluated algorithms.

## Hyperparameter Optimization

`RandomizedSearchCV` evaluated **30 parameter combinations using 5-fold cross-validation**.

The best cross-validation RMSE improved to approximately:

**1.217**

However, on the independent test set, the tuned model produced:

- MAE: 1.191
- RMSE: 2.614
- R²: 0.735

The result demonstrates an important ML engineering principle: a better cross-validation score does not necessarily guarantee better performance on a particular unseen test set.

## Feature Importance

Feature importance analysis revealed that **Present Price and Car Age together represented approximately 97% of total feature importance**.

This indicates that these variables dominated the predictions of the fitted Gradient Boosting model.

The result should be interpreted as model-specific predictive importance rather than causal influence.

## Model Diagnostics

The model demonstrated a positive relationship between actual and predicted selling prices.

Prediction accuracy was generally stronger for lower- and mid-priced vehicles, while some higher-priced vehicles produced larger errors.

Residuals were generally concentrated around zero, although some larger positive and negative errors were observed.

## Key Quantifiable Outcomes

- **299** modelling observations
- **2** duplicate records removed
- **4** regression algorithms benchmarked
- **5-fold** cross-validation
- **30** hyperparameter combinations evaluated
- **0.755** initial test R²
- **2.515** initial test RMSE
- **1.431** mean CV RMSE
- **~1.217** best tuned CV RMSE
- **0.735** tuned model test R²
- **~97%** combined feature importance from Present Price and Car Age
- **6.77** predicted selling price for the demonstrated sample vehicle

## Business Interpretation

The model demonstrates the potential for machine learning to support automated vehicle valuation and pricing decisions.

Potential applications include:

- Used-car pricing
- Inventory acquisition
- Vehicle valuation
- Marketplace price recommendations
- Customer-facing price estimates
- Automated pricing systems

The model should currently be considered a **proof-of-concept and baseline predictive system**, rather than a production pricing engine, because of the relatively small dataset and limited feature coverage.

## Limitations

The primary limitations are:

- Small modelling dataset of 299 observations
- Limited vehicle attributes
- Absence of brand/model information
- Absence of vehicle-condition information
- Absence of location and market-demand variables
- Larger errors for some higher-priced vehicles
- Sensitivity to a single train-test split
- Limited evidence for generalization beyond the source dataset

## Recommended Next Steps

1. Expand the dataset substantially.
2. Add brand, model, location, condition, service history, and accident history.
3. Apply repeated or nested cross-validation.
4. Investigate outliers and high-value vehicles separately.
5. Test additional ensemble and stacking approaches.
6. Apply SHAP or similar explainability techniques.
7. Build an API for inference.
8. Develop a Streamlit front-end.
9. Containerize the application.
10. Monitor prediction accuracy and model drift after deployment.

## Executive Conclusion

The project successfully demonstrates the development of an end-to-end machine learning regression pipeline for used-car price prediction.

**Gradient Boosting was the strongest initial model**, achieving an R² of **0.755**, RMSE of **2.515**, and MAE of **1.125** on the held-out test set.

Its mean 5-fold cross-validation RMSE of **1.431** further supported its selection as the strongest candidate among the four evaluated algorithms.

Hyperparameter optimization improved cross-validation performance to approximately **1.217 RMSE**, although the tuned model produced a lower independent test R² of **0.735**.

The strongest model signal came from **Present Price and Car Age**, which together accounted for approximately **97% of feature importance**.

From an ML engineering perspective, the project demonstrates the complete progression from data preparation to model persistence and provides a strong foundation for future deployment.

The principal opportunity for improvement is not simply changing the algorithm, but **improving the quality, size, and breadth of the training data**.

## Author

**Lawrence Ngukusuk**

Data Science Intern | Aspiring Data Scientist | Machine Learning Practitioner

**Internship:** CodeAlpha Data Science Internship

**Primary Language:** Python

**Core Technologies:** Pandas | NumPy | Matplotlib | Seaborn | Scikit-learn | Joblib | Jupyter Notebook

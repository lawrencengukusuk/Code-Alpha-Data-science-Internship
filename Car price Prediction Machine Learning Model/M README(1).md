# Car Price Prediction Using Machine Learning

## Overview

This project develops an end-to-end supervised machine learning solution for predicting used-car selling prices from vehicle characteristics.

The objective was to determine whether historical vehicle attributes could be used to estimate selling prices accurately enough to support data-driven vehicle valuation and pricing decisions.

The project implements a complete machine learning workflow covering data quality assessment, data cleaning, exploratory data analysis, feature engineering, categorical encoding, model benchmarking, cross-validation, hyperparameter optimization, test-set evaluation, residual analysis, feature importance, and model serialization.

The project was developed as part of the CodeAlpha Data Science Internship and demonstrates practical application of machine learning engineering and data science principles.

## Business Problem

Used-car pricing depends on multiple factors, including the vehicle's current value, age, mileage, fuel type, transmission, ownership history, and selling channel.

Manual pricing can introduce subjectivity and inconsistency.

The objective of this project is therefore to build a regression model that can estimate a vehicle's selling price from observable characteristics.

The model is intended as a decision-support tool rather than a replacement for professional vehicle valuation.

## Project Objectives

- Build a supervised regression model for used-car price prediction.
- Compare multiple machine learning algorithms.
- Quantify predictive performance using MAE, RMSE, MSE, and R².
- Evaluate model stability using 5-fold cross-validation.
- Optimize the strongest candidate model using hyperparameter search.
- Identify the variables contributing most strongly to predictions.
- Analyse residuals and prediction errors.
- Serialize the trained model for future inference.

## Dataset

After data cleaning, the final modelling dataset contained:

- 299 observations
- 9 variables
- 2 duplicate records removed

The model uses vehicle characteristics including Present Price, Driven Kilometres, Fuel Type, Selling Type, Transmission, Previous Owners, and Car Age.

A `car_age` feature was engineered from the vehicle year to provide the model with an explicit measure of vehicle age.

## Machine Learning Pipeline

Data Quality Assessment → Duplicate Removal → Data Cleaning → Exploratory Data Analysis → Feature Engineering → Train/Test Split → Categorical Encoding → Model Training → Model Comparison → 5-Fold Cross-Validation → Hyperparameter Optimization → Test Evaluation → Residual Analysis → Feature Importance → Model Serialization

An 80/20 train-test split was used with `random_state=42`.

Categorical variables were transformed using `OneHotEncoder` within the modelling pipeline.

## Models Evaluated

1. Linear Regression
2. Decision Tree Regressor
3. Random Forest Regressor
4. Gradient Boosting Regressor

## Model Performance

| Model | MAE | RMSE | R² |
|---|---:|---:|---:|
| Linear Regression | 1.473 | 2.525 | 0.753 |
| Decision Tree | 1.451 | 3.110 | 0.625 |
| Random Forest | 1.532 | 3.695 | 0.470 |
| Gradient Boosting | 1.125 | 2.515 | 0.755 |

Gradient Boosting produced the strongest initial test-set performance.

Best initial model:

- MAE: 1.125
- RMSE: 2.515
- R²: 0.755

An R² of 0.755 indicates that approximately 75.5% of the variation in selling price was explained by the model on the held-out test set.

## Cross-Validation

Five-fold cross-validation was used to evaluate model stability.

| Model | Mean CV RMSE |
|---|---:|
| Gradient Boosting | 1.431 |
| Random Forest | 1.668 |
| Linear Regression | 1.871 |
| Decision Tree | 1.894 |

Gradient Boosting achieved the lowest mean cross-validation RMSE at 1.431.

## Hyperparameter Optimization

The Gradient Boosting model was optimized using `RandomizedSearchCV`.

The tuning configuration included:

- 30 parameter combinations
- 5-fold cross-validation
- RMSE as the optimization metric

Best cross-validation RMSE: approximately 1.217.

The tuned model produced:

| Metric | Result |
|---|---:|
| MAE | 1.191 |
| MSE | 6.831 |
| RMSE | 2.614 |
| R² | 0.735 |

The tuned model achieved improved cross-validation performance, but its single held-out test performance was slightly weaker than the initial Gradient Boosting model.

This demonstrates why both cross-validation and independent test-set evaluation are important when selecting a machine learning model.

## Model Selection

The initial Gradient Boosting model was the strongest performer on the held-out test set:

- Highest R²: 0.755
- Lowest MAE: 1.125
- Lowest RMSE among the evaluated models: 2.515
- Best mean CV RMSE: 1.431

Gradient Boosting was therefore identified as the strongest overall candidate from the evaluated algorithms.

## Feature Importance

Feature importance analysis revealed that Present Price and Car Age together accounted for approximately 97% of total feature importance.

This indicates that these two variables dominated the predictive decisions of the fitted Gradient Boosting model.

Other variables, including Driven Kilometres, Fuel Type, Selling Type, Transmission, and Previous Owners, contributed substantially less.

Feature importance describes model-specific predictive contribution and should not be interpreted as causal influence.

## Model Diagnostics

Actual-versus-predicted analysis showed a positive relationship between observed and predicted selling prices.

The model generally performed better for lower- and mid-priced vehicles, while some higher-priced vehicles produced larger prediction errors.

Residual analysis showed that most residuals were concentrated around zero, although larger positive and negative residuals were observed.

This suggests that higher-priced vehicles and potential outliers were more difficult for the model to predict accurately.

## Example Prediction

A sample vehicle was passed through the trained model:

| Feature | Value |
|---|---:|
| Present Price | 8.5 |
| Driven Kilometres | 25,000 |
| Fuel Type | Petrol |
| Selling Type | Dealer |
| Transmission | Manual |
| Previous Owners | 0 |
| Car Age | 5 years |

Predicted selling price: approximately **6.77**.

## Model Serialization

The trained model was serialized using Joblib so that it can be reused for future predictions without retraining the entire pipeline.

Saved model:

`car_price_prediction_model.pkl`

## Key Quantitative Results

| KPI | Result |
|---|---:|
| Final observations | 299 |
| Duplicate records removed | 2 |
| Regression models evaluated | 4 |
| Train/Test Split | 80/20 |
| Cross-validation folds | 5 |
| Hyperparameter combinations | 30 |
| Best initial test R² | 0.755 |
| Best initial test MAE | 1.125 |
| Best initial test RMSE | 2.515 |
| Best mean CV RMSE | 1.431 |
| Best tuned CV RMSE | ~1.217 |
| Tuned model test R² | 0.735 |
| Tuned model test RMSE | 2.614 |
| Dominant feature importance | ~97% |
| Dominant features | Present Price + Car Age |

## Technical Stack

### Programming Language

Python

### Data Manipulation

- Pandas
- NumPy

### Data Visualization

- Matplotlib
- Seaborn

### Machine Learning

- Scikit-learn

### Model Persistence

- Joblib

### Development Environment

- Jupyter Notebook

## Machine Learning Skills Demonstrated

- Supervised learning
- Regression modelling
- Data cleaning
- Exploratory data analysis
- Feature engineering
- Categorical encoding
- Train-test splitting
- Model benchmarking
- Cross-validation
- Hyperparameter optimization
- Performance evaluation
- Feature importance analysis
- Residual analysis
- Model serialization
- Reproducible machine learning workflows

## Engineering Considerations

### Reproducibility

A fixed random state of 42 was used for the train-test split.

### Preprocessing Pipeline

Categorical preprocessing was incorporated into the machine learning workflow using `OneHotEncoder`.

### Model Benchmarking

Multiple algorithms were evaluated instead of assuming that one model would perform best.

### Cross-Validation

5-fold cross-validation was used to reduce dependence on a single validation split.

### Hyperparameter Optimization

`RandomizedSearchCV` was used to search across 30 parameter combinations.

### Model Persistence

The trained model was serialized with Joblib for future inference.

## Limitations

- The final dataset contains only 299 observations.
- The relatively small sample size limits generalization.
- The dataset does not include potentially important variables such as vehicle brand, specific model, geographic location, vehicle condition, accident history, service history, or market demand.
- A single 80/20 train-test split can produce performance estimates that vary depending on the partition.
- Some higher-priced vehicles generated larger prediction errors.
- Feature importance represents predictive contribution within the fitted model and should not be interpreted as causal influence.
- Performance may differ in other markets, regions, time periods, or vehicle populations.

## Future Improvements

- Increase the training dataset size.
- Add vehicle brand and model.
- Incorporate geographic information.
- Add vehicle condition.
- Include accident and service history.
- Incorporate market demand indicators.
- Investigate influential outliers.
- Apply repeated cross-validation.
- Test additional ensemble models.
- Explore stacking and blending.
- Perform advanced feature engineering.
- Apply SHAP or similar explainability techniques.
- Build a Streamlit prediction interface.
- Develop a REST API.
- Containerize the model with Docker.
- Deploy the model to a cloud platform.
- Implement model monitoring and drift detection.

## Business Value

A reliable vehicle price prediction system could support:

- Used-car dealerships
- Vehicle marketplaces
- Automotive pricing teams
- Buyers and sellers
- Vehicle valuation services
- Inventory management
- Automated pricing systems

Potential applications include estimating fair selling prices, supporting inventory acquisition decisions, identifying potentially underpriced vehicles, and providing automated price estimates to customers.

Production use would require additional validation on larger and more representative datasets.

## Conclusion

This project demonstrates a complete machine learning workflow for used-car price prediction, moving beyond simple model training to include benchmarking, validation, optimization, diagnostics, interpretation, and model persistence.

Four regression algorithms were evaluated, with Gradient Boosting achieving the strongest initial test performance at an R² of 0.755 and RMSE of 2.515.

The model also achieved the strongest 5-fold cross-validation performance, with a mean RMSE of 1.431.

Hyperparameter optimization produced a best cross-validation RMSE of approximately 1.217, although the tuned model's independent test R² decreased to 0.735. This result demonstrates the importance of evaluating both cross-validation and independent test performance when selecting a production candidate.

Feature importance analysis showed that Present Price and Car Age accounted for approximately 97% of total feature importance, highlighting the dominance of these variables in the fitted model.

Overall, the project demonstrates practical capability in:

Data Preparation → Feature Engineering → Model Development → Model Benchmarking → Cross-Validation → Hyperparameter Optimization → Model Diagnostics → Interpretation → Model Serialization

The current model provides a strong baseline for used-car price prediction, while the identified limitations provide clear opportunities for further model and data improvements.

## Repository Structure

```text
Car-Price-Prediction/
│
├── README.md
├── EXECUTIVE_SUMMARY.md
├── car_price_prediction.ipynb
├── car_price_prediction_model.pkl
├── data/
│   └── car_data.csv
│
└── images/
    ├── price_distribution.png
    ├── correlation_heatmap.png
    ├── model_comparison.png
    ├── actual_vs_predicted.png
    └── feature_importance.png
```

## Author

**Lawrence Ngukusuk**

Data Science Intern | Aspiring Data Scientist | Machine Learning Practitioner

**Internship:** CodeAlpha Data Science Internship

**Primary Language:** Python

**Core Technologies:** Pandas | NumPy | Matplotlib | Seaborn | Scikit-learn | Joblib | Jupyter Notebook

## Portfolio Statement

This project represents practical application of machine learning engineering principles to a real-world regression problem.

It demonstrates the ability to move from raw data to a validated predictive model while considering predictive performance, model stability, interpretability, limitations, reproducibility, and future deployment requirements.

**Author: Lawrence Ngukusuk**

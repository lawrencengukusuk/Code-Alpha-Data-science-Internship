# Car Price Prediction Using Machine Learning

## Overview

This project develops an end-to-end supervised machine learning solution for predicting used-car selling prices from vehicle characteristics.

The objective was to determine whether historical vehicle attributes could be used to estimate selling prices accurately enough to support data-driven vehicle valuation and pricing decisions.

Rather than focusing only on model training, the project implements a complete machine learning workflow covering data quality assessment, data cleaning, exploratory data analysis, feature engineering, categorical encoding, model benchmarking, cross-validation, hyperparameter optimization, test-set evaluation, residual analysis, feature importance, and model serialization.

The project was developed as part of the CodeAlpha Data Science Internship and demonstrates practical application of machine learning engineering and data science principles.

---

## Business Problem

Used-car pricing depends on multiple factors, including the vehicle's current value, age, mileage, fuel type, transmission, ownership history, and selling channel.

Manual pricing can introduce subjectivity and inconsistency.

The objective of this project is therefore to build a regression model that can estimate a vehicle's selling price from observable characteristics.

The model is intended as a decision-support tool rather than a replacement for professional vehicle valuation.

---

## Project Objectives

The project was designed to:

- Build a supervised regression model for used-car price prediction.
- Compare multiple machine learning algorithms.
- Quantify predictive performance using MAE, RMSE, MSE, and R².
- Evaluate model stability using 5-fold cross-validation.
- Optimize the strongest candidate model using hyperparameter search.
- Identify the variables contributing most strongly to predictions.
- Analyse residuals and prediction errors.
- Serialize the trained model for future inference.

---

## Dataset

After data cleaning, the final modelling dataset contained:

- 299 observations
- 9 variables
- 2 duplicate records removed

The model uses vehicle characteristics including:

- Present Price
- Driven Kilometres
- Fuel Type
- Selling Type
- Transmission
- Previous Owners
- Car Age

A `car_age` feature was engineered from the vehicle year to provide the model with an explicit measure of vehicle age. :contentReference[oaicite:2]{index=2}

---

## Machine Learning Pipeline

The project follows the following end-to-end pipeline:

Data Quality Assessment
→ Duplicate Removal
→ Data Cleaning
→ Exploratory Data Analysis
→ Feature Engineering
→ Train/Test Split
→ Categorical Encoding
→ Model Training
→ Model Comparison
→ 5-Fold Cross-Validation
→ Hyperparameter Optimization
→ Test Evaluation
→ Residual Analysis
→ Feature Importance
→ Model Serialization

An 80/20 train-test split was used with `random_state=42`.

Categorical variables were transformed using `OneHotEncoder` within the modelling pipeline. :contentReference[oaicite:3]{index=3}

---

## Models Evaluated

Four regression algorithms were benchmarked:

1. Linear Regression
2. Decision Tree Regressor
3. Random Forest Regressor
4. Gradient Boosting Regressor

The models were evaluated using:

- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)
- R² Score

---

## Model Performance

### Initial Test-Set Results

| Model | MAE | RMSE | R² |
|---|---:|---:|---:|
| Linear Regression | 1.473 | 2.525 | 0.753 |
| Decision Tree | 1.451 | 3.110 | 0.625 |
| Random Forest | 1.532 | 3.695 | 0.470 |
| Gradient Boosting | 1.125 | 2.515 | 0.755 |

Gradient Boosting produced the strongest initial test-set performance.

### Best Initial Model

**Algorithm:** Gradient Boosting Regressor

**MAE:** 1.125

**RMSE:** 2.515

**R²:** 0.755

The R² score of 0.755 indicates that approximately 75.5% of the variation in selling price was explained by the model on the held-out test set. :contentReference[oaicite:4]{index=4}

---

## Cross-Validation

To evaluate model stability beyond a single train-test split, 5-fold cross-validation was performed.

| Model | Mean CV RMSE |
|---|---:|
| Gradient Boosting | 1.431 |
| Random Forest | 1.668 |
| Linear Regression | 1.871 |
| Decision Tree | 1.894 |

Gradient Boosting achieved the lowest mean cross-validation RMSE at **1.431**, making it the strongest candidate based on cross-validated performance. :contentReference[oaicite:5]{index=5}

---

## Hyperparameter Optimization

The Gradient Boosting model was further optimized using `RandomizedSearchCV`.

The tuning configuration included:

- 30 parameter combinations
- 5-fold cross-validation
- RMSE as the optimization metric

The best cross-validation RMSE obtained during hyperparameter search was approximately:

**1.217**

The tuned model produced the following independent test-set results:

| Metric | Tuned Gradient Boosting |
|---|---:|
| MAE | 1.191 |
| MSE | 6.831 |
| RMSE | 2.614 |
| R² | 0.735 |

The tuned model achieved a cross-validation improvement, but its single held-out test-set performance was slightly weaker than the initial Gradient Boosting model. :contentReference[oaicite:6]{index=6}

This is an important modelling observation: optimization should not be judged solely by the best cross-validation score. Independent test-set performance remains essential for estimating generalization.

---

## Model Selection

The initial Gradient Boosting model was the strongest performer on the held-out test set:

- Highest R²: 0.755
- Lowest MAE: 1.125
- Lowest RMSE among the evaluated models: 2.515

It also achieved the best 5-fold cross-validation RMSE:

**1.431**

Therefore, Gradient Boosting was identified as the strongest overall candidate from the evaluated algorithms. :contentReference[oaicite:7]{index=7}

---

## Feature Importance

Feature importance analysis revealed a strong concentration of predictive information in two variables.

**Present Price + Car Age accounted for approximately 97% of total feature importance.**

This means these two variables dominated the predictive decisions of the fitted Gradient Boosting model.

Other variables, including:

- Driven Kilometres
- Fuel Type
- Selling Type
- Transmission
- Previous Owners

contributed substantially less to the model's overall feature importance. :contentReference[oaicite:8]{index=8}

### Important Interpretation

Feature importance describes how strongly variables contribute to the predictions of this specific model.

It does **not** establish that these variables causally determine vehicle prices.

---

## Model Diagnostics

Actual-versus-predicted analysis showed a positive relationship between observed and predicted selling prices.

The model generally performed better for lower- and mid-priced vehicles, while some higher-priced vehicles produced larger prediction errors.

Residual analysis showed that most residuals were concentrated around zero, although larger positive and negative residuals were present.

This indicates that higher-priced vehicles and potential outliers were more difficult for the model to predict accurately. :contentReference[oaicite:9]{index=9}

---

## Example Prediction

A sample vehicle was passed through the trained model using the following characteristics:

| Feature | Value |
|---|---:|
| Present Price | 8.5 |
| Driven Kilometres | 25,000 |
| Fuel Type | Petrol |
| Selling Type | Dealer |
| Transmission | Manual |
| Previous Owners | 0 |
| Car Age | 5 years |

The model generated an estimated selling price of approximately:

**6.77**

This demonstrates how the trained pipeline can be used for individual vehicle predictions. :contentReference[oaicite:10]{index=10}

---

## Model Serialization

The trained model was serialized using Joblib so that it can be reused for future predictions without retraining the entire pipeline.

Saved model:

`car_price_prediction_model.pkl`

This makes the project suitable for future integration into an application, API, or deployment workflow. :contentReference[oaicite:11]{index=11}

---

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

---

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

The project uses Python together with Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn, Joblib, and Jupyter Notebook. :contentReference[oaicite:12]{index=12}

---

## Machine Learning Skills Demonstrated

This project demonstrates practical experience in:

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

---

## Engineering Considerations

From an ML engineering perspective, several practices were incorporated into the workflow:

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

The final trained model was serialized with Joblib for future inference.

---

## Limitations

The model should be interpreted within the limitations of the dataset and modelling approach.

### 1. Small Dataset

The final dataset contains only 299 observations. This limits the statistical power and generalizability of the model.

### 2. Limited Feature Coverage

The dataset does not include potentially important variables such as:

- Vehicle brand
- Specific vehicle model
- Geographic location
- Vehicle condition
- Accident history
- Service history
- Market demand

These variables could improve predictive performance. :contentReference[oaicite:13]{index=13}

### 3. Test-Set Sensitivity

A single 80/20 train-test split can produce performance estimates that vary depending on the partition.

### 4. Higher-Priced Vehicles

The model produced larger errors for some higher-priced vehicles, suggesting potential limitations in modelling the upper end of the price distribution.

### 5. Feature Importance

The approximately 97% importance attributed to Present Price and Car Age is model-specific and should not be interpreted as causal evidence.

### 6. Market Generalization

Because the model was developed from a single dataset, performance may differ when applied to other markets, regions, time periods, or vehicle populations.

---

## Future Improvements

Future iterations of the project could improve the model by:

- Increasing the training dataset size
- Adding vehicle brand and model
- Incorporating geographic information
- Adding vehicle condition
- Including accident and service history
- Incorporating market demand indicators
- Investigating influential outliers
- Applying repeated cross-validation
- Testing additional ensemble models
- Exploring stacking and blending
- Performing more advanced feature engineering
- Using explainable AI techniques such as SHAP
- Building a Streamlit prediction interface
- Developing a REST API
- Containerizing the model with Docker
- Deploying the model to a cloud platform
- Implementing model monitoring and drift detection

---

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

However, production use would require additional validation on larger and more representative datasets.

---

## Conclusion

This project demonstrates a complete machine learning workflow for used-car price prediction, moving beyond simple model training to include benchmarking, validation, optimization, diagnostics, interpretation, and model persistence.

Four regression algorithms were evaluated, with Gradient Boosting achieving the strongest initial test performance at an R² of **0.755** and RMSE of **2.515**.

The model also achieved the strongest 5-fold cross-validation performance, with a mean RMSE of **1.431**.

Hyperparameter optimization produced a best cross-validation RMSE of approximately **1.217**, although the tuned model's independent test R² decreased to **0.735**. This result demonstrates the importance of evaluating both cross-validation and independent test performance when selecting a production candidate.

Feature importance analysis showed that **Present Price and Car Age accounted for approximately 97% of total feature importance**, highlighting the dominance of these variables in the fitted model.

Overall, the project demonstrates practical capability in:

**Data Preparation → Feature Engineering → Model Development → Model Benchmarking → Cross-Validation → Hyperparameter Optimization → Model Diagnostics → Interpretation → Model Serialization**

The current model provides a strong baseline for used-car price prediction, while the identified limitations provide clear opportunities for further model and data improvements.

---

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

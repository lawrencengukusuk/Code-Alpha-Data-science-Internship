# CodeAlpha Data Science Internship Portfolio

## Data Science Projects

This repository contains the data science projects completed by Lawrence Ngukusuk during the CodeAlpha Data Science Internship.

The portfolio demonstrates practical experience in data analysis, exploratory data analysis, statistical analysis, data visualization, feature engineering, supervised machine learning, model comparison, cross-validation, hyperparameter optimization, model evaluation, and data-driven problem solving.

The internship portfolio contains two real-world data science projects:

1. Unemployment Analysis in India
2. Car Price Prediction Using Machine Learning

Together, these projects demonstrate an end-to-end data science workflow, from problem definition and data preparation to exploratory analysis, statistical analysis, machine learning, model evaluation, interpretation, and communication of actionable insights.

---

# Portfolio Overview

| Project | Domain | Problem Type | Dataset Scope | Key Result |
|---|---|---|---|---|
| Unemployment Analysis in India | Economics / Labour Market | Exploratory & Statistical Analysis | 740 observations across 28 regions | Average unemployment increased by 86.9% during the COVID period |
| Car Price Prediction | Automotive / Machine Learning | Supervised Regression | 299 cleaned observations | Gradient Boosting achieved an initial R² of 0.755 |

---

# Project 1: Unemployment Analysis in India

## Project Overview

The objective of this project was to investigate and quantify the impact of the COVID-19 period on unemployment and labour-market conditions in India.

The analysis examined unemployment rate, estimated employment, and labour-force participation across Indian regions. It compared labour-market conditions before and during the initial COVID-19 period and investigated differences between rural and urban areas, regional variations, the peak of the unemployment shock, and the early recovery.

The project focused on transforming raw labour-market data into measurable insights that could explain the scale and distribution of the employment shock.

## Key Questions

The analysis was designed to answer the following questions:

- How much did unemployment change during the COVID period?
- How did estimated employment change?
- Did labour-force participation decline?
- How did rural and urban areas respond differently?
- Which regions experienced the largest increases in unemployment?
- When did unemployment reach its peak?
- How quickly did the labour market begin to recover?
- Is there statistical evidence of a difference between the pre-COVID and COVID periods?

## Dataset

The dataset contains monthly labour-market observations from May 2019 to June 2020.

Dataset characteristics:

- 740 valid observations
- 28 Indian regions
- 536 pre-COVID observations
- 204 COVID-period observations
- 359 rural observations
- 381 urban observations
- Monthly observations

Key variables include:

- Region
- Date
- Area
- Estimated Unemployment Rate
- Estimated Employed
- Estimated Labour Participation Rate

For this analysis, March 2020 onward was classified as the COVID period.

## Methodology

The project followed a structured analytical workflow:

Data Collection → Data Cleaning → Data Validation → Exploratory Data Analysis → Time-Series Analysis → Pre-COVID vs COVID Comparison → Rural vs Urban Analysis → Regional Analysis → Outlier Analysis → Correlation Analysis → Statistical Testing → Interpretation

The analysis included:

- Data quality assessment
- Data cleaning
- Data type conversion
- Date transformation
- Descriptive statistics
- Exploratory data analysis
- Monthly trend analysis
- Pre-COVID versus COVID comparison
- Rural versus urban segmentation
- Regional comparison
- Correlation analysis
- Outlier detection using the IQR method
- Data visualization
- Welch two-sample t-test

## Key Findings

### Unemployment Increased by 86.9%

Average unemployment increased from 9.51% before COVID-19 to 17.77% during the COVID period.

This represents:

- An increase of 8.26 percentage points
- An 86.9% relative increase

The monthly unemployment rate reached a peak of 24.88% in May 2020 compared with 9.96% in February 2020.

Therefore, the May 2020 unemployment rate was approximately 2.5 times the February 2020 level.

### Estimated Employment Declined by 12.7%

Average estimated employment decreased from approximately 7.47 million to 6.52 million.

This represents an estimated reduction of approximately 948,825 employed persons, equivalent to a 12.7% decline.

### Labour-Force Participation Declined

Average labour-force participation decreased from 43.89% to 39.33%.

This represents a decline of 4.56 percentage points.

The result indicates that the labour-market disruption extended beyond unemployment and was also associated with reduced labour-force participation.

## Rural vs Urban Analysis

Rural unemployment increased from 8.09% before COVID-19 to 16.18% during the COVID period.

This represents:

- An increase of 8.09 percentage points
- A relative increase of approximately 99.9%

Urban unemployment increased from 10.84% to 19.28%.

This represents:

- An increase of 8.43 percentage points
- A relative increase of approximately 77.8%

The analysis shows that urban areas experienced higher unemployment in absolute terms, while rural unemployment experienced a larger relative increase compared with its pre-COVID baseline.

## Regional Impact

The COVID-period impact varied considerably across Indian regions.

| Region | Increase in Average Unemployment |
|---|---:|
| Puducherry | +37.36 percentage points |
| Tamil Nadu | +22.57 percentage points |
| Jharkhand | +22.07 percentage points |
| Bihar | +17.80 percentage points |
| Karnataka | +12.05 percentage points |

Puducherry recorded the largest observed increase, with unemployment rising from 1.59% to 38.96%, representing a 37.36 percentage-point increase.

This demonstrates that the labour-market shock was not uniform across India.

## Monthly Unemployment and Early Recovery

| Month | Unemployment Rate |
|---|---:|
| February 2020 | 9.96% |
| March 2020 | 10.70% |
| April 2020 | 23.64% |
| May 2020 | 24.88% |
| June 2020 | 11.90% |

Unemployment increased sharply between March and April 2020 and reached its peak in May 2020.

Between May and June 2020, unemployment declined by 12.98 percentage points.

This represents approximately a 52.2% reduction from the May peak.

However, the June 2020 unemployment rate remained above the February 2020 pre-COVID level.

## Statistical Testing

A Welch two-sample t-test was conducted to compare unemployment observations between the pre-COVID and COVID periods.

Results:

- t-statistic: -7.52
- p-value: 1.10 × 10⁻¹²

The very small p-value provides strong statistical evidence of a difference between unemployment observations in the two periods under the test specification.

However, statistical significance should not be interpreted as proof of causality.

The dataset contains repeated observations across regions, areas, and time. A panel-data approach would provide a stronger framework for controlling for regional and temporal effects.

## Key Insights

The unemployment analysis identified several measurable labour-market effects:

- Average unemployment increased by 86.9%.
- Unemployment increased by 8.26 percentage points.
- Estimated employment declined by 12.7%.
- Approximately 948,825 fewer estimated employed persons were recorded on average.
- Labour-force participation declined by 4.56 percentage points.
- Rural unemployment increased by approximately 99.9% relative to its baseline.
- Puducherry recorded the largest regional increase at 37.36 percentage points.
- Unemployment reached a peak of 24.88% in May 2020.
- Unemployment declined by 12.98 percentage points between May and June 2020.

## Conclusion

The analysis indicates that the initial COVID-19 period was associated with a substantial disruption to India's labour market.

Average unemployment increased by 86.9%, while estimated employment declined by 12.7% and labour-force participation decreased by 4.56 percentage points.

The impact was also uneven across geographic and demographic segments. Rural unemployment almost doubled relative to its pre-COVID baseline, while several regions experienced exceptionally large increases in unemployment.

The sharp decline from the May 2020 peak to June 2020 suggests an early labour-market recovery, although unemployment remained above the pre-COVID level.

Overall, the project demonstrates how exploratory data analysis and statistical techniques can be used to quantify large-scale economic changes, identify regional differences, and communicate labour-market trends using measurable evidence.

## Limitations

The unemployment analysis has several limitations:

- The dataset ends in June 2020 and therefore captures only the initial COVID-19 shock and early recovery.
- The analysis is primarily descriptive and does not establish a causal relationship between COVID-19 and unemployment.
- The repeated regional and time structure of the dataset means that observations may not be fully independent.
- The statistical test does not explicitly control for lockdown intensity, industry composition, migration, seasonality, or other potential confounding factors.
- Correlation results should not be interpreted as causal relationships.

A future study could use fixed-effects panel regression, Difference-in-Differences, or other panel-data techniques to provide stronger causal inference.

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- SciPy
- Jupyter Notebook

---

# Project 2: Car Price Prediction Using Machine Learning

## Project Overview

The objective of this project was to develop a supervised machine learning regression model capable of predicting used-car selling prices based on vehicle characteristics.

The project followed an end-to-end machine learning workflow covering data cleaning, exploratory data analysis, feature engineering, model development, model comparison, cross-validation, hyperparameter optimization, test-set evaluation, residual analysis, feature importance, and model serialization.

## Key Questions

The project was designed to answer the following questions:

- Which regression algorithm performs best?
- How accurately can selling price be predicted?
- Which vehicle characteristics are most important for prediction?
- How stable is model performance across different data splits?
- Can hyperparameter optimization improve model performance?
- What types of vehicles generate larger prediction errors?

## Dataset

After data cleaning, the final modelling dataset contained:

- 299 observations
- 9 variables
- 2 duplicate records removed

The model used vehicle characteristics including:

- Present price
- Driven kilometres
- Fuel type
- Selling type
- Transmission
- Previous owners
- Car age

A new `car_age` feature was engineered from the vehicle year.

## Methodology

The machine learning workflow followed these stages:

Data Quality Assessment → Duplicate Removal → Data Cleaning → Exploratory Data Analysis → Feature Engineering → Train/Test Split → Categorical Encoding → Model Training → Model Comparison → 5-Fold Cross-Validation → Hyperparameter Optimization → Test Evaluation → Residual Analysis → Feature Importance → Model Serialization

The dataset was split into training and test sets using an 80/20 split with a fixed random state of 42.

Categorical variables were encoded using OneHotEncoder and incorporated into the modelling pipeline.

## Models Evaluated

Four regression algorithms were evaluated:

1. Linear Regression
2. Decision Tree Regressor
3. Random Forest Regressor
4. Gradient Boosting Regressor

## Initial Model Performance

| Model | MAE | RMSE | R² |
|---|---:|---:|---:|
| Linear Regression | 1.473 | 2.525 | 0.753 |
| Decision Tree | 1.451 | 3.110 | 0.625 |
| Random Forest | 1.532 | 3.695 | 0.470 |
| Gradient Boosting | 1.125 | 2.515 | 0.755 |

Gradient Boosting achieved the strongest initial test-set performance.

Performance:

- MAE: 1.125
- RMSE: 2.515
- R²: 0.755

An R² of 0.755 indicates that approximately 75.5% of the variation in selling price was explained by the model on the held-out test data.

## Cross-Validation

Five-fold cross-validation was used to assess model stability across different training and validation partitions.

| Model | Mean CV RMSE |
|---|---:|
| Gradient Boosting | 1.431 |
| Random Forest | 1.668 |
| Linear Regression | 1.871 |
| Decision Tree | 1.894 |

Gradient Boosting produced the lowest mean cross-validation RMSE among the evaluated algorithms.

## Hyperparameter Optimization

RandomizedSearchCV was used to optimize the Gradient Boosting model.

The tuning process evaluated:

- 30 parameter combinations
- 5-fold cross-validation
- RMSE as the optimization metric

The best cross-validation RMSE obtained during the search was approximately 1.217.

The tuned model achieved:

| Metric | Result |
|---|---:|
| MAE | 1.191 |
| MSE | 6.831 |
| RMSE | 2.614 |
| R² | 0.735 |

The tuned model explained approximately 73.5% of the variation in the held-out test data.

An important modelling observation is that hyperparameter optimization improved cross-validation performance while producing slightly weaker performance on the single held-out test set than the initial Gradient Boosting model.

This demonstrates why both cross-validation and independent test-set evaluation are important when selecting a machine learning model.

## Feature Importance

Feature importance analysis showed that Present Price and Car Age together accounted for approximately 97% of total feature importance.

This indicates that these two variables dominated the predictive decisions of the fitted Gradient Boosting model.

Other variables, including fuel type, transmission, selling type, previous ownership, and driven kilometres, contributed substantially less to the fitted model.

Feature importance represents model-specific predictive contribution and should not be interpreted as causal influence.

## Model Diagnostics

The actual-versus-predicted analysis showed a positive relationship between actual and predicted selling prices.

The model generally performed better for lower- and mid-priced vehicles but produced larger errors for some higher-priced vehicles.

Residual analysis showed that most residuals were concentrated around zero, although some larger positive and negative residuals were observed.

This suggests that higher-priced vehicles and potential outliers were more difficult for the model to predict accurately.

## Example Prediction

A sample vehicle with the following characteristics was supplied to the trained model:

- Present price: 8.5
- Driven kilometres: 25,000
- Fuel type: Petrol
- Selling type: Dealer
- Transmission: Manual
- Previous owners: 0
- Car age: 5 years

The model generated a predicted selling price of approximately 6.77.

## Model Serialization

The trained model was serialized using Joblib so that it could be reused for future predictions without retraining the complete workflow.

Saved model:

`car_price_prediction_model.pkl`

## Key Insights

The car price prediction project produced several measurable findings:

- 299 cleaned vehicle observations were used.
- Four regression algorithms were evaluated.
- Gradient Boosting achieved the strongest initial test R² of 0.755.
- Initial Gradient Boosting RMSE was 2.515.
- Five-fold cross-validation produced a mean RMSE of 1.431.
- Hyperparameter optimization achieved a best cross-validation RMSE of approximately 1.217.
- Present Price and Car Age accounted for approximately 97% of feature importance.
- Prediction errors were larger for some higher-priced vehicles.
- The relatively small dataset limits the generalizability of the model.

## Conclusion

The machine learning analysis demonstrated that Gradient Boosting provided the strongest initial predictive performance among the four evaluated algorithms.

The initial Gradient Boosting model achieved an R² of 0.755, indicating that approximately 75.5% of the variation in selling price was explained on the held-out test data.

Five-fold cross-validation further supported Gradient Boosting as the strongest candidate, producing a mean RMSE of 1.431.

Hyperparameter optimization improved cross-validation performance, although the tuned model achieved a slightly lower R² of 0.735 on the independent test set. This highlights the importance of evaluating model performance using multiple validation approaches.

Feature importance analysis showed that Present Price and Car Age dominated the predictive process, together accounting for approximately 97% of total feature importance.

Overall, the project demonstrates a complete machine learning workflow from data preparation through model development, evaluation, interpretation, and serialization.

## Limitations

The machine learning project has several limitations:

- The final dataset contains only 299 observations.
- The relatively small sample size limits generalization to the wider used-car market.
- The model is based on a single dataset and may not perform similarly in other markets or time periods.
- A single 80/20 train-test split can produce performance estimates that vary depending on the random partition.
- Some higher-priced vehicles generated larger prediction errors.
- The dataset does not include potentially important variables such as vehicle brand, specific model, location, vehicle condition, accident history, service history, or market demand.
- Feature importance represents predictive contribution within the fitted model and should not be interpreted as causal influence.

## Future Improvements

Potential improvements include:

- Increasing the size of the training dataset
- Adding vehicle brand and model information
- Incorporating location and market conditions
- Adding vehicle condition and service history
- Investigating influential outliers
- Testing additional regression algorithms
- Applying repeated cross-validation
- Exploring ensemble and stacking methods
- Performing more extensive feature engineering
- Building a Streamlit prediction application
- Deploying the model through an API
- Monitoring model performance after deployment

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Joblib
- Jupyter Notebook

---

# Combined Technical Skills Demonstrated

These projects demonstrate practical experience across the complete data science lifecycle.

## Data Analysis

- Data cleaning
- Data quality validation
- Exploratory data analysis
- Descriptive statistics
- Time-series analysis
- Regional segmentation
- Rural versus urban analysis
- Correlation analysis
- Outlier detection
- Statistical hypothesis testing
- Data visualization
- Quantitative interpretation

## Machine Learning

- Supervised learning
- Regression modelling
- Feature engineering
- Categorical encoding
- Model comparison
- Train-test splitting
- Cross-validation
- Hyperparameter optimization
- Model evaluation
- Feature importance
- Residual analysis
- Model serialization

## Analytical Thinking

- Problem definition
- Research question development
- KPI identification
- Quantitative comparison
- Pattern identification
- Statistical interpretation
- Model interpretation
- Limitation assessment
- Business-oriented insight generation

---

# Portfolio Highlights

## Unemployment Analysis

- 740 labour-market observations analysed
- 28 Indian regions examined
- 86.9% increase in average unemployment quantified
- 8.26 percentage-point increase in unemployment identified
- 12.7% decline in estimated employment quantified
- Approximately 948,825 decline in average estimated employment
- 4.56 percentage-point decline in labour-force participation identified
- 99.9% relative increase in rural unemployment identified
- 37.36 percentage-point maximum regional increase identified
- 24.88% unemployment peak recorded in May 2020
- 12.98 percentage-point decline recorded between May and June 2020
- Welch t-test p-value of 1.10 × 10⁻¹²

## Car Price Prediction

- 299 cleaned vehicle observations modelled
- 4 regression algorithms compared
- 5-fold cross-validation applied
- 30 hyperparameter combinations evaluated
- 0.755 initial test R² achieved
- 2.515 initial test RMSE achieved
- 1.431 mean cross-validation RMSE achieved
- Approximately 1.217 best cross-validation RMSE achieved during hyperparameter tuning
- Approximately 97% of feature importance attributed to Present Price and Car Age

---

# Overall Methodology

Both projects followed a structured data science approach:

Problem Definition → Data Collection → Data Cleaning → Exploratory Data Analysis → Feature Engineering → Statistical / Machine Learning Analysis → Model Evaluation → Interpretation → Communication

The methodology was adapted according to the problem type.

The unemployment project focused on descriptive statistics, trend analysis, segmentation, regional comparisons, and statistical testing.

The car-price project focused on supervised learning, regression model comparison, cross-validation, hyperparameter optimization, feature importance, and predictive evaluation.

---

# Business and Analytical Value

The unemployment project demonstrates how data can be used to quantify the magnitude and distribution of a major economic shock.

The analysis provides measurable indicators of unemployment growth, employment decline, reduced labour-force participation, regional differences, rural/urban differences, and early recovery.

The car-price project demonstrates how machine learning can be used to support pricing and valuation decisions.

The model provides a quantitative approach to estimating selling prices from vehicle characteristics and identifies the variables that contribute most strongly to the predictions.

Together, the projects demonstrate the ability to connect technical analysis with practical questions and measurable outcomes.

---

# Overall Conclusion

The CodeAlpha Data Science Internship provided practical experience in applying data science methods to both descriptive and predictive problems.

The Unemployment Analysis project demonstrated the ability to investigate a real-world economic problem, clean and explore labour-market data, quantify changes using statistical measures, identify regional and rural/urban patterns, conduct hypothesis testing, and communicate findings through data-driven insights.

The Car Price Prediction project demonstrated the ability to develop a complete machine learning pipeline, compare multiple regression algorithms, evaluate predictive performance, apply cross-validation, perform hyperparameter optimization, interpret feature importance, analyse residuals, and save a trained model for future use.

Together, the projects demonstrate complementary data science capabilities in:

- Descriptive analytics
- Exploratory data analysis
- Statistical analysis
- Time-series analysis
- Data visualization
- Feature engineering
- Machine learning
- Predictive modelling
- Model evaluation
- Hyperparameter tuning
- Statistical interpretation
- Business-oriented insight generation
- Professional technical communication

The overall workflow demonstrated across this portfolio can be summarized as:

Problem Definition → Data Preparation → Exploratory Analysis → Feature Engineering → Statistical / Machine Learning Modelling → Evaluation → Interpretation → Business Insight → Communication

These projects represent practical application of data science techniques and form an important part of my developing professional data science portfolio.

---

# Internship Learning Outcomes

Through these projects, I developed practical experience in:

- Translating real-world problems into analytical questions
- Working with structured datasets
- Cleaning and validating data
- Performing exploratory data analysis
- Identifying trends and patterns
- Quantifying business and economic impacts
- Conducting statistical hypothesis testing
- Building machine learning models
- Comparing competing algorithms
- Applying cross-validation
- Performing hyperparameter optimization
- Evaluating model performance
- Interpreting model outputs
- Identifying model limitations
- Communicating technical findings
- Structuring professional data science projects

---

# Repository Structure

```text
CodeAlpha-Data-Science-Internship/
│
├── README.md
│
├── Project-1-Unemployment-Analysis-India/
│   ├── README.md
│   ├── EXECUTIVE_SUMMARY.md
│   ├── unemployment_analysis.ipynb
│   ├── data/
│   └── images/
│
└── Project-2-Car-Price-Prediction/
    ├── README.md
    ├── car_price_prediction.ipynb
    ├── car_price_prediction_model.pkl
    ├── data/
    └── images/
```

---

# Internship Information

## Internship

CodeAlpha Data Science Internship

## Projects Completed

1. Unemployment Analysis in India
2. Car Price Prediction Using Machine Learning

## Primary Language

Python

## Core Technologies

Python | Pandas | NumPy | Matplotlib | Seaborn | SciPy | Scikit-learn | Joblib | Jupyter Notebook

---

# About the Author

## Lawrence Ngukusuk

Data Science Intern | Aspiring Data Scientist

Lawrence Ngukusuk is developing practical expertise in data analysis, machine learning, statistical modelling, data visualization, and data-driven decision making through hands-on projects involving real-world datasets.

This repository represents work completed during the CodeAlpha Data Science Internship and demonstrates the ability to transform raw data into measurable insights and predictive solutions.

The portfolio reflects a growing focus on applying analytical thinking, statistical reasoning, Python programming, and machine learning techniques to practical problems.

## Professional Interests

- Data Science
- Data Analytics
- Machine Learning
- Predictive Modelling
- Statistical Analysis
- Data Visualization
- Business Intelligence
- Data-Driven Decision Making

---

# Final Portfolio Summary

This repository demonstrates practical capability across both analytics and machine learning.

The Unemployment Analysis project shows the ability to investigate an economic question using data, quantify the magnitude of change, identify differences across regions and population segments, conduct statistical testing, and communicate findings.

The Car Price Prediction project shows the ability to build predictive models, compare algorithms, validate performance, tune model parameters, interpret feature importance, diagnose errors, and prepare a model for reuse.

The combination of these projects demonstrates a developing professional profile in:

- Data Analytics
- Data Science
- Statistical Analysis
- Machine Learning
- Predictive Modelling
- Python Programming
- Data Visualization
- Quantitative Problem Solving
- Business Intelligence
- Data-Driven Decision Making

---

# Thank You

Thank you for visiting this repository and reviewing my work.

This portfolio represents my practical learning and project experience during the CodeAlpha Data Science Internship.

**Author:** Lawrence Ngukusuk

**Role:** Data Science Intern | Aspiring Data Scientist

**Internship:** CodeAlpha Data Science Internship

**Primary Language:** Python

**Core Technologies:** Pandas, NumPy, Matplotlib, Seaborn, SciPy, Scikit-learn, Joblib, Jupyter Notebook

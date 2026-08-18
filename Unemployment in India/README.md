# Impact of COVID-19 on Unemployment in India

## Project Overview

This project analyzes how the COVID-19 shock and the associated economic restrictions affected India's labour market between **May 2019 and June 2020**. The analysis uses unemployment, estimated employment, and labour-force participation indicators to quantify the change between a pre-COVID baseline and the COVID period.

The project is designed as an end-to-end data analytics portfolio case study covering:

- Data cleaning and quality checks
- Exploratory data analysis (EDA)
- Time-series trend analysis
- Pre-COVID vs COVID comparison
- Rural vs urban analysis
- Regional/state-level impact analysis
- Recovery analysis
- Correlation analysis
- Statistical significance testing
- Outlier detection
- Creation of a cleaned analytical dataset

> **Important analytical note:** The notebook uses March 2020 onward as the COVID period. The available dataset ends in June 2020, so this analysis captures the **initial labour-market shock and early recovery**, not the full pandemic period. The results establish strong association with the COVID period but should not be interpreted as a fully causal estimate of COVID-19's effect.

---

## Business Question

**How materially did COVID-19 disrupt India's labour market, and which segments and regions experienced the greatest impact?**

The analysis focuses on four decision-oriented questions:

1. How did unemployment change after the COVID period began?
2. What happened to employment and labour-force participation?
3. Was the impact different between rural and urban areas?
4. Which regions experienced the largest deterioration and fastest early recovery?

---

## Dataset

The notebook works with the **Unemployment in India** dataset and analyzes **740 valid observations** after removing 28 completely empty rows.

### Coverage

| Metric | Value |
|---|---:|
| Observation period | May 2019 – June 2020 |
| Valid observations | 740 |
| Regions | 28 |
| Rural/Urban observations | 359 / 381 |
| Pre-COVID observations | 536 |
| COVID-period observations | 204 |
| Frequency | Monthly |

### Core variables

- `Region` — Indian state/region
- `Date` — observation date
- `Frequency` — data frequency
- `Estimated Unemployment Rate (%)`
- `Estimated Employed`
- `Estimated Labour Participation Rate (%)`
- `Area` — Rural or Urban

### Analytical variables created

- `COVID_Period`
- `Year`
- `Month`
- `Month_Name`
- `Year_Month`
- `Pre_COVID_Regional_Avg`
- `COVID_Deviation`

---

## Methodology

### 1. Data quality and preparation

The analysis:

- Inspected the dataset structure and data types.
- Identified **28 completely empty rows** and removed them.
- Confirmed **0 duplicate rows** after cleaning.
- Standardized column names and categorical values using whitespace trimming.
- Converted `Date` to a proper datetime format.
- Sorted observations by region, area, and date.
- Created a binary analytical period:
  - **Pre-COVID:** before March 2020
  - **COVID:** March 2020 onward

### 2. Descriptive and time-series analysis

Monthly averages were calculated for:

- Unemployment rate
- Estimated employment
- Labour participation rate

This provides a national-level view of the labour-market shock and the subsequent early recovery.

### 3. Pre-COVID vs COVID comparison

The notebook compares period averages and calculates:

- Absolute change
- Percentage change
- Regional COVID deviation from each region's pre-COVID average

### 4. Rural vs Urban analysis

The same indicators are segmented by `Area` to identify whether the shock was materially different across rural and urban labour markets.

### 5. Regional impact analysis

For each region, the analysis calculates:

`COVID average unemployment - Pre-COVID average unemployment`

This creates a comparable **COVID impact measure in percentage points** and supports regional ranking.

### 6. Recovery analysis

April 2020 unemployment is compared with June 2020 unemployment to quantify the early recovery:

`April unemployment - June unemployment`

A larger positive value indicates a larger decline in unemployment between the two months.

### 7. Correlation analysis

Pearson correlations were calculated among:

- Unemployment rate
- Estimated employment
- Labour participation rate

### 8. Statistical test

A Welch two-sample t-test was applied to compare unemployment observations between the pre-COVID and COVID periods.

Result:

- **t-statistic:** -7.52
- **p-value:** 1.10 × 10⁻¹²

The result is statistically significant under the notebook's test specification.

### 9. Outlier analysis

The IQR rule was used to identify unusually high or low unemployment observations.

The analysis identified **35 outlier observations**, with the highest values concentrated around the April-May 2020 shock.

---

# Key Findings

## 1. COVID-19 produced a major unemployment shock

The average unemployment rate increased from:

**9.51% pre-COVID → 17.77% during the COVID period**

That represents:

- **+8.26 percentage points**
- **+86.9% relative increase**

The monthly peak in the available national series occurred in **May 2020 at 24.88%**, up from **9.96% in February 2020**.

This means the observed monthly unemployment rate was approximately **2.5× the February level** at the May peak.

---

## 2. Employment contracted materially

Average estimated employment declined from approximately:

**7.47 million → 6.52 million**

Equivalent to:

- **-948,825 estimated employed persons**
- **-12.7%**

At the monthly level, estimated employment fell to approximately **5.28 million in April 2020**, before recovering to **7.39 million by June 2020** in the dataset.

---

## 3. Labour-force participation also weakened

Average labour-force participation fell from:

**43.89% → 39.33%**

A decline of:

**-4.56 percentage points**

The monthly series reached **35.14% in April 2020**, compared with **43.72% in February 2020**.

This matters because the shock was not simply an increase in unemployment: participation in the labour market also contracted.

---

## 4. Urban unemployment was higher, but rural unemployment nearly doubled

### Rural

- Pre-COVID unemployment: **8.09%**
- COVID-period unemployment: **16.18%**
- Change: **+8.09 percentage points**
- Relative increase: **+99.9%**

### Urban

- Pre-COVID unemployment: **10.84%**
- COVID-period unemployment: **19.28%**
- Change: **+8.43 percentage points**
- Relative increase: **+77.8%**

Urban areas maintained the higher unemployment rate in absolute terms, while rural areas experienced the larger **relative increase**.

This is an important portfolio insight: looking only at absolute unemployment levels would miss the scale of the rural deterioration.

---

## 5. The shock was highly uneven across regions

The largest average increases in unemployment during the COVID period were:

| Rank | Region | Pre-COVID | COVID | Change |
|---:|---|---:|---:|---:|
| 1 | Puducherry | 1.59% | 38.96% | **+37.36 pp** |
| 2 | Tamil Nadu | 2.84% | 25.40% | **+22.57 pp** |
| 3 | Jharkhand | 14.28% | 36.35% | **+22.07 pp** |
| 4 | Bihar | 13.83% | 31.63% | **+17.80 pp** |
| 5 | Karnataka | 3.23% | 15.28% | **+12.05 pp** |
| 6 | Haryana | 22.94% | 34.65% | **+11.72 pp** |
| 7 | Kerala | 6.99% | 17.95% | **+10.96 pp** |
| 8 | Telangana | 4.66% | 15.44% | **+10.79 pp** |
| 9 | Madhya Pradesh | 4.74% | 14.07% | **+9.33 pp** |
| 10 | Andhra Pradesh | 5.04% | 13.58% | **+8.54 pp** |

Puducherry stands out as the largest observed deterioration, with a **37.36 percentage-point** increase.

---

## 6. Some regions showed smaller or negative changes

The smallest COVID-period changes were observed in:

- Jammu & Kashmir: **-4.33 pp**
- Tripura: **-2.31 pp**
- Himachal Pradesh: **-2.06 pp**
- Chandigarh: **-2.00 pp**
- Assam: **+0.21 pp**

These results demonstrate that the national shock was **not homogeneous across regions**.

A negative change should not automatically be interpreted as an economic improvement caused by COVID-19; it may reflect baseline differences, local labour-market structure, measurement variation, or the short observation window.

---

## 7. The labour market showed an early recovery

The national monthly unemployment series moved:

- February 2020: **9.96%**
- March 2020: **10.70%**
- April 2020: **23.64%**
- May 2020: **24.88%**
- June 2020: **11.90%**

The decline from the May peak to June was:

**-12.98 percentage points**, or approximately **52.2%** relative to the May peak.

The recovery was therefore rapid, although June unemployment remained above the February pre-COVID level.

---

## 8. Regional recovery was also uneven

From April to June 2020, the largest observed unemployment reductions included:

| Region | April | June | Reduction |
|---|---:|---:|---:|
| Puducherry | 75.62% | 4.55% | **71.08 pp** |
| Tamil Nadu | 49.37% | 13.49% | **35.88 pp** |
| Bihar | 51.93% | 16.47% | **35.46 pp** |
| Jharkhand | 51.60% | 20.45% | **31.14 pp** |
| Andhra Pradesh | 24.29% | 3.35% | **20.94 pp** |

This suggests that the initial labour-market shock was severe but, in several regions, partially reversible as economic activity resumed.

---

## 9. Correlations were weak

The observed correlations were:

| Variables | Correlation |
|---|---:|
| Unemployment vs Employment | **-0.22** |
| Unemployment vs Labour Participation | **0.00** |
| Employment vs Labour Participation | **0.01** |

The negative unemployment-employment relationship is directionally intuitive but relatively weak.

The low correlations indicate that the three indicators did not move in a simple one-to-one relationship across the full dataset and that other regional, structural, seasonal, or measurement factors likely contributed to observed variation.

---

## 10. Statistical evidence supports a period difference

The Welch t-test produced:

- **t = -7.52**
- **p = 1.10 × 10⁻¹²**

This provides strong statistical evidence that the unemployment observations in the two periods differ under the assumptions of the test.

However, statistical significance should **not** be confused with causal identification. The notebook's test treats individual observations as independent, while the dataset contains repeated measurements across regions, areas, and dates. A stronger inferential design would use panel methods that explicitly account for this structure.

---

# Portfolio-Level Business Insights

### Insight 1 — COVID-19 created a severe but short-lived labour-market shock

Unemployment rose by **8.26 percentage points**, an **86.9% increase** in the period comparison, while monthly unemployment peaked at **24.88%** in May 2020.

### Insight 2 — Employment and participation both deteriorated

Estimated employment fell **12.7%**, while labour participation fell **4.56 percentage points**. This indicates a broader labour-market contraction rather than unemployment alone.

### Insight 3 — Rural and urban markets experienced different forms of stress

Urban unemployment was higher, but rural unemployment almost **doubled** relative to its pre-COVID baseline.

### Insight 4 — Regional targeting matters

The COVID impact ranged from **-4.33 pp to +37.36 pp** across regions. A single national unemployment statistic therefore hides substantial geographic variation.

### Insight 5 — Recovery was rapid but incomplete

Unemployment fell from **24.88% in May to 11.90% in June**, but June remained above the **9.96% February** level.

---

# Recommendations

From a business and policy analytics perspective, the findings suggest:

1. **Target labour-market interventions geographically.** Regions with large unemployment deviations require different support intensity from regions with relatively stable rates.
2. **Track rural and urban labour markets separately.** The near-doubling of rural unemployment demonstrates why national averages can conceal material segment-level shocks.
3. **Monitor participation as well as unemployment.** A fall in participation can mask labour-market distress because people leaving the labour force may no longer be counted as unemployed.
4. **Use recovery indicators alongside shock indicators.** Measuring the April-to-June change shows that the speed of recovery can vary substantially by region.
5. **Build a stronger panel model for causal analysis.** Future work should control for region and time effects and test whether changes persist after accounting for pre-existing regional differences.

---

# Limitations

This project is intentionally an exploratory/portfolio analytics study rather than a causal econometric evaluation.

### Key limitations

- The dataset ends in **June 2020**, so it captures the initial shock and early recovery only.
- The COVID period is defined mechanically as **March 2020 onward**.
- The dataset contains repeated regional and area observations, so a simple t-test does not fully account for panel dependence.
- The analysis does not control for confounding factors such as sector mix, state-level restrictions, migration, seasonality, or regional economic structure.
- The correlation analysis is descriptive and does not establish causation.
- Extremely high observations are retained rather than automatically removed because they may represent genuine pandemic-period shocks.
- The employment figures are treated as the dataset's estimated employment measure and should not be interpreted as a precise count of unique jobs lost.

---

# Recommended Next Steps

For a stronger version of the project:

- Add a **Difference-in-Differences** framework where an appropriate treatment/control design can be justified.
- Use **fixed-effects panel regression** by region and month.
- Add sector-level indicators such as manufacturing, construction, agriculture, and services.
- Extend the dataset beyond June 2020 to measure the full recovery path.
- Compare India with other major emerging economies.
- Build an interactive **Power BI/Tableau dashboard** showing national, regional, rural/urban, and recovery KPIs.
- Add confidence intervals and robustness checks.

---

# Tools & Technologies

- **Python**
- **Pandas** — data cleaning and aggregation
- **NumPy** — numerical operations
- **Matplotlib** — visualization
- **Seaborn** — statistical visualization
- **SciPy** — statistical testing
- **Jupyter Notebook** — analysis environment

---

# Project Structure

```text
.
├── Untitled-1.ipynb
├── cleaned_unemployment_india.csv
├── README.md
└── EXECUTIVE_SUMMARY.md
```

---

# How to Run

1. Clone/download the project.
2. Place the source unemployment dataset in the project directory.
3. Update the CSV path in the notebook if necessary.
4. Open `Untitled-1.ipynb` in Jupyter Notebook, JupyterLab, or VS Code.
5. Run the notebook from top to bottom.
6. The notebook produces the cleaned analytical dataset:
   `cleaned_unemployment_india.csv`

---

# Portfolio Positioning

**Project type:** Exploratory Data Analysis / Labour Market Analytics

**Business domain:** Economics, Workforce Analytics, Public Policy

**Primary analytical skills demonstrated:**

- Data cleaning
- Data quality validation
- Time-series analysis
- KPI design
- Segmentation
- Regional benchmarking
- Statistical testing
- Outlier analysis
- Business storytelling
- Analytical interpretation

### One-line portfolio summary

> **Quantified the initial COVID-19 labour-market shock in India, finding an 86.9% increase in average unemployment, a 12.7% decline in estimated employment, a 4.56-point fall in labour participation, and substantial regional variation in impact and recovery.**

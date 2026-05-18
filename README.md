# 🌴 Analyzing Date Price and Demand Patterns in Saudi Arabia 🌴

---

## Course Information
**Course:** DSA 210 – Introduction to Data Science (Spring 2026)  
**Student:** Can Kurt 

---

## Motivation

Having been born in Saudi Arabia, dates have always been a significant part of my diet. They are widely produced across the country and are recognized as a staple food rich in nutrients and dietary fiber. Dates hold considerable importance in Saudi Arabia’s agricultural, economic, and religious sectors due to their high quality and strong market demand. They are consumed daily, with particularly high demand during Ramadan, when they are traditionally used to break the fast.

Despite their importance, fluctuations in date prices are often attributed to general assumptions, such as seasonal harvest cycles or increased demand during religious periods. This project aims to move beyond these assumptions by analyzing the underlying factors through a data-driven approach.

---

## Research Question

---

To what extent does time, weather conditions, search interest, and production influence the supply and demand of dates in Saudi Arabia?

---

## Data Sources

---

This project integrates four heterogeneous datasets covering periods approximately between 2000 and 2025, enriched and aligned temporally:


### 1. Date Production & Prices (Saudi Arabia)

- **Source:** FAOSTAT (https://www.fao.org/faostat/) and Saudi General Authority for Statistics (https://www.stats.gov.sa/)
  
- **Frequency:** Yearly
  
- **Collection Method:** Downloaded from official databases
  
- **Preprocessing:**  
  - Converted prices to a common currency (USD where necessary)  
  - Handled missing and inconsistent values  
  - Aligned production and price data by year  


### 2. Weather Data (Saudi Arabia Regions)

- **Source:** Open-Meteo Historical Weather API (https://open-meteo.com/)
   
- **Frequency:** Daily
  
- **Features:**  
  - Temperature (max/min)  
  - Precipitation  
  - Humidity
    
- **Collection Method:** Python API requests with batching
  
- **Preprocessing:**  
  - Aggregated daily data into yearly averages  
  - Created seasonal indicators  
  - Aligned weather data with production timeline  


### 3. Google Trends

- **Keyword:** “تمر”, “dates Saudi”, “ajwa dates”
  
- **Region:** Saudi Arabia
  
- **Collection Tool:** pytrends
   
- **Methodology:**  
  - Normalized search interest values  
  - Aggregated weekly data into yearly averages  
  - Aligned with production and price data  


### 4. Seasonal & Religious Indicators

- **Source:** Public calendar data
  
- **Features:**  
  - Ramadan periods  
  - Harvest season (approx. August–October)
    
- **Usage:** Capturing demand spikes during Ramadan
  
- **Preprocessing:**  
  - Created binary variables for Ramadan periods  
  - Added seasonal indicators for harvest cycles  

---

## Data Analysis Pipeline

---

### 1. Data Preparation

- Handled missing values  
  - Missing production values were filled using interpolation when necessary  
  - Consistent time ranges were formatted across all datasets  

- Data alignment  
  - Production, Google Trends, and seasonal indicators were aligned by (year) period 

- Data normalization  
  - Standard variables from data were normalized   


### 2. Exploratory Data Analysis (EDA)

EDA focused on understanding long-term trends and seasonal effects:

- Time series analysis  
  - Date production was analyzed over time  
  - Long-term growth patterns were identified

- Seasonal analysis  
  - Production across different periods were compared
  - Patterns around Ramadan and harvest seasons were examined

- Demand analysis   
  - Google Trends data was analyzed as a proxy for demand  
  - Spikes in search interest was observed during key periods  

- Output  
  - All figures were stored in the figure directory  

### 3. Feature Engineering

Constructed explanatory variables, including:

- Seasonal indicators  
  - Harvest season (Aug–Oct)  
  - Off-season periods  

- Religious indicators  
  - Binary variable for Ramadan  

- Trend variables  
  - Year index to capture long-term growth  

- Data quality indicators  
  - Flags for missing or interpolated values
  
---

## Visualization and Storytelling

---

**Visualizations**

- Time series plots (production trends)
- Seasonal comparisons (harvest, Ramadan, off-season)
- Google Trends vs production
- Model results (predictions vs actual)

**Storytelling**

- Key trends and patterns were highlighted
- Seasonal and demand effects were explained
- Connections between results and real-world context displayed

---

## Tools & Environment

---

| Category | Tools |
|---|---|
| **Language** | Python 3.x |
| **Libraries** | pandas · numpy · matplotlib · seaborn · scikit-learn · scipy · statsmodels |
| **Environment** | Jupyter Notebook · Google Colab |
---

## Hypothesis Testing

---

The following hypotheses were evaluated using regression analysis, correlation tests, and two-sample t-tests.

| Hypothesis | Description | Result |
|---|---|---|
| H1 | Date production exhibits long-term growth patterns | Confirmed (R² = 0.705, p < 0.001) |
| H2 | Weather and seasonal variables influence production | Partially confirmed (R² = 0.782, year trend significant at p = 0.030) |
| H3 | Ramadan increases search interest for dates | Confirmed (t = 2.24, p = 0.0259) |
| H4 | Higher production reduces producer prices | Not confirmed (Spearman ρ = -0.276, p = 0.254) |
| H5 | Search interest reflects estimated demand trends | Confirmed (Pearson r = 0.833, p < 0.001) |

The hypothesis testing results suggest that production and demand patterns in the Saudi Arabian dates market are influenced more strongly by long-term trends, trade activity, and consumer search behavior than by yearly weather variables alone.

---

## Machine Learning Models

---

Two regression models were implemented to predict the log-transformed producer price of Saudi Arabian dates using supply, demand, weather, and lag variables.

### Model Setup
- Models:
  - Random Forest Regressor
  - Ridge Regression

- Validation Method:
  - Leave-One-Out Cross Validation (LOOCV)

- Feature Groups:
  - Supply variables
  - Demand variables
  - Weather variables
  - Lag variables

### Results

| Model Group | Best Model | R² | MAE |
|---|---|---|---|
| Supply | Random Forest | 0.274 | 0.079 |
| Demand | Random Forest | 0.305 | 0.084 |
| Weather | Ridge Regression | 0.026 | 0.099 |
| Lag | Random Forest | 0.030 | 0.102 |

Random Forest generally outperformed Ridge Regression, suggesting that the relationships between the variables and producer prices may be non-linear rather than purely linear.

Weather and lag feature groups showed relatively weak predictive performance compared to demand-related variables.

Feature importance analysis showed that year trend, export quantities, search interest, and previous-year producer prices were among the most influential predictors.

---

## Project Results

---

### Key Findings

1. **Saudi Arabian date production increased over time**  
   Regression analysis confirmed a significant long-term upward trend in production.

2. **Weather variables showed partial influence on production**  
   Weather-related variables improved the regression model, but not all weather variables were statistically significant.

3. **Ramadan increased search interest for dates**  
   The t-test showed significantly higher search interest during Ramadan periods.

4. **Search interest was strongly related to estimated demand**  
   Pearson correlation showed a strong positive relationship between Google Trends search interest and estimated demand.

5. **Demand variables were the strongest machine learning predictors**  
   The Demand feature group achieved the strongest Random Forest performance in predicting producer prices.

---

## Data Compatibility Justification

---

The datasets used in this project came from multiple sources with different formats and time frequencies. To ensure compatibility, all datasets were cleaned, normalized, and aligned into a common yearly format before merging. Daily weather data and weekly Google Trends data were aggregated into yearly indicators, while missing values and inconsistent column formats were handled during preprocessing.

---

## AI Assistance Disclosure

---

AI tools (Chatgpt, Claude, Gemini) were utilized for:

*Debugging and restructuring Python code
*Improving figure visualization and clarity
*Reviewing statistical interperatations from results
*Providing feedback on certain inconsistencies in the project
*Enhancing documentation and README file structure

---

## Limitations

---

- **Limited dataset size:**  
  Several analyses were conducted using yearly data, resulting in a relatively small number of observations for statistical testing and machine learning models.

- **Data availability differences:**  
  Some datasets covered different time ranges, which reduced the number of overlapping years available after merging.

- **Demand proxy limitation:**  
  Google Trends was used as a proxy for demand, reflecting public search interest rather than actual consumer purchases or consumption volumes.

- **Weather aggregation limitations:**  
  Daily weather data was aggregated into seasonal and yearly averages, which may not fully capture short-term extreme weather effects on date production.

- **Missing or incomplete agricultural records:**  
  Some FAOSTAT datasets contained missing years or multiple agricultural indicators, requiring filtering and preprocessing before analysis.

- **Model performance limitations:**  
  Some machine learning models produced weak predictive performance, suggesting that additional market, economic, or policy-related variables may influence producer prices.

- **Association vs. causation:**  
  The analyses identify statistical relationships between variables but do not establish direct causal effects.

- **Minor Coding Errors:**
  During preprocessing, several coding and formatting issues were encountered, such as inconsistent column names, missing values, and date-format problems. These were resolved through data cleaning and validation.
  
---

## Conclusion

---

This project analyzed how production, weather conditions, search interest, and trade-related variables influence the supply and demand dynamics of dates in Saudi Arabia between 2000 and 2025.

Statistical analysis showed that Saudi Arabian date production has experienced significant long-term growth over time. Ramadan periods were associated with significantly higher Google search interest, and search interest showed a strong positive relationship with estimated demand. However, production alone did not demonstrate a statistically significant relationship with producer prices.

Machine learning models further suggested that demand-related variables, such as export quantities and search interest, were stronger predictors of producer prices than weather variables alone. Random Forest models generally outperformed Ridge Regression, indicating that non-linear relationships may exist within the market.

Overall, the project demonstrated how combining agricultural, weather, trade, and public-interest data can provide valuable insights into the Saudi Arabian dates market and help better understand the factors influencing supply, demand, and producer prices.


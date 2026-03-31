# 🌴 Analyzing Date Price and Demand Patterns in Saudi Arabia 🌴

---

## Course Information
**Course:** DSA 210 – Introduction to Data Science (Spring 2026)  
**Student:** Can Kurt 

---

## Motivation

Having been born in Saudi Arabia, dates have always been a significant part of my diet. They are widely produced across the country and are recognized as a staple food rich in nutrients and dietary fiber. Dates hold considerable importance in Saudi Arabia’s agricultural, economic, and religious sectors due to their high quality and strong market demand. They are consumed daily, with particularly high demand during Ramadan, when they are traditionally used to break the fast.

Despite their importance, flucuations in date prices are often attributed to general assumptions, such as seasonal harvest cycles or increased demand during religous periods. This project aims to move beyond these assumptions by analyzing the underlying factors through a data-driven approach.

---

## Data Sources

This project integrates four heterogeneous datasets covering approximately 1999–2025, enriched and aligned temporally:


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
  - Missing production values will be filled using interpolation when necessary  
  - consistent time ranges will be formatted across all datasets  

- Data alignment  
  - Production, Google Trends, and seasonal indicators will aligned by (year) period 

- Data normalization  
  - Standard varibes from data will be normalized   


### 2. Exploratory Data Analysis (EDA)

EDA focused on understanding long-term trends and seasonal effects:

- Time series analysis  
  - Date production will be anlalyzed over time  
  - Long-term growth patterns will be identified

- Seasonal analysis  
  - Production across different periods will be compared
  - Patterns around Ramadan and harvest seasons will be examined

- Demand analysis   
  - Google Trends data will be analyzed as a proxy for demand  
  - Spikes in search interest will be observed during key periods  

- Output  
  - All figures will be stored in the figure directory  


### 3. Feature Engineering

Constructed explanatory variables including:

- Seasonal indicators  
  - Harvest season (Aug–Oct)  
  - Off-season periods  

- Religious indicators  
  - Binary variable for Ramadan  

- Trend variables  
  - Year index to capture long-term growth  

- Data quality indicators  
  - Flags for missing or interpolated values
  

### 4. Hypothesis Testing

The following hypotheses will be evaluated through ANOVA and Kruskal–Wallis:

- (H1) Date production exhibits long-term growth patterns
    
- (H2) Production varies across seasons and harvest periods
 
- (H3) Ramadan increases demand (Google Trends)
  
- (H4) Higher production reduces price pressure
  
- (H5) Search interest reflects demand trends
  

### 5. Machine Learning

**Models**

- Linear Regression (production prediction)
- Logistic Regression / Random Forest (classification)

**Targets**

- Predict production levels
- Classify periods (high vs low demand)

**Evaluation**

- Regression: R², MSE  
- Classification: Accuracy, Precision, Recall, F1, ROC-AUC

**Insights**

- Identifying key factors affecting production and demand


### 6. Visualization and Storytelling

**Visualizations**

- Time series plots (production trends)
- Seasonal comparisons (harvest, Ramadan, off-season)
- Google Trends vs production
- Model results (predictions vs actual)

**Storytelling**

- Key trends and patterns will be highlighted
- Seasonal and demand effects will be explained
- Connections between results and real-world context will be displayed

---

## Tools & Environment

---

| Category            | Tools                                                        |
| ------------------- | ------------------------------------------------------------ |
| **Language**        | Python 3.x                                                   |
| **Libraries**       | pandas · numpy · matplotlib · seaborn · scikit-learn · scipy |
| **Environment**     | Jupyter Notebook / Google Collab                                   |

---

## Hypotheses Testing

---

The following hypotheses were evaluated using statistical analysis and correlation tests:

| Hypothesis | Description | Result |
|------------|------------|--------|
| H1 | Date production exhibits long-term growth patterns | Partially Confirmed (F-test p = 0.095 > 0.05; weak positive relationship) |
| H2 | Production varies across seasons and harvest periods | Confirmed () |
| H3 | Ramadan increases demand (Google Trends) | Confirmed () |
| H4 | Higher production reduces price pressure | Partially confirmed () |
| H5 | Search interest reflects demand trends | Weak positive relationship |

---

## Machine Learning Models

---

## Expected Deliverables

---

- Data will be cleaned and merged dataset (production, trends, seasonal indicators)
  
- Jupyter notebooks & Google Collab (EDA, hypothesis testing, modeling)
  
- Visualizations (stored in plots & graphs)
  
- Final report summarizing insights, results, and limitations

---

## Data Compatibility Justification

---

Datasets (production, Google Trends, seasonal indicators) were aligned by year for consistency. Google Trends was used as a relative demand proxy, making it comparable over time. Normalization ensured variables are on similar scales, allowing reliable integration and analysis.

---

## Limitations

---

- **Geographic scope:** The analysis focuses on Saudi Arabia, so results may not generalize to other countries or regions.

- **Demand proxy:** Google Trends is used as a proxy for demand, which reflects search interest rather than actual consumption.

- **Data limitations:** Production data may contain missing or interpolated values, which can affect accuracy of the analysis.

- **Temporal alignment:** Differences in data frequency (e.g., yearly vs. seasonal patterns) may reduce precision for the study.

- **Association vs. causation:** The analysis identifies patterns and relationships but does not establish causal effects.

---

## Summary

---

- **Main Dataset:** Date production data (FAOSTAT / national statistics)
  
- **Enrichment Data:** Google Trends (demand proxy) + seasonal indicators (Ramadan, harvest periods)
  
- **Objective:** Analyze how production and demand vary over time and across seasonal and religious periods
  
- **Outcome:** Apply data science methods to identify patterns, test relationships, and evaluate the impact of seasonal and demand factors

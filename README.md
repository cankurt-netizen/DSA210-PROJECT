# Analyzing Date Price and Demand Patterns in Saudi Arabia

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
  - Filled missing production values using interpolation where necessary  
  - Ensured consistent time ranges across all datasets  

- Data alignment  
  - Aligned production, Google Trends, and seasonal indicators by year  

- Data normalization  
  - Standardized variables where needed (e.g., scaling Google Trends data)  


### 2. Exploratory Data Analysis (EDA)

EDA focused on understanding long-term trends and seasonal effects:

- Time series analysis  
  - Visualized date production trends over time  
  - Identified long-term growth patterns  

- Seasonal analysis  
  - Compared production across different periods  
  - Examined patterns around Ramadan and harvest seasons  

- Demand analysis  
  - Analyzed Google Trends data as a proxy for demand  
  - Observed spikes in search interest during key periods  

- Output  
  - All figures stored in the `figures/` directory  


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

---

## Hypothesis Testing

The following hypotheses were evaluated using statistical analysis and correlation tests:

| Hypothesis | Description | Result |
|------------|------------|--------|
| H1 | Date production exhibits long-term growth patterns | Confirmed (steady increase over time) |
| H2 | Production varies across seasons and harvest periods | Confirmed (clear seasonal patterns) |
| H3 | Ramadan increases demand (Google Trends) | Confirmed (significant spikes observed) |
| H4 | Higher production reduces price pressure | Partially confirmed (inverse relationship observed) |
| H5 | Search interest reflects demand trends | Weak positive relationship |


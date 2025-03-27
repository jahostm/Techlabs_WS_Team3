# 📈 Stock Market Trends & Earthquake Impact Analysis

**Predicting market behavior based on earthquake events.**

![Screen Recording](C:\Users\dongv\OneDrive\Desktop\Techlabs\Techlabs_WS_Team3\04_visualization\visualization-dashboard.gif)

## 🌟 Project Overview  

**Mission:** Analyze, visualize, and predict stock market trends influenced by major earthquake events to support investor decision-making.  

**Key Questions:**  
We received 16 datasets containing information about Stock market data (from 2008 to 2023) and Earthquake data (from 1990 to 2023). The key questions we want to solve are:
1. How do natural disasters impact markets (short/long term)?  
2. Which sectors/regions are most sensitive to earthquakes?  
3. How can investors leverage this model?  

---

## 👥 Team: 

-	Sohail Jannessari
-	Jan Hostmann
-	Anh Dong 

**Mentor:** Nopparat Wasikanon 

---

## 📅 Project Phases: 

**Project Duration:** 9 weeks (13/01/2025 – 16/03/2025) 

|     |             Description              |  Timeline  | Completion Date |
|:----|:-------------------------------------|:-----------|:----------------|
|  1  | Team and Project setup               |   Week 1   | ✅ 19/01/2025   |
|  2  | Exploratory Data Analysis (EDA)      |   Week 2   | ✅ 26/01/2025   |
|  3  | Data Cleanup & Analysis              |  Week 3-4  | ✅ 09/02/2025   |
|  4  | Problem Definition                   |  Week 5-6  | ✅ 23/02/2025   |
|  5  | Modelling & Evaluation               |  Week 7-8  | ✅ 09/03/2025   |
|  6  | Final Presentation prep, Submission  |   Week 9   | 🟡 16/03/2025   |

---

## 🛠️ Installation 
**Install required packages:** 
```
pip install pandas, numpy, statsmodels.api, geocoder, datetime, yfinance, matplotlib.pyplot, seaborn, requests, glob, dash, plotly, plotly.express, plotly.graph_objects
```
---

## 📂 Repository Structure

```
├── 01_data/
│   ├── 01_raw/          # Raw datasets (2008-2023)
│   ├── 02_pre/          # Processed data (e.g., clean_major_earthquakes.csv)
│   └── 03_additional/   # External data (yFinance/Google)
├── 02_code/
│   ├── 0_preprocess/    # Data prep notebooks
│   └── 1_analysis/      # Regression & market analysis
├── 03_documentation/
│   └── 01_regressions/  # Saved model outputs
├── 04_visualization/    # Visualization dashboard
└── README.md
```

##  🚀 How to Run this Project code

### Part 1: Regression Analysis
#### 1. Data Prep

Run these notebooks sequentially:
```
 1. 02_code/0_preprocess/01_preparation.ipynb (Filters earthquakes ≥6 magnitude)
    -> It limits the earthquakes to our stock market timespan, and a threshold of magnitude.
    -> Then it merges the stock market files and split the merged file into separate data sets for each market.

 2. 02_code/0_preprocess/02_create_regression_files.ipynb (Merges market/earthquake data)
    -> It uses additional information (close time, location, etc), and the earthquake and market data sets, to prepare data sets for running linear and logistic regressions.
    -> It summarizes the earthquakes equal or above the magnitude of 6 that happen between two closing time of each stock market, into number of these sort of earthquakes, maximum magnitude, maximum significance, minimum depth, and the closest distance between the location of these earthquakes to the location of a market.
    -> It also assigns values from 0 to 3 to each day for each market, based on the difference between the pecentage of change in one market and the average of all the markets, attempting to isolate the effect of earthquake (or a special event) that affect this one market and not the others.
    -> This 'effect' is assigned based on average and standard deviation of the change in markets, with three showing extreme divergence between a specific market and all the others.

```
#### 2. Modeling
```
 3. Linear Regression: 02_code/1_analysis/01_linear_reg.ipynb 
    -> It includes two blocks that run regressions.
    -> The second one tries to correct the first block for an error of missing values.
    -> The results are saved in separate text files.

 4. Multinomial Regression: 02_code/1_analysis/02_multinomial_reg.ipynb
    -> It also includes two blocks that run regressions.
    -> The second one tries to correct the first block for an error of missing values.
    -> The results are saved in separate text files under '03_documentation\01_regressions.

```

### Part 2: Market-Specific Analysis
 ```
 # Example for Japan (Nikkei 225):

1. Run 02_code/0_preprocess/03_N225_companies_stock.ipynb
    -> retrieve the csv file 01_data\02_pre\clean_major_earthquakes.csv (Filters earthquakes ≥6 magnitude)

2. Run 02_code/1_analysis/03_N225_and_major_earthquake.ipynb
    -> retrieve the csv file 01_data\03_additional\01_N225_Japan\N225_companies_stock.csv
    -> 01_data\03_additional\01_N225_Japan\N225_companies_stock.csv includes all 225 companies stock values (open, close, volume) of ^N225 (Nikkei 225, Japan Market)
    -> retrieve 3 pkl files (in 01_data\03_additional\01_N225_Japan) that are used in Dash visualization dashboard code (04_visualization\Final_Dashboard.ipynb).
 ```
 Repeat for other markets (N100, China, BSESN, NSEI).

  ### Part 3: Dashboard
 ```
1. Run 02_code/0_preprocess/nikkei_companies_adresses.ipynb
    -> to get the adresses of the companies that are shown on the map 
    -> retrieve the file 02_code\0_preprocess\nikkei_companies.pkl that is used in Dash visualization dashboard code (04_visualization\Final_Dashboard.ipynb)

2. Run 04_visualization\Heatmap_Japan_new.ipynb # Heatmap earthquakes in Japan

3. Launch Dash app (see dashboard code in 04_visualization\Final_Dashboard.ipynb)
 ```
 ---

## 🔑 Key Deliverables
**Regression Models:** Quantify earthquake impact on markets

**Market Analysis:** Analyze affected markets (Japan, EU, China, India)

**Interactive Dashboard:** Visualize geo map and market recovery timelines

---


## 🙏 Acknowlegments

Special thanks to Techlabs and our Mentor Nopparat Wasikanon for all the work that went through organizing this project and insights. 

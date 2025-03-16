# Techlabs_WS_Team3 - Stock Market Trends

Project Mission: to analyze, visualize and create a prediction model for Stock Market Trends based on Earthquake Event.

## Project Team: 

-	Sohail Jannessari
-	Jan Hostmann
-	Anh Dong 

## Project Phases: 

Project Duration: 9 weeks (13/01/2025 – 16/03/2025) 

|     |             Description              |  Timeline  | Completion Date |
|:----|:-------------------------------------|:-----------|:----------------|
|  1  | Team and Project setup               |   Week 1   |    19/01/2025   |
|  2  | Exploratory Data Analysis (EDA)      |   Week 2   |    26/01/2025   |
|  3  | Data Cleanup & Analysis              |  Week 3-4  |    09/02/2025   |
|  4  | Problem Definition                   |  Week 5-6  |    23/02/2025   |
|  5  | Modelling & Evaluation               |  Week 7-8  |    09/03/2025   |
|  6  | Final Presentation prep, Submission  |   Week 9   |    16/03/2025   |


## Abstract:  

We develop a prediction model for Stock Market Trends based on Global Events (in this case, Natural Disaster: Earthquake). Our model aims to show how earthquakes, especially major ones, impact global markets. By comparing earthquake data with stock market trends, we want to help investors, economists, and decision-makers understand how earthquakes may change market behavior. This will help them see risks/chances more clearly and make better decisions. 

## Overview:

We received 16 datasets containing information about Stock market data (from 2008 to 2023) and Earthquake data (from 1990 to 2023). 
The key questions we want to solve are: 
1.	How is the impact of natural disasters on the stock market - in the short and long term?
2.	Are there specific sectors (e.g., energy, real estate, insurance, ...) or regions that are more sensitive to earthquakes in terms of market performance?
3.	How can investors apply this model? 

## How to use/read this Project code? 
 
- Firstly, some libraries need to be installed: pandas, numpy, statsmodels.api, geocoder, datetime, yfinance, matplotlib.pyplot, seaborn, requests, glob, dash, plotly (plotly.express,plotly.graph_objects)
- Secondly, the data sources: 
    + Raw data (01_data\01_raw): ...
    + Additional data (01_data\03_additional): from yfinance and google (national stock exchange websites)

### Part 1: Regression Analysis
1. The file '02_code/0_preprocess/01_preparation.ipynb' does the basic preparations: It limits the earthquakes to our stock market timespan, and a threshold of magnitude. Then it merges the stock market files and split the merged file into separate data sets for each market.

2. The file '02_code/0_preprocess/02_create_regression_files.ipynb' uses additional information (close time, location, etc), and the earthquake and market data sets, to prepare data sets for running linear and logistic regressions. It summarizes the earthquakes equal or above the magnitude of 6 that happen between two closing time of each stock market, into number of these sort of earthquakes, maximum magnitude, maximum significance, minimum depth, and the closest distance between the location of these earthquakes to the location of a market. It also assigns values from 0 to 3 to each day for each market, based on the difference between the pecentage of change in one market and the average of all the markets, attempting to isolate the effect of earthquake (or a special event) that affect this one market and not the others. This 'effect' is assigned based on average and standard deviation of the change in markets, with three showing extreme divergence between a specific market and all the others.

3. The file '02_code\1_analysis\01_linear_reg.ipynb' runs our linear regression based on the output from the step 2. It includes two blocks that run regressions. The second one tries to correct the first block for an error of missing values. The results are saved in separate text files.

4. The file '02_code\1_analysis\02_multinomial_reg.ipynb' runs our multinomial logistic regression based on the output from step 2. It also includes two blocks that run regressions. The second one tries to correct the first block for an error of missing values. The results are saved in separate text files under '03_documentation\01_regressions.'

### Part 2: Market Analysis

1. Run the file: "01_preparation.ipynb" (in 02_code\0_preprocess) to retrieve the csv file "clean_major_earthquakes.csv" (in 01_data\02_pre). This "clean_major_earthquakes.csv" includes earthquake from 2008-2023, magnitudo >= 6

2. Run the file: "03_N225_companies_stock.ipynb" (in 02_code\0_preprocess\03_N225_companies_stock.ipynb) to retrieve the csv file "N225_companies_stock.csv" (in 01_data\02_pre). This "N225_companies_stock.csv" includes all 225 companies stock value (open, close, volume) of ^N225 (Nikkei 225, Japan Market). 

3. Run the file "03_N225_and_major_earthquake.ipynb" (in 02_code\1_analysis) to get the analysis of Market Performance (in here is Japan Market) and the Time for the Market to recover from the Earthquake. 

4. Do the same step 2 and 3 above for the rest markets : N100 (Europe), China, BSESN (India), NSEI (India).



### Part 3: Visualization Dashboard

1. All the results of the Japanese Market are shown in the Dashboard. Therefore please run the file "nikkei_companies_adresses.ipynb" (in 02_code/0_preprocess) to get the adresses of the companies that are shown on the map. 

2. All the Analysis of the Japanes Markets are stored in the file "03_N225_companies_stock.ipynb"(in 02_code/0_preprocess). Please run this file to safe the analysis for the markets. They are loading in the file for the dashboard again. 


## Acknowlegment

Special thanks to Techlabs and our Mentor Nopparat Wasikanon for all the work that went through organizing this project and insights. 

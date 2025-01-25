# Düsseldorf Techlabs Data Science Team 3

We are a startup aiming to develop a "tool" that can analyze and predict stock market trends based on global events - without the need to manually dig through the news.

### Project Team

-   Jan
-   Anh
-   Jannette
-   Sohail

### Project Phases

Project timeframe: January 21 - March 22, 2025

| Steps | Description            | Timeline | Completion Date |
|-------|------------------------|----------|-----------------|
| 1     | Team and Project setup | Week 1   | January 26      |

### Abstract

tktktktk

### Introduction

We were given 2 collection of data sets containing information about stock markets and earthquakes. Stock data sets consisted of 16 csv files, containing daily values for 12 different stock market indices going from August 2008 to July 2023, together almost 45000 rows and 8 columns. The Earthquake file covered earthquakes around the world from 1990 to 2023, and contained various characteristics such as location, magnitude, depth, etc. We were asked to add at least two other data sets.

The issues we faced were: - How to connect the data sets - How to upload the data sets in GitHub

### Data

Our first practical task was to understand and explore the data.The data included around 3.5 million earthquakes, averaging to 300 per day. The csv file is around 500MB and difficult to work with, e.g. inability to do a fast basic exploratory analysis with software such as Excel. The first step was to remove all the rows from before 2008, as we didn't have corresponding data from stock market for that period.

``` python
df = pd.read_csv('/data/Eartquakes-1990-2023.csv')
df['date'] = pd.to_datetime(df['date'],format='ISO8601')
cutoff = pd.Timestamp('2008-07-31 00:00:00.00+00:00') #the last date before stock data begins
df = df[df['date'] > cutoff] #removing rows before cutoff date
df.to_csv('/data/EQ2008-23.csv')
```

Stock market data seemed straight forward. They covered all the dates in which stock markets functioned during a 15 year period. We could easily combine them into one file instead of 16. Two of them had a typo in their name so after correcting that, it was easy to do.

``` python
dfs = [] #create a list to save all the csv's
# Loop through the years
for year in range(2008, 2024):
    file_name = "/data/"+str(year)+"_Global_Markets_Data.csv"
        # Read the CSV file
    df = pd.read_csv(file_name)
    dfs.append(df) #adding the year's df to the list
    
# Concatenate all DataFrames into a single DataFrame
merged_df = pd.concat(dfs, ignore_index=True) #creating a df for all the dates
merged_df.to_csv('/data/stock2008-23.csv')
```

The Earthquake data set had some issues. There were some dates with no reports of earthquakes happening, even though for other days there were report of average 300 earthquakes around the world. We decided to tktktktktk


We had to deal with some issues:
 - Which independent variables to use, between 300 quakes a day, and measures such as depth, magnitude, significance, and location.
 - What is our dependent variable, the difference between open and close or low and high, and the day after quakes or the same day, having in mind that quakes cover whole day and markets function in only a part of the day.
 - How to deal with weekends and holidays when stock markets are closed but earthquakes happen.

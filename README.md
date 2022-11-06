# Mercado_Libre_Prophet_Analysis


1. Data Sources
google_hourly_search_trends.csv
mercado_daily_revenue.csv
mercado_stock_price.csv

2. Installation Guide
PIP Installs for Google COLAB
!pip install prophet
!pip install hvplot
!pip install holoviews

3. Imports
import pandas as pd
import holoviews as hv
from prophet import Prophet
import hvplot.pandas
import datetime as dt
import numpy as np
%matplotlib inline

4. Steps of Implementation
## Find unusual patterns in hourly Google search traffic.
Read the search data into a DataFrame, and then slice the data to just the month of May 2020. (During this month, Mercado Libre released its quarterly financial results.) Use hvPlot to visualise the results. Do any unusual patterns exist?

**Answer:** There is a significant jump in the Google Search on the 5 and 6 day of May, 2020 when Mercdo Libre announced the reslts. 

Calculate the total search traffic for the month, and then compare the value to the monthly median across all months. Did the Google search traffic increase during the month that Mercado Libre released its financial results?

**Answer:** The total search results for month of May were 38181 while the Median search results were 35172, which are higher than median. 

## Mine the Search Traffic Data for Seasonality
Group the hourly search data to plot the average traffic by the day of the week (for example, Monday vs. Friday).
**Answer:**
/Screenshot 2022-11-05 at 8.51.23 PM.png
/Screenshot 2022-11-05 at 8.53.40 PM.png

Note that market events emerged during 2020 that many companies found difficult. But after the initial shock to global financial markets, new customers and revenue increased for e-commerce platforms. So, slice the data to just the first half of 2020 (2020-01 to 2020-06 in the DataFrame), and then use hvPlot to plot the data. Do both time series indicate a common trend that’s consistent with this narrative?
**Answer:**
/Screenshot 2022-11-05 at 8.55.37 PM.png

Yes, it is indicative of the this trend. 

Create a new column in the DataFrame named “Lagged Search Trends” that offsets, or shifts, the search traffic by one hour. Create two additional columns:
“Stock Volatility”, which holds an exponentially weighted four-hour rolling average of the company’s stock volatility
“Hourly Stock Return”, which holds the percentage of change in the company stock price on an hourly basis
**Answer:**
### Stock Volatility
/Screenshot 2022-11-05 at 8.57.43 PM

Review the time series correlation, and then answer the following question: Does a predictable relationship exist between the lagged search traffic and the stock volatility or between the lagged search traffic and the stock price returns?
### Correlation 
/Screenshot 2022-11-05 at 8.59.21 PM

## Create a Time Series Model by Using Prophet

What is the near-term forecast for the popularity of Mercado Libre?
/Screenshot 2022-11-05 at 9.02.46 PM.png

What time of day exhibits the greatest popularity?

/Screenshot 2022-11-05 at 9.04.55 PM

Which day of the week gets the most search traffic?
/Screenshot 2022-11-05 at 9.04.55 PM

What's the lowest point for search traffic in the calendar year?
/Screenshot 2022-11-05 at 9.06.21 PM

## Forecast the Revenue by Using Time Series Models

Interpret the model output to identify any seasonal patterns in the company revenue. For example, what are the peak revenue days? (Mondays? Fridays? Something else?)

/Screenshot 2022-11-05 at 9.08.20 PM


Produce a sales forecast for the finance group. Give them a number for the expected total sales in the next quarter. Include the best- and worst-case scenarios to help them make better plans.

Optimistic Revenue    1051.031452
Conservative           888.070959
Projected              969.607010


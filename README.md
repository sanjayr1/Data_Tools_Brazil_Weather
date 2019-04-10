# Data_Tools_Brazil_Weather

(Launch the jupyter notebook with binder below)
[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/jeff326/Data_Tools_Brazil_Weather/6d4a47c93759d01f8d44ceecf6a337d272f460b5)

- Main notebook = Brazil.ipynb
- Main presentation = slideshowroughdraft.ipynb

# Project Objective

I will be working with hourly weather data from 120+ weather stations in the southeast region of Brazil.  The data has been recorded from 2000 - 2016 and includes measurements of temperature, humidity, dew point, pressure, wind speed, solar radiation, and precipitation. First, we would gather descriptive statistics around each attribute of the data and get monthly and annual summaries. Then we would like to explore whether we can see effects of climate change (longer droughts, higher temperatures during certain times of year, coastal versus inland, differences in elevation, stronger solar radiation due to thinning ozone etc). Then, based on this historical data, possibly extrapolating this to predict montly/annual temperature, precipitation, etc if climate trends continue the way they are.

# Dataset Attribute and Metadata

- The Kaggle dataset is located here: https://www.kaggle.com/PROPPG-PPG/hourly-weather-surface-brazil-southeast-region

17 climate parameters (continuous values) from 122 weather stations - Southeast Brazil.

- wsid - Weather station id
- wsnm - Name station (usually city location or nickname)
- elvt - Elevation
- lat - Latitude
- lon - Longitude
- inme - Station number (INMET number) for the location
- city - City
- prov - State (Province)
- mdct - Observation Datetime (complete date: date + time)
- date - Date of observation
- yr - The year (2000-2016)
- mo - The month (0-12)
- da - The day (0-31)
- hr - The hour (0-23)
- prcp - Amount of precipitation in millimetres (last hour)
- stp - Air pressure for the hour in hPa to tenths (instant)
- smax - Maximum air pressure for the last hour in hPa to tenths
- smin - Minimum air pressure for the last hour in hPa to tenths
- gbrd - Solar radiation KJ/m2
- temp - Air temperature (instant) in celsius degrees
- dewp - Dew point temperature (instant) in celsius degrees
- tmax - Maximum temperature for the last hour in celsius degrees
- dmax - Maximum dew point temperature for the last hour in celsius degrees
- tmin - Minimum temperature for the last hour in celsius degrees
- dmin - Minimum dew point temperature for the last hour in celsius degrees
- hmdy - Relative humid in % (instant)
- hmax - Maximum relative humid temperature for the last hour in %
- hmin - Minimum relative humid temperature for the last hour in %
- wdsp - Wind speed in metres per second
- wdct - Wind direction in radius degrees (0-360)
- gust - Wind gust in metres per second


- Here are a few samples of data points for each attribute. I pulled data from 2 weather stations and kept the data in series to demonstrate how the values may differ.

| wsid| wsnm       | elvt | lat	     |     lon	  |inme|	city	   |prov|	       mdct        |     date   |tmax|	dmax|	tmin|	dmin|	hmdy|	hmax|	hmin|wdsp| wdct  |gust |
|-----|------------|------|----------|------------|----|-----------|----|--------------------|----------- |-----|-----|-----|-----|-----|-----|-----|----|------ |---- |
| 178 | SÃO GONÇALO| 237.0| -6.835777|	-38.311583|A333|São Gonçalo|RJ  |	2007-11-06 05:00:00|	2007-11-06|	25.4|	16.4|	23.8|	16.0|	62.0|	62.0|	57.0|	2.0|	99.0 |	6.8|
| 178 | SÃO GONÇALO| 237.0| -6.835777|	-38.311583|A333|São Gonçalo|RJ  |	2007-11-06 06:00:00|  2007-11-06|	23.8|	16.7|	22.0|	16.2|	72.0|	72.0|	62.0|	1.3|	93.0 |	4.9|
| 178	| SÃO GONÇALO| 237.0| -6.835777|	-38.311583|A333|São Gonçalo|RJ  |	2007-11-06 07:00:00|	2007-11-06|	22.0|	17.8|	19.5|	16.6|	86.0|	89.0|	72.0|	0.5|	157.0|	2.8|
| 178	| SÃO GONÇALO| 237.0| -6.835777|	-38.311583|A333|São Gonçalo|RJ  |	2007-11-06 08:00:00|  2007-11-06|	19.7|	17.3|	18.3|	16.9|	93.0|	94.0|	85.0|	NaN|	141.0|  1.5|
| 178	| SÃO GONÇALO| 237.0| -6.835777|	-38.311583|A333|São Gonçalo|RJ  |	2007-11-06 09:00:00|	2007-11-06|	22.9|	18.3|	18.2|	17.1|	75.0|	94.0|	75.0|	NaN|	248.0|  NaN|
| 178	| SÃO GONÇALO| 237.0| -6.835777|	-38.311583|A333|São Gonçalo|RJ  |	2007-11-06 11:00:00|	2007-11-06|	0.0	| 0.0	|  0.0|	0.0 |	 0.0|	0.0	| 0.0	| 0.0|	0.0	 |  0.0|
| 178	| SÃO GONÇALO| 237.0| -6.835777|	-38.311583|A333|São Gonçalo|RJ  |	2007-11-06 12:00:00|	2007-11-06|	0.0	| 0.0	|  0.0|	0.0 |  0.0| 0.0	| 0.0	| 0.0|	0.0  |  0.0|
| 178	| SÃO GONÇALO| 237.0| -6.835777|	-38.311583|A333|São Gonçalo|RJ  |	2007-11-06 13:00:00|	2007-11-06|	0.0	| 0.0	|  0.0|	0.0 |  0.0| 0.0 | 0.0	| 0.0|	0.0  |  0.0|
| 178	| SÃO GONÇALO| 237.0| -6.835777|	-38.311583|A333|São Gonçalo|RJ  |	2007-11-06 14:00:00|	2007-11-06|	31.8|	16.0|	30.0|	14.3|	36.0|	42.0|	36.0|	3.2|	97.0 |  9.1|
| 423	| BARUERI	   | 777.0| -23.52389|	-46.86945	|A755|Barueri	   |SP  |	2016-09-30 04:00:00|	2016-09-30|	14.9|	12.3|	14.7|	11.3|	84.0|	85.0|	80.0|	0.0|	0.0	 |  0.0|


| yr	| mo| da|	hr|	prcp|	stp  | smax| smin|gbrd|	temp|	dewp|
|-----|---|---|---|-----|------|-----|-----|----|-----|-----|
| 2007|	11|	6 |	 0|	 NaN|	982.5|982.5|981.3|NaN | 29.3|	12.1|
| 2007|	11|	6	|  1|	 NaN|	983.2|983.2|982.5|NaN |	29.0|	13.5|
| 2007|	11|	6	|  2|	 NaN|	983.5|983.5|983.2|NaN |	27.4|	14.0|



# Tentative Timeline

- Data collection: Data attained from Kaggle
- Data Cleanup: End of Week 5
- Transformation: End of Week 6 
- Feature Engineering: End of Week 7
- Statistical Summary: End of Week 8
- Visualization: End of Week 9

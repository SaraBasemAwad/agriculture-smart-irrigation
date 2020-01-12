# agriculture-smart-irrigation

## Installation

Run the following:
```
pip install selenium
pip install requests
pip install BeautifulSoup
pip install BackgroundScheduler
pip install logging
pip install utc
pip install refet
pip install pvlib
```

## Global Parameters

Change base_path into your global path directory

## Scripts

### AccuWeather.ipynb
This script is responsible for trigerring a task scheduler on different time intervals of each day for 
each city defined in "cities_locations.xlsx" and exporting data from AccuWeather such as the following information:
- Temperature
- Precipitation
- Wind Speed
- Solar Radiation
- Humidity
- Cover Percentage

### Aggregate_EEflux_RefET.ipynb
This script is responsible for computing the reference evapotranspiration ETo for all the sites from AmeriFlux
refering to [Ref ET](https://github.com/WSWUP/RefET) and then retrieve the ETo from EEflux and resample
the AmeriFlux data from half-hourly to daily and merge with EEflux data

### Ameriflux_Cleaning.ipynb
This script is responsible for cleaning the half-hourly data for all the sites from AmeriFlux
and resampling the half-hourly to daily and then retrieving the data from EEflux and merging the daily AmeriFlux with EEflux data

- is_hourly: Boolean value set to True for hourly data otherwise False
- skipRowsNum: Defaults to zero, incase the excel has meaningless rows to skip it should be set to the number of rows to skip
- split_num: Defaults to zero, the index to read the name of the site from the file when splitting the file name
- lags_count: The number of lags to generate the data for, currently it it set to 5
- output_name: The path of the output file where the generated data should reside


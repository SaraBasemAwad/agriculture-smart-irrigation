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

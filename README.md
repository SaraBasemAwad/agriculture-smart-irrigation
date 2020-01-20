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
pip install rasterio
pip install earthpy
pip install pyproj
pip install Pool
pip install requests_respectful
pip install ratelimit
pip install backoff
pip install tenacity
pip install gcsfs
pip install wget
pip install clint
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

### EEflux_Scrap.ipynb
This script is responsible for scraping data from EEflux by specifying the following input and output fields:

- BUCKET_NAME: The name of the bucket in google cloud that is used to store the rasters retrieved ex: agriculture-bucket-wgr
- site_id_path: The folder name of the site id to scrap data for
- site_id: The name of the site id to scrap data for 
- type_id: The type oe metric to be exported from the raster (i.e 1 for ET, 2 for ETr, 3 for ETo, 4 for LST)
- from_to: The date range to retrieve the data for. i.e: "2004-01-01 to 2011-12-31"

### EuroFlux_Cleaning.ipynb
This script is responsible for concatenating data from EuroFlux keeping each Level alone (Level 2, 3, & 4) and adding a year and a site_id column which are retrieved from the file's name

- input_path: The input path folder to read the zip files from

### Ameriflux_Cleaning-Correction.ipynb
This script is responsible for computing the correction on Ameriflux Daily data using Bowen's ratio and generating data similar to what is in Ameriflux_Cleaning script which uses the same input/out parameters. Graphs are also exported to show
the difference between LE before and after correction between Ameriflux and EEflux

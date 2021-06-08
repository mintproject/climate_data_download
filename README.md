# Recipes to download and register the climate data needed for MINT

Guide on downloading the necessary climate data.

## GLDAS

### GLDAS 3-hourly

See this repository: https://github.com/mintproject/MINT-Data-Sync/blob/master/sync_gldas.py

### GLDAS monthly

The code above can be modified using the following link to obtain the data: https://hydro1.gesdisc.eosdis.nasa.gov/data/GLDAS/GLDAS_NOAH025_M.2.1/

## CHIRPS

### 6-hourly

Download the data from this link: https://data.chc.ucsb.edu/products/CHIRPS-2.0/africa_6-hourly/p1_bin/. Needs to be updated as more data becomes available.

### monthly

All the monthly data is available in one file. https://data.chc.ucsb.edu/products/CHIRPS-2.0/global_monthly/netcdf/. Needs to be re-downloaded as it gets updated. See notebook in this repository to lift metadata directly.

## ECMWF ERA5

1. Need to register for an account here: https://cds.climate.copernicus.eu/#!/home
2. Use the following API call by updating month year:

```
import cdsapi

c = cdsapi.Client()

c.retrieve(
    'reanalysis-era5-land-monthly-means',
    {
        'format': 'netcdf',
        'product_type': 'monthly_averaged_reanalysis',
        'variable': [
            '2m_temperature', 'total_precipitation',
        ],
        'year': [
            '1981', '1982', '1983',
            '1984', '1985', '1986',
            '1987', '1988', '1989',
            '1990', '1991', '1992',
            '1993', '1994', '1995',
            '1996', '1997', '1998',
            '1999', '2000', '2001',
            '2002', '2003', '2004',
            '2005', '2006', '2007',
            '2008', '2009', '2010',
            '2011', '2012', '2013',
            '2014', '2015', '2016',
            '2017', '2018', '2019',
            '2020', '2021',
        ],
        'month': [
            '01', '02', '03',
            '04', '05', '06',
            '07', '08', '09',
            '10', '11', '12',
        ],
        'time': '00:00',
    },
    'download.nc')
```
3. How to use API instructions here: https://cds.climate.copernicus.eu/api-how-to 

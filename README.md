# Weather Driver Independence Evaluation
UConn Eversource Energy Center - Jack Bienvenue Spring 2025 internship.

<p align="center">
  <img src="images/Rain_over_water_Unsplash.jpg" width="50%">
</p>

This repository contains scripts which allow for the construction of an outage prediction model for the state of Connecticut using meteorological data from the [ECMWF ERA5 LAND package dataset.](https://www.ecmwf.int/en/era5-land)

## PROBLEM DESCRIPTION:

## DATA DESCRIPTION:

This repository provides scripts to ease the process of data cleaning. This open meterological data

## DEPENDENCIES:

The scripts in this repository are written using **Quarto**, an free software which allows for markdown-code cell development and various forms of outputs, like notebooks and presentations. Quarto can be downloaded [here](https://quarto.org/docs/get-started/) and runs on top of Jupyter for Python, the language of this project. 

## DATA PROCESSING:

Since the data processing for analysis is comprised of many stages, let's walk through these.

**The GRIB files provided from ECMWF are time series of weather data for whole geographic areas, which are comprised on rectangular (spherically projected because of the surface of the Earth) grid cells. We want to:**
**1. Make data accessible to us by converting to CSV, and**
**2. Gather time series for individual grid cells.**

First, download data from the ERA5 Land Package. Next, perform data handling for GRIB files from the European Center for Medium-Range Weather Forecasting (ECMWF) to CSVs:

1. Process GRIB files from **data/data_CT** using **scripts/grib_to_csv.qmd** (NOTE: This operation may have to be batched if you experience processing constraints)
2. IF THE PREVIOUS STEP WAS DONE IN BATCHES, merge batches using **scripts/merging_batched_csvs.qmd**. Otherwise, proceed.
3. Convert hourly dataframes to daily using aggregation by using **scripts/aggregation_daily.qmd**

Next, construction of grid cells for geospatial reference, visualization, & analysis:

1. Use scripts/shapefile_build.qmd to construct grid cells or access the default ones in data/grid_cell_shapefile

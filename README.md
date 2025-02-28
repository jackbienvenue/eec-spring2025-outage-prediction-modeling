# Weather Driver Independence Evaluation
UConn Eversource Energy Center - analysis of independence of weather variables to assess validity of driver independence assumption in outage forecasting reports.

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Centered Image</title>
    <style>
        body {
            text-align: center; /* This centers the content horizontally */
            margin: 0;
            padding: 0;
        }
        img {
            width: 30%; /* Makes the image 30% of its original size */
            display: block; /* Ensures the image is treated as a block element */
            margin: 0 auto; /* Centers the image horizontally */
        }
    </style>
</head>
<body>
    <img src="images/Rain_over_water_Unsplash.jpg" alt="Rain over water">
</body>
</html>

Since the data processing for analysis is comprised of many stages, let's walk through these.

First, data handling for GRIB files from the European Center for Medium-Range Weather Forecasting (ECMWF) to CSVs:

1. Process GRIB files from data/data_CT using scripts/grib_to_csv.qmd (NOTE: This operation may have to be batched because of processing constraints)
2. IF THE PREVIOUS STEP WAS DONE IN BATCHES, merge batches using scripts/merging_batched_csvs.qmd. Otherwise, proceed.
3. Convert hourly dataframes to daily using aggregation by using scripts/aggregation_daily.qmd

Next, construction of grid cells for geospatial reference, visualization, & analysis:

1. Use scripts/shapefile_build.qmd to construct grid cells or access the default ones in data/grid_cell_shapefile

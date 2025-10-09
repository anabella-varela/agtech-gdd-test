# 🌾 Geospatial Data Developer – Agro Take-Home Challenge

![soy](assets/soy.jpg)

## Intro

Welcome to the Geospatial Data Developer Take Home Challenge!

In Garruchos Agropecuaria, we're growing our data toolset and it is important that developers are capable and flexible enough to learn and adapt to new technologies if needed.

The challenge is divided into two parts which value is presented below. We're aware that this test is quite open, as we intend to give value to innovative approaches and not that much to applying tool A or B, the whole assignment should take 2-3 days at most (you can take the time you need to resolve it tho). Please also note that the bonus section is optional, we know that these THT take time and we value your effort.

The delivery format is up to you, it can be a GitHub repository, a .zip file, a Google Drive folder, or whatever you prefer. Any code used to resolve the challenge should be included in the delivery, as well as a README file explaining how to run it and any other information you consider relevant. If any step is performed outside a programming language (e.g., QGIS, ArcGIS, etc.), please include screenshots or a video explaining the process.

We're excited to see how you solve it, please take your time and be aware that there is no one unique approach to it, feel free to use any resources you want and more importantly, enjoy it.

## Part 1. Setting up the infrastructure with Docker 🐳 (3 points)

While we wrangle data at different levels and stages of maturity, PostgreSQL and its extensions ecosystem has demonstrated to be great at solving quite a lot of the challenges we face in our day to day, specially when it comes to answering questions that lay on different geospatial data sources and types, including raster, vector and spatial index (H3) data mainly.

The first part of the challenge is to set up a Dockerfile and image that fulfills the following requirements:

- Runs PostgreSQL, with minimum major version 14
- Has PostGIS extension installed, with minimum major version 3
- Has the h3-pg extension installed (optional)

Once the image is built, the following datasets should be loaded into the database (these will be used in the next part of the challenge):

1. Field boundaries of "La Magdalena" farm L4 plot

- Description: Polygon layer with the boundaries of the L4 field "La Magdalena" in Córdoba province, Argentina.
- Format: Keyhole Markup Language (KML)
- [Dataset](https://storage.googleapis.com/agtech-test-data/la_magdalena_L4.kml)

Columns:

    - name: Field name
    - geom: Geometry column (Polygon, EPSG:4326)

2. Soy performance data from the campaigns 2019, 2021 and 2023

- Description: Point / H3 (resolution 12) layer with soy yield data from the L4 field "La Magdalena" in Córdoba province, Argentina.
- Format: GeoParquet (1.0.0)
- [Dataset](https://storage.googleapis.com/agtech-test-data/soy_performance_2019_2021_2023.parquet)

Columns:

    - campaign_year: End year of the campaign (e.g., 2019 for the 2018/2019 campaign)
    - h3_res12: H3 index at resolution 12
    - geom: Geometry column (Point, EPSG:4326)
    - performance_pct: Soy performance in percentage (0-100), relative across all campaigns

3. Veris soil sensor data

>NOTE: Veris soil data comes from 2019 campaign only, but we can consider it as static data for the purpose of this challenge.

- Description: Point layer with soil sensor data from the L4 field "La Magdalena" in Córdoba province, Argentina.
- Format: GeoPackage
- [Dataset](https://storage.googleapis.com/agtech-test-data/veris_data.gpkg)

Columns:

    - ec_surface: Relative electrical conductivity at the surface level (%)
    - ec_subsurface: Relative electrical conductivity at the subsurface level (%)
    - altimetry_rel: Relative altimetry
    - geom: Geometry column (Point, EPSG:4326)

## Part 2. Analyzing crop yield data (7 points) 🌱

Once the data has been correctly ingested into the database, we can start analyzing it.

>NOTE: You may use both SQL and Python for this part of the challenge.

1. (2 points) Evaluate the performance of the different soy campaigns and identify possible correlations between the yield performance and:

    - Electrical conductivity (at both subsurface and surface levels)
    - Altimetry

2. (2 points) Can you identify spatial hotspots and coldspots based on the yield performance of the 2020-2021 campaign?

3. (3 points) What could be the reason for the low productivity in the worst performant areas? Can you suggest any actions to be taken in collaboration with the field team to improve performance in these areas?

### Bonus (2 extra points)

The field team and the business stakeholders require a better understanding of the crop as plants grow (i.e before the campaign ends and yield values are collected).

For this purpose, you have decided to include (at least one) Sentinel-2 based spectral index (e.g: NDVI, NDFI, EVI, SAVI, etc.) for the 2020-2021 campaign.

Do you think that it'd be possible to use this index as a proxy to know the crop's health and anticipate the yield performance as the crop grows?

>💡 HINT: You can use any data sources that you find useful, e.g: [Planetary Computer](https://planetarycomputer.microsoft.com/dataset/sentinel-2-l2a) or [Google Earth Engine](https://developers.google.com/earth-engine/datasets/catalog/COPERNICUS_S2_SR_HARMONIZED)

## Final questions 🧠

1. If you had to integrate yield, soil, satellite, and weather data on a continuous basis, what steps or tools would you use to ensure data quality, consistency, and traceability over time?

2. How would you adapt your current workflow so it can run across many fields and campaigns while remaining reproducible and maintainable?


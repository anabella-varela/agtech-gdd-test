# Part 1. Setting up the Infrastructure with Docker 🐳

This repository documents the setup and upload process of spatial datasets into a PostgreSQL + PostGIS database using Docker.  

The complete step-by-step process is detailed in this [shared document](https://docs.google.com/document/d/1HuQ6qCgoR1tylKmPry1VrAUdCpMT_QI3KeBg7WzyTZA/edit?tab=t.0), and demonstrated in the attached Video Evidence -> PART_1.webm 🎥 Also, there is a dockerfile text with the scrip for creating the image

## Steps Summary
1. **Docker setup**
   - Downloaded Docker into my personal computer
   - Created a Dockerfile
   - Build and ran PostgreSQL + PostGIS container

2. **La Magdalena field (KML)**
   - Imported using `ogr2ogr`.

3. **Soy performance (GeoParquet)**
   - Loaded with Python + GeoPandas.

4. **Veris soil sensor data (GeoPackage)**
   - Imported with Python + GeoPandas.

##  Video Evidence
The video PART_1.webm demonstrates, from within the Docker container, that the PostgreSQL database contains the three tables

-
Note:
For data transformation and analysis, I’ll use Python. While I could perform grouping, joining, and filtering operations directly in SQL, I find that using a Google Colab notebook provides a cleaner and more transparent way to share both the code and the analytical insights step by step.
-

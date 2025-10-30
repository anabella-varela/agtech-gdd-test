# 🧩 Part 1. Setting up the Infrastructure with Docker 🐳

This repository documents the setup and upload process of spatial datasets into a PostgreSQL + PostGIS database using Docker.  

The complete step-by-step process is detailed in this[shared document](https://docs.google.com/document/d/1HuQ6qCgoR1tylKmPry1VrAUdCpMT_QI3KeBg7WzyTZA/edit?tab=t.0), and demonstrated in the attached Video Evidence -> PART_1.webm 🎥 

---
## 🧠 Steps Summary

1. **Docker setup**
   - Downloaded Docker into my personal computer
   - Created and ran PostgreSQL + PostGIS container.
   - Verified connectivity using `psql`.

2. **La Magdalena field (KML)**
   - Imported using `ogr2ogr`.

3. **Soy performance (GeoParquet)**
   - Loaded with Python + GeoPandas.

4. **Veris soil sensor data (GeoPackage)**
   - Imported and converted geometry to GeoJSON.

---

## 🎥 Video Evidence
The attached video demonstrates, from within the Docker container, that the PostgreSQL database contains the three tables


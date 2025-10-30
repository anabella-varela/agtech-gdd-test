# 🐳 Part 1 — Infrastructure Setup with Docker

This repository documents the setup and upload process of spatial datasets into a **PostgreSQL + PostGIS** database using Docker.  
The goal is to build a reproducible spatial-data environment for later analysis and visualization.

---

## 📄 Documentation & Evidence

- 📘 **Detailed Process:** [Google Doc](https://docs.google.com/document/d/1HuQ6qCgoR1tylKmPry1VrAUdCpMT_QI3KeBg7WzyTZA/edit?tab=t.0)
- 🎥 **Video Evidence:** `PART_1.webm` — shows the 3 tables inside the Docker container
- 🐋 **Dockerfile:** included in this repo contains the script used to build the image

---

## ⚙️ Steps Summary

### 1. Docker Environment
- Installed Docker on mi CPU.
- Created a `Dockerfile` to build a container running **PostgreSQL + PostGIS** with h3-pg extension.
- Built the image and launched the container.

### 2. La Magdalena — Field Boundary (KML)
- Imported the KML file into PostGIS using `ogr2ogr`.
- Created the table: `la_magdalena`.

### 3. Soy Performance (GeoParquet)
- Loaded the GeoParquet file using **Python + GeoPandas**.
- Stored it in PostGIS as `soy_performance`.

### 4. Veris Soil Sensor Data (GeoPackage)
- Imported the GeoPackage file with **Python + GeoPandas**.
- Created the table: `veris_soil_data`.

---

NOTE: For data transformation and analysis I will primarily use Python.
Although many operations (grouping, joining, filtering) can be performed directly in SQL, I prefer to use Google Colab notebooks to present the step-by-step code, intermediate results, visualizations, and comments in a shareable and reproducible format.

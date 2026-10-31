# Rides & Bookings Ingestion and Geospatial Processing

An end-to-end Big Data ETL pipeline that ingests, cleans, and spatializes NYC Yellow Taxi trip records using PySpark, Uber H3 spatial indexing, and Apache Hive.

---

## 👥 Team & Collaboration
This project was developed as a collaborative team effort by:
* **Nasser Alalem**
* **Fatma Ibrahim**
* **Galal Qassas**

---

## 🛠️ Tech Stack & Architecture
* **Processing:** PySpark, Apache Hadoop (HDFS)
* **Storage & Warehousing:** Apache Hive, Parquet Format
* **Geospatial Indexing:** Uber H3 (Resolution 9)
* **Language & Tools:** Python (PySpark), HiveQL, Jupyter Notebooks

---

## 🔄 Pipeline Workflow
1. **Data Ingestion & Preparation:**
   * Raw trip records ingested and converted to compressed Parquet format for optimized Spark processing.
2. **Data Cleaning & Transformation:**
   * Removed records with invalid coordinates (0.0 values).
   * Filtered out trips with `trip_distance <= 0.0` and invalid timestamps where pickup time exceeded dropoff time.
   * Generated unique sequential `trip_id` identifiers and derived `trip_duration_time`.
3. **Geospatial Processing:**
   * Converted pickup and dropoff latitude/longitude coordinates into discrete H3 hexagonal cell tokens (`start_geo_hash`, `end_geo_hash`) using resolution 9.
4. **Hive Loading & Analytics:**
   * Exported final transformed datasets into Apache Hive external tables stored as Parquet.
   * Executed queries to identify high-demand pickup spots, popular trip destinations, and ride frequency aggregations.

---

## 📁 Repository Structure
* `finaltransform.ipynb`: PySpark transformation, cleaning, and H3 indexing implementation.
* `Project-Report.pdf`: System documentation, HDFS logs, and Hive query execution reports.

# 🚔 LAPD Crime Data Engineering Pipeline

## 📌 Project Overview

This project builds an end-to-end **data engineering pipeline** using real-world crime data from the City of Los Angeles. The goal is to simulate how raw data is ingested, transformed, stored, and served for analysis.

The pipeline follows a standard data engineering workflow:

**Ingestion → Transformation → Storage → Serving**

---
##DATA SOURCE
https://www.kaggle.com/datasets/aadigupta1601/lapd-crime-data-2020-2024



## 🎯 Objectives

* Build a reproducible data pipeline using Python and SQL
* Clean and transform real-world messy data
* Store structured data in a relational database
* Enable analytical queries for insights
* Showcase data engineering skills for a portfolio

---

## 📂 Dataset Description

The dataset contains crime records reported by the Los Angeles Police Department (LAPD).

### Key fields:

* `date` – Date of crime occurrence
* `crime_type` – Category of crime
* `location` – Area or district
* `victim_age` – Age of victim
* `victim_gender` – Gender of victim
* `weapon_used` – Type of weapon involved 

---

## ⚙️ Tech Stack

* **Python** (Pandas) – Data processing
* **SQLite ** – Database storage
* **SQL** – Querying and analysis
* *(Optional)*: Airflow – Pipeline orchestration
* *(Optional)*: Streamlit / Power BI – Visualization

---

## 🏗️ Pipeline Architecture

### 1. Data Ingestion

* Load dataset from CSV 
* Initial inspection and schema validation

```python
df = pd.read_csv("lapd_crime_data.csv")
```

---

### 2. Data Transformation

* Handle missing values
* Standardize columns (e.g., weapon types)
* Convert date formats
* Remove duplicates

```python
df["date"] = pd.to_datetime(df["date"])
df["weapon_used"] = df["weapon_used"].fillna("unknown")
df = df.drop_duplicates()
```

---

### 3. Data Storage

* Store cleaned data in a relational database

```python
df.to_sql("crimes", conn, if_exists="replace", index=False)
```

---

### 4. Data Serving

* Query data using SQL
* Generate insights

```sql
SELECT weapon_used, COUNT(*) AS total
FROM crimes
GROUP BY weapon_used
ORDER BY total DESC;
```

---

## 🧱 Database Schema

### Table: `crimes`

| Column Name   | Data Type | Description              |
| ------------- | --------- | ------------------------ |
| id            | INTEGER   | Unique record ID         |
| date          | DATE      | Crime occurrence date    |
| crime_type    | TEXT      | Type of crime            |
| location      | TEXT      | Area/location            |
| victim_age    | INTEGER   | Victim age               |
| victim_gender | TEXT      | Victim gender            |
| weapon_used   | TEXT      | Weapon involved (if any) |

---

## 📊 Example Analysis

* Most common crime types
* Weapon usage distribution
* Crime trends over time
* High-risk locations

---

## 🚀 How to Run the Project

1. Clone the repository

```bash
git clone <your-repo-link>
cd lapd-data-pipeline
```

2. Install dependencies

```bash
pip install pandas sqlite3
```

3. Run the pipeline

```bash
python pipeline.py
```

---

## 📈 Future Improvements

* Automate ingestion using scheduled jobs
* Use PostgreSQL or cloud data warehouse
* Implement data validation checks
* Add dashboards (Power BI / Streamlit)
* Introduce real-time streaming simulation

---

## 💼 Portfolio Value

This project demonstrates:

* End-to-end data pipeline development
* Data cleaning and transformation
* SQL and database design
* Real-world dataset handling
* Analytical thinking

---

## 📎 License

This project uses publicly available data. Please check the original dataset source for licensing details.

---

## ✨ Author

Brandon Mutua Mwiti Kirema
Aspiring Data Engineer

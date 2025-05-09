# Layoffs SQL Project – Data Cleaning & EDA

This project showcases a full data cleaning and exploratory analysis pipeline using **SQL** on a dataset containing records of global company layoffs. It was conducted in **MySQL** and includes thorough steps for cleaning and exploring the data.

---

## 🧾 Project Objectives

* Clean and standardize a raw tech layoffs dataset to make it suitable for analysis.
* Perform exploratory data analysis (EDA) to extract insights and trends.

---

## 📁 Files

* `sql_DataCleaning.sql` – SQL script containing data cleaning queries.
*  `sql_EDA.sql` – SQL script containing EDA queries.
* `layoffs.csv` – The data used.

---

## 🛠 Tools Used

* **Database:** MySQL
* **Environment:** MySQL Workbench or any MySQL-compatible interface
* **Techniques:** CTEs, window functions, date formatting, aggregation, joins

---

## 🧼 Data Cleaning Steps

### 1. Data Staging

* Duplicated original table into `layoffs_staging` and `layoffs_staging2` to preserve the raw data and isolate changes.

### 2. Duplicate Removal

* Used `ROW_NUMBER()` to identify duplicate entries based on all major fields.
* Removed redundant rows from `layoffs_staging2`.

### 3. Standardization

* Trimmed spaces from string fields (e.g., `company`, `country`).
* Standardized values like "Crypto" and removed trailing punctuation from country names.
* Converted `date` strings to the correct `DATE` format.

### 4. Null & Blank Value Handling

* Replaced empty strings in `industry` with `NULL`.
* Filled missing industries by cross-referencing other records of the same company.
* Removed rows with missing critical values (`total_laid_off` and `percentage_laid_off`).

### 5. Schema Optimization

* Dropped helper columns used for interim processes (e.g., `row_num`).

---

## 📊 Exploratory Data Analysis (EDA)

A range of queries was used to analyze the cleaned data:

### 🔢 Summary Statistics

* Maximum layoffs: `MAX(total_laid_off)`, `MAX(percentage_laid_off)`
* First and last recorded layoff: `MIN(date)`, `MAX(date)`

### 🏢 Company Insights

* Companies with the most layoffs overall
* Year-wise layoffs per company
* Companies with the highest average percentage laid off

### 🌍 Geographic Insights

* Layoffs by country
* Layoffs by industry
* Layoffs by company stage (e.g., Startup, Series A, etc.)

### 📆 Temporal Analysis

* Total layoffs by year: `GROUP BY YEAR(date)`
* Monthly layoffs trend
* Rolling monthly layoffs total using `SUM(...) OVER (ORDER BY month)`

### 🥇 Top 5 Companies by Year

* Used `DENSE_RANK()` to identify the top 5 companies with the most layoffs in each year.

---


If you found this project useful, consider giving it a ⭐ or contributing with improvements. You can also fork it and build visual dashboards with Power BI, Tableau, or Python!

---

Would you like me to bundle this README and the SQL script into a downloadable ZIP file?

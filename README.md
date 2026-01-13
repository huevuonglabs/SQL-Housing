# 🏠 SQL - Housing Data Cleansing Toolkit (SQL Server)

## 📌 Project Overview

This project demonstrates a practical **data cleaning workflow in SQL Server** using a housing / mortgage dataset. The goal is to transform raw, inconsistent data into a **clean, analysis-ready table** by standardizing formats, fixing missing values, splitting messy fields, removing duplicates, and dropping unused columns.

This is the type of cleaning process that typically happens before reporting, dashboarding, or modeling—especially when working with real business datasets.

---

## ✅ What This Project Demonstrates

This project highlights my ability to:

* Clean and transform messy datasets using **SQL only**
* Write structured **step-by-step data preparation scripts**
* Standardize inconsistent formats (dates, categorical fields)
* Handle **missing values** with logic-driven backfilling
* Split combined address fields into normalized columns
* Identify and remove duplicates using **window functions**
* Improve dataset usability by removing irrelevant columns

---

## 🧠 Business/Analytical Goal

Housing datasets are often noisy: inconsistent date formats, null addresses, duplicate records, and mixed-format fields make the data difficult to use for analysis.

This project cleans the dataset so it can be reliably used for:

* housing market analysis
* mortgage trend reporting
* property pricing exploration
* geographic segmentation (city/state level analysis)

---

## 🗂 Dataset Notes (High Level)

The dataset includes:

* property sale and mortgage-related records
* key identifiers such as **ParcelID** and **UniqueID**
* address information for both **property** and **owner**
* sale date, sale price, legal reference, and vacancy status indicators

---

## 🔧 Cleaning Steps Performed (SQL Workflow)

### 1) Inspect the raw table

Loaded and reviewed the `Housing` table structure and values.

---

### 2) Standardize date format

Converted `SaleDate` into a clean SQL `DATE` type for consistency and analysis readiness.

✅ Techniques used:

* `CONVERT(Date, SaleDate)`
* `ALTER TABLE ... ADD`
* `UPDATE`

---

### 3) Populate missing property addresses

Filled missing `PropertyAddress` values by matching records using `ParcelID`.

✅ Techniques used:

* `JOIN` on `ParcelID`
* `ISNULL()` for backfilling missing values
* Ensuring unique updates using `UniqueID`

---

### 4) Split property address into structured fields

Separated combined address strings into:

* `PropertySplit_Address`
* `PropertySplit_City`

✅ Techniques used:

* `SUBSTRING()`
* `CHARINDEX()`

---

### 5) Clean and split owner address into address/city/state

Transformed a single `OwnerAddress` field into:

* `OwnerSplit_Address`
* `OwnerSplit_City`
* `OwnerSplit_State`

✅ Techniques used:

* `REPLACE()`
* `PARSENAME()` trick for parsing comma-separated text

---

### 6) Normalize categorical values (Y/N → Yes/No)

Converted inconsistent binary values into a cleaner format for easier filtering and reporting.

✅ Techniques used:

* `CASE WHEN`
* `UPDATE`

---

### 7) Remove duplicate records

Detected and removed duplicate rows using a window function based on key sale identifiers.

✅ Techniques used:

* `ROW_NUMBER() OVER (PARTITION BY ...)`
* CTE (`WITH RowNumCTE AS (...)`)
* Deleting records where `row_num > 1`

---

### 8) Drop unused or redundant columns

Removed fields that were no longer needed after cleaning or splitting.

✅ Dropped columns:

* `OwnerAddress`
* `PropertyAddress`
* `TaxDistrict`
* `SaleDate`

---

## 🛠 Tools / SQL Concepts Used

* SQL Server
* Data type conversion (`CONVERT`)
* Schema updates (`ALTER TABLE`)
* String parsing (`SUBSTRING`, `CHARINDEX`, `REPLACE`, `PARSENAME`)
* Conditional logic (`CASE`)
* Null handling (`ISNULL`)
* Deduplication with window functions (`ROW_NUMBER`)
* CTEs

---

## 📈 Outcome

After cleaning, the dataset becomes:

* easier to query and analyze
* consistent across formatting and categorical values
* normalized for location-based analysis (city/state breakdown)
* free of duplicate records
* structured for downstream use (dashboards, analysis, modeling)

---

If you want, I can also:
✅ rewrite this README in a more “Analytics Engineer” tone
✅ add a **project folder template** so each SQL project page is consistent
✅ generate a **main repo README** that summarizes all projects like a portfolio homepage

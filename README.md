# Python ETL Project: Data Cleaning & Transformation

This project demonstrates a core ETL (Extract, Transform, Load) process using Python and the Pandas library. The goal was to take a raw, "messy" sales dataset and transform it into a clean, complete, and reliable dataset ready for business analysis.

This project was completed in direct response to a job description for a Data Analyst, which emphasized the need for skills in **data manipulation**, **data quality management**, and **ETL processes**.

---

## 1. Extract 📂

* **Source:** The original "Snitch Clothing Sales" dataset from Kaggle.
* **Action:** Loaded the raw `Snitch Sales Transaction.csv` file into a Pandas DataFrame.
* **Initial Diagnosis:** An initial analysis with `df.info()` revealed significant data quality issues:
    * **2500** total rows.
    * Widespread **missing values** in critical columns like `Units_Sold`, `Unit_Price`, and `City`.
    * The `Order_Date` column was incorrectly stored as `object` (text) instead of a proper `datetime`.
    * A large number of **duplicate** records.

---

## 2. Transform 🧼

A multi-step data cleaning pipeline was applied to address these issues:

1.  **Date Transformation:** Converted the `Order_Date` column to `datetime` format. All rows with unfixable or missing dates were dropped, as they are unusable for sales analysis.
2.  **Duplicate Removal:** Identified and removed all duplicate rows to ensure data integrity.
3.  **Handling Missing Values:**
    * **Numerical:** Filled missing `Units_Sold` and `Unit_Price` with the **median** of their respective columns to maintain statistical integrity. `Discount_%` and `Sales_Amount` were filled with `0`, assuming a missing value meant no discount.
    * **Categorical:** Filled missing `City` and `Segment` data with the placeholder "Unknown" to ensure no data was lost.
4.  **Final Verification:** The cleaning process successfully filtered the original 2500 records down to **628 unique, high-quality, and complete records**.

---

## 3. Load 💾

* **Action:** The final, clean DataFrame was saved as a new CSV file: `snitch_sales_cleaned.csv`.
* **Result:** A pristine, analysis-ready dataset with **zero missing values** and **correct data types**.

## Tools Used 🛠️

* **Python**
* **Pandas** (for data manipulation and cleaning)
* **Jupyter Notebook** (for iterative development and documentation)

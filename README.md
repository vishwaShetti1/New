# Data Pipeline Project

## Project Title

**Data Pipeline using Web Scraping, Data Cleaning, SQLite, SQL, and Pandas**

---

## Project Description

This project demonstrates a complete **ETL (Extract, Transform, Load)** data pipeline using Python. The data is collected from **books.toscrape.com**, a public website designed for web scraping practice.

The pipeline performs the following tasks:

* Scrapes book information from the first five pages of the website.
* Cleans and transforms the collected data.
* Converts prices from GBP to INR using a fixed conversion rate.
* Stores the cleaned data in a normalized SQLite database.
* Executes SQL queries to analyze the data.
* Reads SQL query results into pandas.
* Reproduces the SQL JOIN using `pd.merge()` and compares both results.

---

# Dataset

Website:

https://books.toscrape.com/

Books Scraped:

* First 5 pages
* Total Books: 100

Collected Fields:

* Title
* Price (GBP)
* Star Rating
* Availability
* Category

---

# Technologies Used

* Python
* Requests
* BeautifulSoup
* Pandas
* SQLite3
* SQL
* Google Colab

---

# Python Libraries

```python
requests
beautifulsoup4
pandas
sqlite3
```

---

# Data Cleaning

The following preprocessing steps were performed:

### Price Cleaning

* Removed the "£" symbol.
* Converted the values into floating-point numbers.

Example:

£51.77 → 51.77

---

### Rating Conversion

Converted text ratings into integers.

| Text  | Integer |
| ----- | ------- |
| One   | 1       |
| Two   | 2       |
| Three | 3       |
| Four  | 4       |
| Five  | 5       |

---

### Availability

Converted availability text into Boolean values.

Example:

* In Stock → True
* Out of Stock → False

---

### Missing Values

If numeric values failed to parse:

* Median Imputation was applied.

If important text fields were missing:

* The row was removed.

Reason:

Median is less affected by outliers and produces better estimates for missing numeric values.

---

# Currency Conversion

Fixed project conversion rate:

**1 GBP = 105.50 INR**

No API was used because the assignment specifies a fixed conversion rate.

---

# Database Design

Database Name:

books.db

Tables:

## categories

| Column        | Type                |
| ------------- | ------------------- |
| category_id   | INTEGER PRIMARY KEY |
| category_name | TEXT UNIQUE         |

---

## books

| Column      | Type                |
| ----------- | ------------------- |
| book_id     | INTEGER PRIMARY KEY |
| title       | TEXT                |
| price_gbp   | REAL                |
| price_inr   | REAL                |
| rating      | INTEGER             |
| in_stock    | INTEGER             |
| category_id | INTEGER             |

Foreign Key:

books.category_id → categories.category_id

---

# SQL Queries Executed

The project includes the following SQL operations:

* SELECT
* WHERE
* ORDER BY
* LIMIT
* DISTINCT
* BETWEEN
* INNER JOIN
* GROUP BY (Extra)

---

# Pandas Operations

The following pandas operations were demonstrated:

* DataFrame creation
* Data cleaning
* `pd.read_sql()`
* `pd.merge()`
* Data comparison
* CSV export

---

# Output Files

The project generates the following files:

* raw_books.csv
* clean_books.csv
* books.db
* sql_query_outputs.txt
* sql_join_output.csv
* pandas_merge_output.csv
* comparison_report.txt

---

# Folder Structure

```
data_pipeline/

│

├── notebook.ipynb

├── raw_books.csv

├── clean_books.csv

├── books.db

├── sql_query_outputs.txt

├── sql_join_output.csv

├── pandas_merge_output.csv

├── comparison_report.txt

└── README.md
```

---

# How to Run

1. Open Google Colab.
2. Upload the notebook.
3. Run every code cell from top to bottom.
4. The notebook automatically:

   * Scrapes the website
   * Cleans the data
   * Creates the database
   * Executes SQL queries
   * Saves all outputs

---

# Assignment Requirements Covered

* Web Scraping
* Data Cleaning
* Error Handling
* Currency Conversion
* SQLite Database
* Primary Key
* Foreign Key
* SQL Queries
* JOIN
* Pandas
* pd.read_sql()
* pd.merge()
* Output Comparison

---

# Conclusion

This project successfully demonstrates a complete data engineering workflow from data collection to analysis. It includes web scraping, preprocessing, relational database design, SQL querying, and pandas-based analysis. The implementation satisfies all assignment requirements and provides a reusable pipeline for processing catalog-style product data.
****

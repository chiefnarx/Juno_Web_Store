# 🛍️ Juno Web Store Data Pipeline

**Juno Web Store** is a data engineering project designed to extract, transform, and load product pricing data from Jumia, an ecommerce platform. Using Python and PostgreSQL, the project performs **static HTML scraping** from multiple pages of laptop listings, and loads the structured dataset into a relational database for further analysis. 

---

## 📌 Project Overview

This project automates product data collection and builds a clean database pipeline from live HTML sources:

✅ Scrape product information from 50 pages of Jumia laptop listings  
✅ Extract titles, current prices, former prices, and discount percentages  
✅ Transform and clean the data using pandas  
✅ Load the structured dataset into PostgreSQL using SQLAlchemy  

---

## ⚙️ Technologies Used

⏺ Python (`requests`, `BeautifulSoup`, `pandas`, `sqlalchemy`) — for scraping and transformation  
⏺ PostgreSQL — target database system  
⏺ HTML Parsing (`lxml`) — used with BeautifulSoup for fast scraping  

---

## 🔄 Full ETL Workflow

### 1. Data Extraction and Scraping

- Fetched catalog pages with `requests`  
- Parsed HTML using BeautifulSoup  
- Extracted:
  - Product titles (`<h3 class="name">`)
  - Current prices (`<div class="prc">`)
  - Former prices (`<div class="old">`)
  - Discount percentages (`<span class="bdg_dsct _dyn -mls">`)

### 2. Data Cleaning and Transformation

- Stored extracted data into Python lists
- Structured the scraped data into a dictionary
- Converted the dictionary into a pandas DataFrame  
- Transposed and validated structure for database insertion  
- Replaced null entries in `former_price` with `'0'` and in `discount_percs` with `'0%'`

### 3. PostgreSQL Database Loading

- Defined DB parameters:
  - Username: `postgres`
  - Password: `MongoDB4luv`
  - Host: `localhost`
  - Port: `5432`
  - Database: `Juno_eCommerce`
- Constructed SQLAlchemy connection URL  
- Used `laptop_df.to_sql()` to load into PostgreSQL

---

## 📄 Results & Final Verification

✅ Successfully scraped product data from 50 catalog pages  
✅ Generated clean and structured DataFrame for laptops  
✅ Created PostgreSQL-ready ingestion pipeline  

---

## 📝 Notes
  
⏺ This scraping pipeline is built for **educational purposes**  
⏺ Additional fields such as brand, rating, or product URLs can be added in future versions  
⏺ Can be extended with Kafka for real-time data ingestion in streaming pipelines


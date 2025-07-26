📊-Zepto-SQL-Project

🔍 SQL-based data analysis project on Zepto’s product dataset. Includes data cleaning, 
inventory insights, revenue analysis, and discount trends to optimize e-commerce operations using PostgreSQL queries.   



🧠 Problem Statement
With the ever-increasing competition in e-commerce and instant delivery platforms, understanding product pricing,
availability, and stock management is critical. Zepto, a 10-minute delivery startup, offers a wide variety of FMCG products,
and optimizing inventory and pricing can drive better customer satisfaction and profitability.

This project aims to:

Analyze product data from Zepto’s inventory

Clean and structure the data using SQL

Derive actionable insights to support inventory decisions, pricing strategy, and sales optimization




🧩 Dataset Overview
The dataset is sourced from Zepto’s online product listing. It includes details such as:

Product name and category

MRP (Maximum Retail Price)

Discounted price and discount %

Weight of product

Availability status

Stock quantity


⚙️ Tools and Technologies

| Tool       | Purpose                     |
| ---------- | --------------------------- |
| PostgreSQL | Data storage and querying   |
| SQL        | Data cleaning and analysis  |
| Excel/CSV  | Initial raw data format     |
| GitHub     | Version control and sharing |


🧾 SQL Workflow Breakdown

1. 🔧 Table Creation
Created the zepto table with relevant fields and data types to mirror the product dataset schema.

<img width="728" height="245" alt="102215" src="https://github.com/user-attachments/assets/18162efa-ace8-4215-91b7-f8aa5dad6a69" />

3. 🔍 Data Exploration
Counted total entries

Identified missing/null values

Discovered unique product categories

Checked duplicates and repeated product names

Analyzed stock status distribution

<img width="960" height="474" alt="102303" src="https://github.com/user-attachments/assets/4aa7b14d-4196-4138-9944-c47ac4aa83ec" />



3. 🧹 Data Cleaning
Removed entries with price = 0

Converted prices from paise to rupees

Checked and handled null or anomalous values

4. 📈 Data Analysis Insights


Q1. Top 10 Best-Value Products by Discount %

   SELECT name, mrp, discountPercent FROM zepto ORDER BY discountPercent DESC LIMIT 10;

<img width="317" height="175" alt="1   103152" src="https://github.com/user-attachments/assets/b85def24-7916-435f-b89b-68a30f2db613" />

Q2. High MRP but Out of Stock Products

    SELECT name, mrp FROM zepto WHERE outOfStock = TRUE AND mrp > 300;

<img width="286" height="140" alt="2  103253" src="https://github.com/user-attachments/assets/13f29b76-e302-45e2-8ee0-820d9fad317f" />

Q3. Estimated Revenue by Category

   SELECT category, SUM(discountedSellingPrice * availableQuantity) AS total_revenue FROM zepto GROUP BY category;
   
<img width="182" height="217" alt="3  103338" src="https://github.com/user-attachments/assets/5361a6f3-e05d-4fe4-ac10-b9a0ea4fbea1" />


Q4. Premium Products with Low Discounts

   SELECT name, mrp, discountPercent FROM zepto WHERE mrp > 500 AND discountPercent < 10;

<img width="317" height="175" alt="4 103152" src="https://github.com/user-attachments/assets/77dce1c1-21ba-4205-8db8-d257ae07112c" />

Q5. Top 5 Categories by Avg. Discount %

   SELECT category, ROUND(AVG(discountPercent),2) AS avg_discount FROM zepto GROUP BY category;
   
<img width="178" height="97" alt="5  102902" src="https://github.com/user-attachments/assets/bb3f0b3a-b292-40d1-becb-338d288d53aa" />


Q6. Price per Gram Analysis

   SELECT name, ROUND(discountedSellingPrice/weightInGms,2) AS price_per_gram FROM zepto WHERE weightInGms >= 100;
   
<img width="506" height="223" alt="6   102715" src="https://github.com/user-attachments/assets/68bae91d-d87e-4586-ac2e-f64fcf08a76d" />


Q7. Weight Categorization

   Grouped products as:

   Low (<1kg)

   Medium (1kg–5kg)

   Bulk (>5kg)
   
<img width="460" height="224" alt="7  102616" src="https://github.com/user-attachments/assets/cf7ed997-f9d3-4905-8d01-2a8335769322" />


Q8. Total Inventory Weight by Category

   SELECT category, SUM(weightInGms * availableQuantity) FROM zepto GROUP BY category;
   
<img width="176" height="217" alt="8  102449" src="https://github.com/user-attachments/assets/1ecaac24-5dfe-44ad-813c-76b4b7d91074" />

   
🧠 Key Learnings

Data Structuring: Learned how to design and normalize tables before importing raw data.

Data Cleaning in SQL: Practical experience handling nulls, conversions, and outlier removal.

Real-World Business Queries: Built and answered questions crucial for e-commerce operations.

SQL Optimization: Used GROUP BY, CASE, and aggregate functions effectively.

Insight Derivation: Converted raw data into meaningful business insights.


| Feature                 | Preview                                         |
| ----------------------- | ----------------------------------------------- |
| Data Cleaning           | ✅ Remove zeros and nulls, format currency       |
| Insight Extraction      | ✅ Revenue, discount, price-per-gram, categories |
| Stock & Weight Analysis | ✅ Product availability and inventory loads      |

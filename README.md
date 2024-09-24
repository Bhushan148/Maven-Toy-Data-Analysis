# 🎯 **Maven Toy Data Analysis**

**A Complete SQL-Based Toy Store Data Analysis Project**

---

## 📌 **Project Overview**

This project is part of **Mentorness Internship Task 2**, where I analyzed toy sales data for **Maven Toys** to uncover key business information related to store performance, product sales, and inventory management.

The dataset consists of **4 tables**: **Inventory**, **Products**, **Sales**, and **Stores**. Using **PostgreSQL**, I structured the data, wrote queries, and addressed **15 business questions** through SQL.

---

## 🛠️ Tools, Skills, and Languages Used

### 🛠️ Tools
- **PostgreSQL**: Used for database management and executing SQL queries.
- **Excel**: Utilized for temporary data analysis and data modeling.
- **Canva**: For creating visually appealing PDF documentation of the project.

### 📚 Skills
- **SQL**: Proficient in writing complex queries to extract and analyze data from relational databases.
- **Data Analysis**: Ability to interpret and derive insights from datasets to inform business decisions.
- **Data Visualization**: Skills in creating visual representations of data for better understanding and presentation of findings.

### 💻 Languages
- **SQL**: The primary language used for querying the database.

### 📢 Showcase
- The project is showcased on various platforms, including:
  - **LinkedIn**: Promoting the project and sharing insights with a professional audience.
  - **GitHub**: Hosting the project repository for public access and collaboration.
  - **Portfolio**: Featuring the project as part of a comprehensive data analytics portfolio.

---


## 📚 Project Resources

### Dataset
- For **Mentorness Task 2**, all the detailed dataset information can be found in the `data/` folder of this repository. This includes CSV files necessary for executing the SQL queries and analyzing the business-related questions.

📥 Download [Google Drive Link](https://drive.google.com/drive/folders/10KCaSU5lJRzQtF76NppOffSaVaj__H8n)


### PDF Documentation
- You can access the comprehensive PDF documentation that includes all problem statements, SQL queries, and sample outputs in the `docs/` folder. This report provides a detailed overview of the project and its findings.

📥 Download [Documentation.pdf](https://github.com/Bhushan148/Maven-Toy-Data-Analysis/blob/main/Maven%20Toy%20Data%20Analysis.pdf)

---

## 📑 **Table of Contents**

- [📁 Project Structure](#Project-Structure)
- [📊 Dataset Details](#dataset-details)
- [🛠️ Database Schema](#database-schema)
- [💡 Problem Statements](#problem-statements)
- [⚙️ Installation and Setup](#installation-and-setup)
- [🚀 How to Run Queries](#how-to-run-queries)
- [📈 Results Overview](#results-overview)
- [📄 PDF Documentation](#pdf-documentation)
- [📞 Contact Information](#contact-information)

---

## 📁 **Project Structure**

```bash
Maven-Toy-Data-Analysis/
│
├── data/                      # 📂 Contains the dataset in CSV format
│   ├── inventory.csv
│   ├── products.csv
│   ├── sales.csv
│   ├── stores.csv
│
├── sql/                       # 🛠️ SQL files for schema and queries
│   ├── schema.sql
│   ├── queries.sql
│
├── docs/                      # 📄 Documentation for the project
│   ├── Documentation.pdf
│
├── README.md                  # 📜 Project overview and instructions
```

---

## 📊 Dataset Details
The dataset includes four key tables representing the toy store’s operations, sales, and products:

### Inventory Table:
- 📍 **Store_ID**: Unique identifier for the store.
- 🧸 **Product_ID**: Unique identifier for the product.
- 🏷️ **Stock_On_Hand**: Number of units available in stock.

### Products Table:
- 🧩 **Product_ID**: Unique identifier for the product.
- 🏷️ **Product_Name**: Name of the product.
- 🎨 **Product_Category**: Category (e.g., educational, plush, action figures).
- 💰 **Product_Cost**: Cost price of the product.
- 💵 **Product_Price**: Selling price of the product.

### Sales Table:
- 🏷️ **Sale_ID**: Unique identifier for the sale.
- 📅 **Sale_Date**: Date of the sale.
- 📍 **Store_ID**: Links to the store table.
- 🧸 **Product_ID**: Links to the product table.
- 📦 **Units**: Number of units sold.

### Stores Table:
- 📍 **Store_ID**: Unique identifier for the store.
- 🏬 **Store_Name**: Name of the store.
- 🌍 **Store_City**: City where the store is located.
- 📅 **Store_Open_Date**: Date the store was opened.


--- 

## 🛠️ Database Schema
The project uses PostgreSQL to model the dataset into a relational database. The following example illustrates the Products and Stores tables:

```sql
-- 🛠️ Products Table
CREATE TABLE Products (
    Product_ID SERIAL PRIMARY KEY,
    Product_Name VARCHAR(100) NOT NULL,
    Product_Category VARCHAR(50) NOT NULL,
    Product_Cost DECIMAL(10, 2) NOT NULL,  -- Adjusted precision
    Product_Price DECIMAL(10, 2) NOT NULL   -- Adjusted precision
);

-- 🏬 Stores Table
CREATE TABLE Stores (
    Store_ID SERIAL PRIMARY KEY,
    Store_Name VARCHAR(100) NOT NULL,
    Store_City VARCHAR(50) NOT NULL,
    Store_Location VARCHAR(50) NOT NULL,
    Store_Open_Date DATE NOT NULL
);

-- Sales_Data Table
CREATE TABLE Sales_Data (
    Sale_ID SERIAL PRIMARY KEY,
    Sale_Date DATE NOT NULL,
    Store_ID INTEGER NOT NULL,
    Product_ID INTEGER NOT NULL,
    Units INTEGER NOT NULL,
    CONSTRAINT fk_store FOREIGN KEY (Store_ID) REFERENCES Stores(Store_ID),
    CONSTRAINT fk_product FOREIGN KEY (Product_ID) REFERENCES Products(Product_ID)
);

-- Inventory Table
CREATE TABLE Inventory (
    Store_ID INTEGER NOT NULL,
    Product_ID INTEGER NOT NULL,
    Stock_On_Hand INTEGER NOT NULL,
    PRIMARY KEY (Store_ID, Product_ID),
    CONSTRAINT fk_store_inventory FOREIGN KEY (Store_ID) REFERENCES Stores(Store_ID),
    CONSTRAINT fk_product_inventory FOREIGN KEY (Product_ID) REFERENCES Products(Product_ID)
);
);
```
---

## 💡 Problem Statements
This project aims to answer 15 business-related questions using SQL queries:

- 💵 **Total Sales Revenue by Store:** What is the total sales revenue generated by each store?
- 📦 **Top-Selling Products:** Which products are the top-selling in terms of units sold?
- 🛍️ **Sales Performance by Category:** What is the sales performance by product category?
- 📊 **Current Inventory Levels:** What are the current inventory levels for each product at each store?
- 📅 **Monthly Sales Trends:** How do monthly sales trends vary across stores?
- 🏆 **Top & Bottom Performing Stores:** Which stores have the highest and lowest sales performance?
- 💰 **Profit Margin by Product:** What is the profit margin for each product?
- 🌍 **Sales Distribution by City:** How are sales distributed across different cities?
- ❌ **Out of Stock Products:** Which products are out of stock in each store?
- 📅 **Sales Trends by Date:** How do sales vary by specific dates?
- 💵 **Average Cost by Product Category:** What is the average cost of products by category?
- 📈 **Sales Growth Over Time:** What is the sales growth over time for the entire company?
- 🏬 **Store Open Date Impact:** How does the store open date affect sales performance?
- 📊 **Sales Contribution by Store:** What percentage of total sales does each store contribute?
- 📦 **Sales vs. Current Stock Levels:** How do sales compare to current stock levels for each product?

---

## ⚙️ Installation and Setup
### Prerequisites
- ✅ PostgreSQL must be installed.
- ✅ Basic knowledge of SQL to execute queries.

### Steps to Install
1. Clone this repository:
    ```bash
    git clone https://github.com/Bhushan148/Maven-Toy-Data-Analysis.git
    ```
2. Navigate to the project directory:
    ```bash
    cd Maven-Toy-Data-Analysis
    ```
3. Set up the database:
   - Use the provided `sql/schema.sql` file to create the database tables.
   - Import the CSV files from the `data/` folder into your PostgreSQL database.

4. Run the Queries:
   - Execute the SQL queries from the `sql/queries.sql` file to analyze the dataset.

---

## 📋 Problem Statements and Queries
Below is a list of all the problem statements along with their corresponding SQL queries:

### 1. What is the total sales revenue generated by each store?
   ```sql
SELECT s.Store_ID AS "Store ID",s.Store_Name AS "Store Name",
          TO_CHAR(SUM(sd.Units * p.Product_Price),'$9,99,999.00') AS "Total Sales Revenue"
FROM Sales_Data sd
JOIN Stores s ON sd.Store_ID = s.Store_ID
JOIN Products p ON sd.Product_ID = p.Product_ID
GROUP BY s.Store_ID, s.Store_Name
ORDER BY SUM(sd.Units * p.Product_Price) DESC;
```

### 2. Which products are the top-selling in terms of units sold?
   ```sql
SELECT p.Product_ID AS "Product ID", p.Product_Name AS "Product Name",
          concat(SUM(sd.Units), ' Units') AS "Total Units Sold"
FROM Sales_Data sd
JOIN Products p ON sd.Product_ID = p.Product_ID
GROUP BY p.Product_ID, p.Product_Name
ORDER BY "Total Units Sold" DESC;
```

### 3. What is the sales performance by product category?
   ```sql
SELECT p.Product_Category AS "Product Category",
        concat('$ ', SUM(sd.Units * p.Product_Price)) AS "Total Sales Revenue"
FROM Sales_Data sd
JOIN Products p ON sd.Product_ID = p.Product_ID
GROUP BY p.Product_Category
ORDER BY "Total Sales Revenue" DESC;
```

### 4. What are the current inventory levels for each product at each store?
   ```sql
SELECT s.Store_ID AS "Store ID", s.Store_Name AS "Store Name", p.Product_ID AS "Product ID",
    p.Product_Name AS "Product Name", i.Stock_On_Hand AS "Current Inventory Level"
FROM Inventory i
JOIN Stores s ON i.Store_ID = s.Store_ID
JOIN Products p ON i.Product_ID = p.Product_ID
ORDER BY s.Store_ID, p.Product_ID;
```

### 5. How do monthly sales trends vary across different stores?
   ```sql
SELECT s.Store_ID AS "Store ID", s.Store_Name AS "Store Name",
	      EXTRACT(YEAR FROM sd.Sale_Date) AS "YEAR", EXTRACT(MONTH FROM sd.Sale_Date) AS "Month Number",
        TO_CHAR(sd.Sale_Date, 'Month') AS "Month Name", SUM(sd.Units * p.Product_Price) AS "Total Sales Revenue"
FROM Sales_Data sd
JOIN Stores s ON sd.Store_ID = s.Store_ID
JOIN Products p ON sd.Product_ID = p.Product_ID
GROUP BY 
    s.Store_ID, s.Store_Name, 
		EXTRACT(YEAR FROM sd.Sale_Date), 
	  EXTRACT(MONTH FROM sd.Sale_Date), 
		TO_CHAR(sd.Sale_Date, 'Month')
ORDER BY 
    s.Store_ID, "YEAR","Month Number";
```

### 6. Which stores have the highest and lowest sales performance?
   ```sql
WITH Sales_Performance AS (
    SELECT 
        s.Store_ID AS "Store ID",
        s.Store_Name AS "Store Name",
        SUM(sd.Units * p.Product_Price) AS "Total Sales Revenue"
    FROM 
        Sales_Data sd
    JOIN 
        Stores s ON sd.Store_ID = s.Store_ID
    JOIN 
        Products p ON sd.Product_ID = p.Product_ID
    GROUP BY 
        s.Store_ID, s.Store_Name)
-- Retrieve highest and lowest performing stores with labels
SELECT 
    sp."Store ID", 
    sp."Store Name", 
    sp."Total Sales Revenue",
    CASE
        WHEN sp."Total Sales Revenue" = 
			(SELECT MAX("Total Sales Revenue") FROM Sales_Performance) THEN 'Highest'
        WHEN sp."Total Sales Revenue" = 
			(SELECT MIN("Total Sales Revenue") FROM Sales_Performance) THEN 'Lowest'
    END AS "Performance"
FROM 
    Sales_Performance sp
WHERE 
    sp."Total Sales Revenue" = (SELECT MAX("Total Sales Revenue") FROM Sales_Performance)
    OR sp."Total Sales Revenue" = (SELECT MIN("Total Sales Revenue") FROM Sales_Performance);
```

### 7. What is the profit margin for each product?
   ```sql
SELECT 
    Product_ID AS "Product ID", 
    Product_Name AS "Product Name", 
    Product_Cost AS "Cost Price", 
    Product_Price AS "Selling Price", 
    concat(round(((Product_Price - Product_Cost) /
		Product_Price) * 100,2),' %') AS "Profit Margin (%)"
FROM 
    Products;
```

### 8. How are sales distributed across different cities?
   ```sql
SELECT 
    s.Store_City AS "City",  -- Store ka city
    concat('$ ', SUM(sd.Units * p.Product_Price)) AS "Total Sales Revenue"
FROM 
    Sales_Data sd
JOIN 
    Stores s ON sd.Store_ID = s.Store_ID
JOIN 
    Products p ON sd.Product_ID = p.Product_ID 
GROUP BY 
    s.Store_City
ORDER BY 
    "Total Sales Revenue" DESC;
```

### 9. Which products are out of stock in each store?
   ```sql
SELECT 
    s.Store_Name AS "Store Name", 
    p.Product_Name AS "Product Name", 
	case when i.stock_on_hand = 0 then 'Out Of Stock'
			else 'Available' end as "Stock Status"
FROM 
    Inventory i
JOIN 
    Stores s ON i.Store_ID = s.Store_ID  
JOIN 
    Products p ON i.Product_ID = p.Product_ID  
WHERE 
    i.Stock_On_Hand = 0; 
```

### 10. How do sales vary by specific dates?
   ```sql
SELECT 
    sd.Sale_Date AS "Sale Date",
    SUM(sd.Units) AS "Total Units Sold",  
    SUM(sd.Units * p.Product_Price) AS "Total Sales Revenue" 
FROM 
    Sales_Data sd
JOIN 
    Products p ON sd.Product_ID = p.Product_ID  
GROUP BY 
    sd.Sale_Date 
ORDER BY 
    sd.Sale_Date; 
```

### 11. What is the average cost of products in each category?
   ```sql
SELECT 
    p.Product_Category AS "Product Category", 
    concat('$ ',(round(AVG(p.Product_Cost),2))) AS "Average Cost"
FROM 
    Products p
GROUP BY 
    p.Product_Category 
ORDER BY 
    "Average Cost" DESC;
```

### 12. What is the total sales revenue generated by each store?
   ```sql
SELECT 
    TO_CHAR(sd.Sale_Date, 'YYYY-MM') AS "Month", 
    SUM(sd.Units * p.Product_Price) AS "Total Sales Revenue",  
    LAG(SUM(sd.Units * p.Product_Price)) OVER (ORDER BY TO_CHAR(sd.Sale_Date, 'YYYY-MM')) AS "Previous Month Sales", 
    concat(round((SUM(sd.Units * p.Product_Price) - LAG(SUM(sd.Units * p.Product_Price)) OVER (ORDER BY TO_CHAR(sd.Sale_Date, 'YYYY-MM'))) / NULLIF(LAG(SUM(sd.Units * p.Product_Price)) OVER (ORDER BY TO_CHAR(sd.Sale_Date, 'YYYY-MM')), 0) * 100,2), ' %') AS "Sales Growth (%)"  -- Sales growth percentage
FROM 
    Sales_Data sd
JOIN 
    Products p ON sd.Product_ID = p.Product_ID
GROUP BY 
    TO_CHAR(sd.Sale_Date, 'YYYY-MM') 
ORDER BY 
    "Month";  
```

### 13. How does the store open date affect sales performance?
   ```sql
SELECT 
    s.Store_Open_Date AS "Store Open Date",
    s.Store_Name AS "Store Name",          
    EXTRACT(YEAR FROM s.Store_Open_Date) AS "Open Year", 
    SUM(sd.Units * p.Product_Price) AS "Total Sales Revenue" 
FROM 
    Sales_Data sd
JOIN 
    Stores s ON sd.Store_ID = s.Store_ID 
JOIN 
    Products p ON sd.Product_ID = p.Product_ID 
GROUP BY 
    s.Store_Open_Date, s.Store_Name 
ORDER BY 
    "Open Year" ASC, "Total Sales Revenue" DESC; 
```

### 14. What percentage of total sales does each store contribute?
   ```sql
SELECT 
    s.Store_Name AS "Store Name", 
    SUM(sd.Units * p.Product_Price) AS "Store Sales", 
    ROUND((SUM(sd.Units * p.Product_Price) /
         (SELECT SUM(sd2.Units * p2.Product_Price) 
           FROM Sales_Data sd2 
           JOIN Products p2 ON sd2.Product_ID = p2.Product_ID)) * 100, 2) AS "Sales Percentage (%)" 
FROM 
    Sales_Data sd
JOIN 
    Stores s ON sd.Store_ID = s.Store_ID 
JOIN 
    Products p ON sd.Product_ID = p.Product_ID 
GROUP BY 
    s.Store_Name  
ORDER BY 
    "Sales Percentage (%)" DESC; 
```

### 1. How do sales compare to current stock levels for each product?
SELECT 
   ```sql
SELECT 
    p.Product_Name AS "Product Name", 
    SUM(sd.Units) AS "Total Units Sold",  
    i.Stock_On_Hand AS "Current Stock Level",
    (i.Stock_On_Hand - SUM(sd.Units)) AS "Stock After Sales" 
FROM 
    Sales_Data sd
JOIN 
    Products p ON sd.Product_ID = p.Product_ID 
JOIN 
    Inventory i ON p.Product_ID = i.Product_ID 
GROUP BY 
    p.Product_Name, i.Stock_On_Hand 
ORDER BY 
    "Stock After Sales" ASC; 
```

---

## 📈 Results Overview
Here’s an overview of some key findings:

- 🏆 **Top Store:** Maven Toys Ciudad de Mexico 2 had the highest total sales revenue.
- 🧸 **Best-Selling Product:** Barrel O' Slime sold the most units.
- 💰 **Highest Profit Margin:** Chutes & Ladders had the highest profit margin (84.68%).
- 📅 **Seasonal Sales:** Higher sales were observed during holiday seasons.
- ❌ **Inventory:** Several products were out of stock due to high demand.


--- 

## 📄 PDF Documentation
You can find a detailed PDF report in the `docs/` folder, which includes all problem statements, SQL queries, and sample outputs.

📥 Download [Documentation.pdf](https://github.com/Bhushan148/Maven-Toy-Data-Analysis/blob/main/Maven%20Toy%20Data%20Analysis.pdf)

---

## 📞 Contact Information
If you have any questions or feedback about this project, feel free to reach out:

- 📧 **Email:** bhushanjg14@gmail.com
- 🌐 **LinkedIn:** [Bhushan Gawali](https://www.linkedin.com/in/bhushan-gawali-97b645233?utm_source=share&utm_campaign=share_via&utm_content=profile&utm_medium=android_app)
- 🐙 **WhatsApp:** [+91 7787885757](https://wa.me/qr/45BQWP6TQQ24M1)


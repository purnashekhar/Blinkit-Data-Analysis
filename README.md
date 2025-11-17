Sure! Here is the **clean, copy-paste ready README** exactly as you need it for GitHub.
Just **select all → copy → paste into your README.md**.

---

# 📊 **Blinkit Data Analysis — SQL + Power BI Project**

A complete end-to-end data analytics project combining **SQL data cleaning & analysis** with an **interactive Power BI dashboard** to uncover sales trends, customer behavior, outlet performance, and business insights.

---

## 🧭 **Project Overview**

This project analyzes the **Blinkit Sales Dataset** using:

* **SQL** for data cleaning, preprocessing, optimization, and exploratory data analysis
* **Power BI** for creating an interactive dashboard with KPIs, charts, filters, and business insights

This demonstrates a **real-world analytics workflow**, from raw data to insights.

---

# 🗃️ **1. SQL Data Cleaning & Preprocessing**

SQL was used to prepare the raw dataset by:

### ✔ Renaming inconsistent columns

### ✔ Standardizing categorical values

### ✔ Converting text columns into numeric formats

### ✔ Optimizing data types (DECIMAL, YEAR, ENUM, VARCHAR)

### ✔ Removing data quality issues before visualization

### 🔧 Key SQL Cleaning Steps

#### Rename incorrect column

```sql
ALTER TABLE blinkit_data 
RENAME COLUMN `item_Fat_Content` TO Item_Fat_Content;
```

#### Standardize fat content values

```sql
UPDATE blinkit_data
SET Item_Fat_Content = 
    CASE 
        WHEN Item_Fat_Content IN ('LF', 'low fat') THEN 'Low Fat'
        WHEN Item_Fat_Content = 'reg' THEN 'Regular'
        ELSE Item_Fat_Content
    END;
```

#### Optimize data types

```sql
ALTER TABLE blinkit_data
MODIFY COLUMN Item_Fat_Content ENUM('Low Fat','Regular'),
MODIFY COLUMN Item_Identifier VARCHAR(10),
MODIFY COLUMN Item_Type VARCHAR(50),
MODIFY COLUMN Outlet_Establishment_Year YEAR,
MODIFY COLUMN Outlet_Identifier VARCHAR(10),
MODIFY COLUMN Outlet_Location_Type ENUM('Tier 1','Tier 2','Tier 3'),
MODIFY COLUMN Outlet_Size ENUM('Small','Medium','High'),
MODIFY COLUMN Outlet_Type VARCHAR(50),
MODIFY COLUMN Item_Visibility DECIMAL(5,4),
MODIFY COLUMN Item_Weight DECIMAL(6,2),
MODIFY COLUMN Total_Sales DECIMAL(10,2),
MODIFY COLUMN Rating DECIMAL(3,1);
```

---

# 📌 **2. SQL KPI Calculations**

### 💰 Total Sales (in Millions)

```sql
SELECT CAST(SUM(Total_Sales)/1000000.0 AS DECIMAL(10,2)) AS Total_Sales_Million 
FROM blinkit_data;
```

### 💵 Average Sales

```sql
SELECT CAST(AVG(Total_Sales) AS DECIMAL(10,0)) AS Avg_Sales 
FROM blinkit_data;
```

### 📦 Total Items Sold

```sql
SELECT COUNT(*) AS No_of_Items FROM blinkit_data;
```

### ⭐ Average Rating

```sql
SELECT CAST(AVG(Rating) AS DECIMAL(10,1)) AS Avg_Rating 
FROM blinkit_data;
```

---

# 🔍 **3. SQL Exploratory Data Analysis (EDA)**

### 🥗 Total Sales by Fat Content

```sql
SELECT Item_Fat_Content, SUM(Total_Sales) AS Total_Sales
FROM blinkit_data
GROUP BY Item_Fat_Content;
```

### 🍎 Total Sales by Item Type

```sql
SELECT Item_Type, SUM(Total_Sales)
FROM blinkit_data
GROUP BY Item_Type
ORDER BY SUM(Total_Sales) DESC;
```

### 🏙️ Fat Content by Outlet Location (Pivot Style)

```sql
SELECT Outlet_Location_Type,
SUM(CASE WHEN Item_Fat_Content='Low Fat' THEN Total_Sales ELSE 0 END) AS Low_Fat,
SUM(CASE WHEN Item_Fat_Content='Regular' THEN Total_Sales ELSE 0 END) AS Regular
FROM blinkit_data
GROUP BY Outlet_Location_Type;
```

### 📅 Sales by Outlet Establishment Year

```sql
SELECT Outlet_Establishment_Year, SUM(Total_Sales)
FROM blinkit_data
GROUP BY Outlet_Establishment_Year
ORDER BY Outlet_Establishment_Year;
```

### 🏬 Sales % by Outlet Size

```sql
SELECT Outlet_Size,
ROUND(SUM(Total_Sales),2) AS Total_Sales,
ROUND((SUM(Total_Sales)*100.0 / SUM(SUM(Total_Sales)) OVER()),2) AS Sales_Percentage
FROM blinkit_data
GROUP_BY Outlet_Size;
```

---

# 📊 **4. Power BI Dashboard**

After SQL cleaning, the dataset was loaded into **Power BI** to build a modern, interactive dashboard.

### 🎯 Key KPIs

| KPI                 | Description          | Value       |
| ------------------- | -------------------- | ----------- |
| 💰 Total Sales      | Total revenue        | **$1.20M**  |
| 💵 Average Sales    | Avg revenue per item | **$141**    |
| 📦 Total Items Sold | Count of items       | **8,523**   |
| ⭐ Average Rating    | Customer rating      | **3.9 / 5** |

---

# 🧩 **5. Dashboard Features**

✔ **Filter Panel** (Outlet Location Type, Outlet Size, Item Type)
✔ **Outlet Establishment Trend** (2012–2022)
✔ **Fat Content Analysis** (Low Fat vs Regular)
✔ **Item Type Distribution** (top-selling categories)
✔ **Outlet Size & Location Performance**
✔ **Outlet Type Comparison** (metrics across outlet types)

---
<img width="1427" height="776" alt="Blinkit dashboard image" src="https://github.com/user-attachments/assets/8b3b62e1-eaa9-411a-8109-c967df05d2ec" />


# 📈 **6. Insights & Conclusions**

### Key Findings

* Total sales cross **$1 Million**
* Customers prefer **Low Fat** products
* **Fruits, Vegetables, and Snacks** lead in revenue
* **Medium-sized outlets** perform the best
* **Tier-3 cities** generate high demand
* **Supermarkets** outperform traditional grocery stores
* Grocery stores have high visibility but lower sales

### Business Recommendations

* Increase stock of low-fat items
* Expand medium-sized outlets in Tier-3 regions
* Improve visibility in lower-performing outlets
* Focus on top-performing item categories
* Enhance customer ratings through product quality initiatives

---

# 🛠️ **Tools & Technologies Used**

* **MySQL** — Cleaning, transformation, EDA
* **Power BI** — Dashboard visualization
* **Excel** — Preprocessing
* **DAX** — KPI calculations
* **SQL Window Functions** — Advanced analysis

---

# 👨‍💻 **Author**

**Bandi Purna Shekhar**
*Data Analyst — SQL | Power BI | Excel | Python*

📧 Email: [purnashekhar2352@gmail.com](mailto:purnashekhar2352@gmail.com)
🔗 LinkedIn: [www.linkedin.com/in/bandi-purna-shekhar](http://www.linkedin.com/in/bandi-purna-shekhar)
🔗 GitHub: *Your GitHub link here*

⭐ If you like this project, please consider giving it a star! ⭐

---

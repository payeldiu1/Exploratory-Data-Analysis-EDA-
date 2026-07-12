# Sales Performance Dashboard: Revenue, Profitability & Product Insights

**Tools:** Python · PySpark SQL · Pandas · NumPy · Matplotlib · Seaborn
**Dataset:** [Sample Supermarket Dataset — Kaggle](https://www.kaggle.com/datasets/bravehart101/sample-supermarket-dataset)

---

## 1. Business Problem

A retail company wants to analyze its sales performance to identify revenue trends, top-performing products, customer behavior, and profit opportunities. This analysis uses Python, PySpark SQL, Pandas, NumPy, Matplotlib, and Seaborn to explore the dataset and answer the business questions below.

## 2. Business Questions

1. What are the total sales, profit, and quantity sold?
2. Which regions generate the highest revenue?
3. Which product categories are the most profitable?
4. Which segments have the highest sales?
5. Which products should be promoted or discontinued?

## 3. Dataset

| | |
|---|---|
| **Source** | Kaggle — [Sample Supermarket Dataset](https://www.kaggle.com/datasets/bravehart101/sample-supermarket-dataset) |
| **Fields** | `Ship Mode`, `Segment`, `Country`, `City`, `State`, `Postal Code`, `Region`, `Category`, `Sub-Category`, `Sales`, `Quantity`, `Discount`, `Profit` |

## 4. Data Cleaning

The following preprocessing steps were performed before analysis:

- Removed duplicate records
- Handled missing values

---

## 5. Exploratory Data Analysis (EDA)

### 5.1 Which regions generate the highest revenue?

```sql
SELECT Region, sum(Profit) AS Profit
FROM sales
GROUP BY Region
ORDER BY Profit DESC
```

| Region | Profit |
|---|---:|
| West | $108,418.45 |
| East | $91,522.78 |
| South | $46,749.43 |
| Central | $39,706.36 |

<img width="876" height="584" alt="image" src="https://github.com/user-attachments/assets/40762525-7f88-4373-9ac8-7b04705fc23a" />

*Figure 1. Total Profit by Region — West leads by a wide margin, generating roughly 2.7x the profit of Central, the lowest-performing region.*

```python
pdf = result.toPandas()
pdf.plot(x='Region', y='Profit', kind='bar', figsize=(10, 6))
plt.title("Total Profit by Region")
plt.xlabel("Region")
plt.ylabel("Total Profit")
plt.show()
```

---

### 5.2 Which product categories are the most profitable?

```sql
SELECT Category, sum(Profit) AS Profit
FROM sales
GROUP BY Category
ORDER BY Profit DESC
```

| Category | Profit |
|---|---:|
| Technology | $145,454.95 |
| Office Supplies | $122,490.80 |
| Furniture | $18,451.27 |

<img width="876" height="637" alt="image" src="https://github.com/user-attachments/assets/b324d41c-0ddc-4396-a090-0c3522e087ed" />

*Figure 2. Total Profit by Category — Technology and Office Supplies together account for the large majority of total profit; Furniture contributes comparatively little.*

```python
pdf = result.toPandas()
pdf.plot(x='Category', y='Profit', kind='bar', figsize=(10, 6))
plt.title("Total Profit by Categories")
plt.xlabel("Categories")
plt.ylabel("Total Profit")
plt.show()
```

---

### 5.3 Which segments have the highest sales?

```sql
SELECT Segment, sum(Sales)/1000000 AS Sales
FROM sales
GROUP BY Segment
ORDER BY Sales DESC
```

| Segment | Sales (Million USD) |
|---|---:|
| Consumer | $1.16M |
| Corporate | $0.71M |
| Home Office | $0.43M |

<img width="910" height="547" alt="image" src="https://github.com/user-attachments/assets/70858a6b-1e7f-47d6-bf16-fe3dd0b20367" />


*Figure 3. Total Sales by Segment — Consumer is the dominant segment, generating more revenue than Corporate and Home Office combined.*

```python
pdf = result.toPandas()
pdf.plot(x='Segment', y='Sales', kind='barh', figsize=(10, 6))
plt.title("Total Sales by Segment")
plt.xlabel("Total Sales (million)")
plt.ylabel("Segment")
plt.show()
```

---

### 5.4 Which products should be promoted or discontinued?

```sql
SELECT `Sub-Category` AS Product, sum(Quantity) AS Quantity
FROM sales
GROUP BY `Sub-Category`
ORDER BY Quantity ASC
LIMIT 5
```

| Product | Quantity Sold |
|---|---:|
| Copiers | 234 |
| Machines | 440 |
| Supplies | 647 |
| Bookcases | 868 |
| Envelopes | 906 |

![Top 5 Lowest-Selling Products](charts/04_lowest_selling_products.png)

*Figure 4. Top 5 Lowest-Selling Sub-Categories by Quantity — Copiers, Machines, and Supplies move the least volume and are the strongest candidates for promotion or discontinuation review.*

```python
pdf = result.toPandas()
pdf.plot(x='Product', y='Quantity', kind='barh', figsize=(10, 6))
plt.title("Top 5 Lowest Sold Products")
plt.xlabel("Total Quantity")
plt.ylabel("Product")
plt.show()
```

---

## 6. Key Insights

- **Regional gap:** West outperforms every other region in profit; Central lags furthest behind, warranting a review of pricing, discounting, or logistics costs in that region.
- **Category concentration:** Technology and Office Supplies drive the overwhelming majority of profit. Furniture's low contribution suggests thin margins relative to its likely inventory footprint.
- **Segment reliance:** The Consumer segment is the primary revenue engine — retention and loyalty efforts here have outsized impact.
- **Low-velocity products:** Copiers, Machines, and Supplies sell in the lowest volumes and should be evaluated for targeted promotions or phased discontinuation.

## 7. Recommendations

1. Investigate discount and cost structures in the Central and South regions to close the profit gap with West and East.
2. Reassess Furniture pricing and margins — determine whether shipping, returns, or discounting is eroding profitability.
3. Pilot bundling or seasonal promotions for Copiers and Machines before considering discontinuation.
4. Prioritize Consumer-segment marketing and retention given its outsized share of total sales.

---

*Report generated from EDA notebook — charts reconstructed from source query outputs for portability.*


# Project 5: Sales Performance Dashboard with Python
# Business Problem

A retail company wants to analyze its sales performance to identify revenue trends, top-performing products, customer behavior, and profit opportunities. This analysis is performed by Python, pysql, pandas,numpy, matplotlib, seaborn 
pyspark.sql 

# Business Questions
What are the total sales, profit, and quantity sold?
Which regions generate the highest revenue?
Which product categories are the most profitable?
Which Segments have the highest sales?
Which products should be promoted or discontinued?


# Dataset
Source: Kaggle –
https://www.kaggle.com/datasets/bravehart101/sample-supermarket-dataset

# Dataset Includes:
Ship Mode', 'Segment', 'Country', 'City', 'State', 'Postal Code',
       'Region', 'Category', 'Sub-Category', 'Sales', 'Quantity', 'Discount',
       'Profit'

# Data Cleaning
The following preprocessing steps were performed before analysis:

Removed duplicate records
Handled missing values

# Exploratory Data Analysis (EDA)
The analysis includes:
What are the total sales, profit, and quantity sold?
Which regions generate the highest revenue?
Which product categories are the most profitable?
Which Segments have the highest sales?
Which products should be promoted or discontinued?


What are the total sales, profit, and quantity sold?
# Which regions generate the highest revenue

result = spark.sql("SELECT Region, sum(Profit) Profit FROM sales group by Region order by 2 desc")

# 6. Show results
result.show(100)

+-------+------------------+
| Region|            Profit|
+-------+------------------+
|   West| 108418.4489000001|
|   East|          91522.78|
|  South|46749.430300000015|
|Central| 39706.36250000001|
+-------+------------------+

pdf = result.toPandas()
#region wise profit bar chart from spark df
pdf.plot(x='Region', y='Profit', kind='bar', figsize=(10,6))
plt.title("Total Profit by Region")
plt.xlabel("Region")
plt.ylabel("Total Profit")
plt.show()


# region wise profit bar chart from original pandas df
df_region_profit = df.groupby('Region')['Profit'].sum()

df_region_profit.plot(x='Region', y='Profit', kind='bar', figsize=(10,6))
plt.title("Total Profit by Region")
plt.xlabel("Region")
plt.ylabel("Total Profit")
plt.show()

<img width="876" height="584" alt="image" src="https://github.com/user-attachments/assets/54c7a9b9-3242-4698-92ec-5abe717bcbe8" />

# Which product categories are the most profitable?

result = spark.sql("SELECT Category, sum(Profit) Profit FROM sales group by Category order by 2 desc")

# 6. Show results
result.show(100)

+---------------+------------------+
|       Category|            Profit|
+---------------+------------------+
|     Technology|145454.94810000007|
|Office Supplies|122490.80079999997|
|      Furniture|18451.272799999984|
+---------------+------------------+

pdf = result.toPandas()
pdf.plot(x='Category', y='Profit', kind='bar', figsize=(10,6))
plt.title("Total Profit by Categories")
plt.xlabel("Categories")
plt.ylabel("Total Profit")
plt.show()


# Which Segments have the highest sales? 
result = spark.sql("SELECT Segment, sum(Sales)/1000000 Sales FROM sales group by Segment order by 2 desc")

# 6. Show results
result.show(100)

+-----------+------------------+
|    Segment|             Sales|
+-----------+------------------+
|   Consumer|1.1614013449999985|
|  Corporate|0.7061463668000004|
|Home Office|0.4296531484999999|
+-----------+------------------+

pdf = result.toPandas()
pdf.plot(x='Segment', y='Sales', kind='barh', figsize=(10,6))
plt.title("Total Sales by Segment")
plt.xlabel("Total Sales(million)")
plt.ylabel("Segment ")
plt.show()



#Which products should be promoted or discontinued?
# Find the top lowest sale product
result = spark.sql("SELECT `Sub-Category` Product, sum(Quantity) Quantity FROM sales group by `Sub-Category` order by 2 asc LIMIT 5")

# 6. Show results
result.show(100)

+---------+--------+
|  Product|Quantity|
+---------+--------+
|  Copiers|     234|
| Machines|     440|
| Supplies|     647|
|Bookcases|     868|
|Envelopes|     906|
+---------+--------+

pdf = result.toPandas()
pdf.plot(x='Product', y='Quantity', kind='barh', figsize=(10,6))
plt.title("Top 5 Lowest saled product")
plt.xlabel("Total Quantity")
plt.ylabel("Product ")
plt.show()

![Uploading image.png…]()


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

<img width="876" height="584" alt="image" src="https://github.com/user-attachments/assets/40762525-7f88-4373-9ac8-7b04705fc23a" />

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

<img width="876" height="637" alt="image" src="https://github.com/user-attachments/assets/b324d41c-0ddc-4396-a090-0c3522e087ed" />

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

<img width="910" height="547" alt="image" src="https://github.com/user-attachments/assets/70858a6b-1e7f-47d6-bf16-fe3dd0b20367" />


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


# Project 1: Canadian Housing Price Analysis using Python

## Objective
Understand the factors influencing housing prices across Canada and identify regional differences.

## Business Problem
A real estate company wants to answer:
- **What factors influence house prices?**
- **Which provinces/cities are more expensive?**

## Steps
1. **Data Collection**  
   - Gather housing data (price, area, bedrooms, bathrooms, region, etc.).
Data gathering from https://www.kaggle.com/datasets/yuliiabulana/canada-housing?resource=download&select=data_on.csv

2. **Data Cleaning**  
   - Handle missing values, duplicates, and outliers.

3. **Exploratory Data Analysis (EDA)**  
   - **Price Distribution**: Histogram and log-transformed plots.  
   - **Regional Analysis**: Average prices by province/city.  
   - **Feature Relationships**: Correlation heatmaps, scatter plots (Area vs Price, Beds vs Price).
  
   # Price Distribution
   sns.histplot(df["price"])

   plt.show()

<img width="580" height="432" alt="image" src="https://github.com/user-attachments/assets/974b0d7d-5a4d-405c-9c23-2b9553b624b8" />

#If skewed (as your earlier plot shows), apply log transformation:

#Price Distribution

sns.histplot(np.log1p(df["price"]), kde=True)

plt.title("Log-Transformed Price Distribution")

plt.show()
<img width="580" height="455" alt="image" src="https://github.com/user-attachments/assets/779abe97-920c-46ac-ada6-f2d4f3a75363" />

# Regional Analysis**: Average prices by province/city.

df.groupby("addressRegion")["price"].mean().sort_values(ascending=True)
<img width="269" height="325" alt="image" src="https://github.com/user-attachments/assets/37d49967-c0bd-4f2f-aa29-d6d7e7adfbf2" />

# Feature Relationships: bar chart.

df.groupby("addressRegion")["price"].mean().plot(kind="bar")

<img width="547" height="455" alt="image" src="https://github.com/user-attachments/assets/1dfd4a42-e432-454f-bd24-388c08f4e5d2" />

# Feature Relationships**: Correlation heatmaps, scatter plots (Area vs Price, Beds vs Price).
plt.figure(figsize=(12,8))

sns.heatmap(df.corr(numeric_only=True), annot=True)

plt.show()
<img width="1150" height="908" alt="image" src="https://github.com/user-attachments/assets/059e0bde-e321-4bd6-92bf-1cca84566cac" />
# Correlation Area vs Price, Beds vs Price).
df.corr(numeric_only=True)["price"].sort_values(ascending=False)


<img width="297" height="356" alt="image" src="https://github.com/user-attachments/assets/a947e694-b9a6-4a98-8189-c8a3cf333ae0" />

sns.scatterplot(data=df, x="property-beds", y="price", hue="addressRegion")

plt.title("Price vs. Bedrooms by Region")

plt.show()

<img width="567" height="455" alt="image" src="https://github.com/user-attachments/assets/fffa8c99-bfac-4eb6-8db9-4ed6e9a9192a" />


5. **Key takeaways**  
   **Summarize findings:
   -Price distribution is right-skewed.
   -Certain regions show higher average prices.
   -Strong correlation between property size and price.

## Deliverables
- Clean dataset ready for analysis.  
- Visualizations (histograms, scatter plots, heatmaps).  
- Insights report highlighting key factors and regional differences.

Script Link: https://colab.research.google.com/drive/13lfCWMED5cFlAdlOM4lw9hGBIQTaXSvP?usp=sharing

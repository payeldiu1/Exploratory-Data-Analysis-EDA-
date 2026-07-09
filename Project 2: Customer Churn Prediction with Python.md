# Telecom Customer Churn Analysis

## 📌 Business Problem
A telecom company wants to predict which customers are likely to leave (churn) so it can proactively retain them.

## ❓ Business Questions
- Which customers are most likely to churn?
- What factors influence or contribute to churn?
- Can we build a model to predict churn accurately?

---

## 📊 Steps

### 1. Data Collection
- Gathered Telecom Customer Churn Prediction data
- Source: https://github.com/YBIFoundation/Dataset/raw/main/TelecomCustomerChurn.csv

- ## 📊 Dataset Features

| Feature              | Description                                                                 |
|-----------------------|-----------------------------------------------------------------------------|
| **customerID**        | Unique identifier for each customer                                         |
| **Gender**            | Male or Female                                                             |
| **SeniorCitizen**     | Indicates if the customer is a senior citizen (1 = Yes, 0 = No)            |
| **Partner**           | Whether the customer has a partner                                          |
| **Dependents**        | Whether the customer has dependents                                         |
| **Tenure**            | Number of months the customer has stayed with the company                   |
| **PhoneService**      | Whether the customer has a phone service                                    |
| **MultipleLines**     | Whether the customer has multiple phone lines                               |
| **InternetService**   | Type of internet service (DSL, Fiber optic, None)                           |
| **OnlineSecurity**    | Whether the customer has online security service                            |
| **OnlineBackup**      | Whether the customer has online backup service                              |
| **DeviceProtection**  | Whether the customer has device protection service                          |
| **TechSupport**       | Whether the customer has tech support service                               |
| **StreamingTV**       | Whether the customer has streaming TV service                               |
| **StreamingMovies**   | Whether the customer has streaming movies service                           |
| **Contract**          | Type of contract (Month-to-month, One year, Two year)                       |
| **PaperlessBilling**  | Whether the customer uses paperless billing                                 |
| **PaymentMethod**     | Customer’s payment method (Electronic check, Credit card, Bank transfer, etc.) |
| **MonthlyCharges**    | Monthly charges incurred by the customer                                    |
| **TotalCharges**      | Total charges incurred by the customer                                      |
| **Churn**             | Target variable (Yes = customer left, No = customer stayed)                 |


### 2. Data Cleaning
- Handled missing values, duplicates, and outliers to ensure data quality.

### 3. Exploratory Data Analysis (EDA)
- **Price Distribution**: Count plots show right-skewed churn distribution.
- **Gender Analysis**: Gender-wise churn distribution examined.
- **Contract Analysis**: Contract type vs churn distribution analyzed.
- **Feature Relationships**: Correlation heatmaps used to identify relationships.

#### 🔑 Correlation with Churn
| Feature          | Correlation with Churn |
|------------------|-------------------------|
| Churn            | 1.000000                |
| MonthlyCharges   | 0.193356                |
| SeniorCitizen    | 0.150889                |
| Tenure           | -0.352229               |

---

## 📌 Key Takeaways
- Churn distribution is **right-skewed**.
- Customers with **monthly contracts** show higher churn.
- **Tenure (-0.35)** has the strongest relationship with churn — longer service duration reduces churn.
- **MonthlyCharges (0.19)** and **SeniorCitizen (0.15)** have weak positive relationships with churn.

---

## 💡 Business Insights
- **Tenure** is the most important predictor: long-term customers are more loyal and less likely to leave.
- **Expensive plans** (higher monthly charges) slightly increase churn risk.
- **Senior citizens** are marginally more likely to churn, but the effect is small.
- Overall, **retention strategies should focus on increasing tenure** (e.g., loyalty programs, long-term contracts).

---

## ✅ Conclusion
Correlation analysis highlights **Tenure** as the strongest predictor of churn.  
A predictive model can be built using tenure, monthly charges, and demographic features to identify at-risk customers and design targeted retention strategies.

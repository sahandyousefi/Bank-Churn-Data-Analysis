# Bank-Churn-Data-Analysis
This is the SQL queries from simple to advance to find hidden secrets in the dataset!

# Bank Customer Churn Analysis Using SQL

## Overview
This project analyzes customer churn from a banking dataset using SQL queries. It provides insights into customer behaviors, churn trends, and potential risk factors influencing customer retention. The dataset contains customer demographics, account balances, activity status, and churn indicators.

## Features
- Data Exploration
- Customer Segmentation
- Churn Rate Analysis
- Risk Assessment & Prediction
- Revenue Estimation

## SQL Queries Covered
- **Basic Queries**: Retrieving customer information, filtering by country, and balance thresholds.
- **Aggregations & Grouping**: Analyzing churn rates per country, gender, and age group.
- **Advanced Analysis**: Identifying high-risk customers, percentile-based balance segmentation.
- **Statistical & Predictive Insights**: Weighted churn scoring, customer lifetime value estimation.

## Dataset
- **Table Name**: `BankCustomerChurnPrediction`
- **Columns**:
  - `CustomerID`: Unique customer identifier
  - `Country`: Customer's country of residence
  - `Gender`: Male/Female
  - `Age`: Customer's age
  - `Balance`: Account balance
  - `IsActive`: Customer activity status (1 = Active, 0 = Inactive)
  - `Churn`: Whether the customer churned (1 = Yes, 0 = No)

## Setup & Usage
1. Upload the dataset to an SQL environment such as SQLite Online, MySQL Workbench, or Azure SQL.
2. Run the queries provided in `queries.sql`.
3. Modify the queries to explore additional insights and customize the analysis.

## Key Insights
- **Customers with high balances tend to churn less.**
- **Inactive customers have a significantly higher churn rate.**
- **Older customers with low balances are at higher risk of churn.**
- **Churn likelihood can be estimated using a weighted scoring method.**

## How to Contribute
Feel free to fork this repository, enhance the queries, and add new analyses!



## Author
Sahand

---

** Ready to explore? Run the queries and gain valuable business insights!**


-- Advanced & Complex SQL Queries for Bank Customer Churn Analysis

-- 1. View first 10 rows
SELECT * FROM BankCustomerChurnPrediction LIMIT 10;

-- 2. Count total customers
SELECT COUNT(*) FROM BankCustomerChurnPrediction;

-- 3. Find all customers from 'France'
SELECT * FROM BankCustomerChurnPrediction WHERE Country = 'France';

-- 4. Find customers with a balance over $50,000
SELECT * FROM BankCustomerChurnPrediction WHERE Balance > 50000;

-- 5. Count active vs inactive customers
SELECT IsActive, COUNT(*) AS total FROM BankCustomerChurnPrediction GROUP BY IsActive;

-- 6. Find the average balance of customers by country
SELECT Country, AVG(Balance) AS AvgBalance FROM BankCustomerChurnPrediction GROUP BY Country;

-- 7. Find the top 5 customers with the highest balance
SELECT * FROM BankCustomerChurnPrediction ORDER BY Balance DESC LIMIT 5;

-- 8. Find customers who churned and had a high balance
SELECT * FROM BankCustomerChurnPrediction WHERE Churn = 1 AND Balance > 50000;

-- 9. Count the number of churned customers per country
SELECT Country, COUNT(*) AS ChurnedCustomers FROM BankCustomerChurnPrediction WHERE Churn = 1 GROUP BY Country;

-- 10. Find the gender ratio of active customers
SELECT Gender, COUNT(*) AS Total FROM BankCustomerChurnPrediction WHERE IsActive = 1 GROUP BY Gender;

-- 11. Find the age distribution of churned vs non-churned customers
SELECT Age, Churn, COUNT(*) AS Count FROM BankCustomerChurnPrediction GROUP BY Age, Churn ORDER BY Age;

-- 12. Identify the top 3 countries with the highest churn rate
SELECT Country, (COUNT(CASE WHEN Churn = 1 THEN 1 END) * 100.0 / COUNT(*)) AS ChurnRate FROM BankCustomerChurnPrediction GROUP BY Country ORDER BY ChurnRate DESC LIMIT 3;

-- 13. Find the average balance of churned vs non-churned customers
SELECT Churn, AVG(Balance) AS AvgBalance FROM BankCustomerChurnPrediction GROUP BY Churn;

-- 14. Find the percentage of high-balance customers who churned
SELECT (COUNT(CASE WHEN Churn = 1 AND Balance > 50000 THEN 1 END) * 100.0 / COUNT(*)) AS HighBalanceChurnRate FROM BankCustomerChurnPrediction;

-- 15. Detect the most common age range among churned customers
SELECT CASE 
    WHEN Age BETWEEN 18 AND 25 THEN '18-25'
    WHEN Age BETWEEN 26 AND 35 THEN '26-35'
    WHEN Age BETWEEN 36 AND 45 THEN '36-45'
    WHEN Age BETWEEN 46 AND 55 THEN '46-55'
    ELSE '56+' END AS AgeGroup, COUNT(*) AS ChurnCount
FROM BankCustomerChurnPrediction WHERE Churn = 1 GROUP BY AgeGroup ORDER BY ChurnCount DESC;

-- 16. Find out if gender has any influence on churn rate
SELECT Gender, (COUNT(CASE WHEN Churn = 1 THEN 1 END) * 100.0 / COUNT(*)) AS ChurnRate FROM BankCustomerChurnPrediction GROUP BY Gender;

-- 17. Find the country with the highest average balance among active customers
SELECT Country, AVG(Balance) AS AvgBalance FROM BankCustomerChurnPrediction WHERE IsActive = 1 GROUP BY Country ORDER BY AvgBalance DESC LIMIT 1;

-- 18. Identify the top 3 factors influencing churn (Balance, Age, and Activity)
SELECT
    (COUNT(CASE WHEN Churn = 1 AND Balance < 20000 THEN 1 END) * 100.0 / COUNT(*)) AS LowBalanceChurnRate,
    (COUNT(CASE WHEN Churn = 1 AND Age > 50 THEN 1 END) * 100.0 / COUNT(*)) AS OlderCustomerChurnRate,
    (COUNT(CASE WHEN Churn = 1 AND IsActive = 0 THEN 1 END) * 100.0 / COUNT(*)) AS InactivityChurnRate
FROM BankCustomerChurnPrediction;

-- 19. Find the correlation between balance and churn using percentiles
SELECT CASE 
    WHEN Balance < (SELECT PERCENTILE_CONT(0.25) WITHIN GROUP (ORDER BY Balance) FROM BankCustomerChurnPrediction) THEN 'Low'
    WHEN Balance < (SELECT PERCENTILE_CONT(0.50) WITHIN GROUP (ORDER BY Balance) FROM BankCustomerChurnPrediction) THEN 'Mid'
    ELSE 'High' END AS BalanceGroup, Churn, COUNT(*) AS Count
FROM BankCustomerChurnPrediction GROUP BY BalanceGroup, Churn ORDER BY BalanceGroup;

-- 20. Find which age group is the most active and least active
SELECT CASE 
    WHEN Age BETWEEN 18 AND 25 THEN '18-25'
    WHEN Age BETWEEN 26 AND 35 THEN '26-35'
    WHEN Age BETWEEN 36 AND 45 THEN '36-45'
    WHEN Age BETWEEN 46 AND 55 THEN '46-55'
    ELSE '56+' END AS AgeGroup, COUNT(CASE WHEN IsActive = 1 THEN 1 END) AS ActiveCount
FROM BankCustomerChurnPrediction GROUP BY AgeGroup ORDER BY ActiveCount DESC;

-- 21. Running totals for customer balances over time (if timestamps exist)
SELECT CustomerID, Balance, SUM(Balance) OVER (PARTITION BY CustomerID ORDER BY LastTransactionDate) AS RunningBalance
FROM BankCustomerChurnPrediction;

-- 22. Finding high-risk customers using a complex case condition
SELECT CustomerID, Age, Balance, 
    CASE 
        WHEN Age > 50 AND Balance < 10000 AND IsActive = 0 THEN 'High Risk'
        WHEN Age BETWEEN 30 AND 50 AND Balance < 20000 THEN 'Medium Risk'
        ELSE 'Low Risk' END AS RiskLevel
FROM BankCustomerChurnPrediction;

-- 23. Churn likelihood prediction using weighted scoring
SELECT CustomerID, 
    (Age * 0.1 + Balance * 0.0001 + IsActive * -5) AS ChurnScore
FROM BankCustomerChurnPrediction ORDER BY ChurnScore DESC LIMIT 10;

-- 24. Calculating customer lifetime value (basic estimation)
SELECT CustomerID, SUM(Balance) / COUNT(*) AS CustomerLifetimeValue
FROM BankCustomerChurnPrediction GROUP BY CustomerID ORDER BY CustomerLifetimeValue DESC;

-- 25. Finding the top 5 highest earning customers assuming an estimated revenue per balance
SELECT CustomerID, Balance, (Balance * 0.02) AS EstimatedRevenue FROM BankCustomerChurnPrediction ORDER BY EstimatedRevenue DESC LIMIT 5;

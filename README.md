**Project Description**:

This project involves analyzing sales data for Atliq using MySQL and Power BI to generate key business insights. The process includes loading data into MySQL, executing queries to extract insights, and visualizing the results using Power BI.


**Data Analysis using SQL**:

Show all customer records: SELECT * FROM customers;

Show total number of customers: SELECT count(*) FROM customers;

Show transactions for Chennai market (market code for Chennai is Mark001): SELECT * FROM transactions where market_code='Mark001';

Show distinct product codes that were sold in Chennai: SELECT distinct product_code FROM transactions where market_code='Mark001';

Show transactions where currency is US dollars: SELECT * from transactions where currency="USD";

Show transactions in 2020 joined by date table: SELECT transactions., date. FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020;

Show total revenue in year 2020: SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and (transactions.currency="INR" or transactions.currency="USD");

Show total revenue in January 2020: SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and date.month_name="January" and (transactions.currency="INR" or transactions.currency="USD");

Show total revenue in Chennai in 2020: SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.market_code="Mark001";


**Data Transformation in Power BI**:

Normalized Currency: Converted USD transactions to INR using the following formula: = Table.AddColumn(#"Filtered Rows", "norm_amount", each if [currency] = "USD" or [currency] ="USD#(cr)" then [sales_amount]*75 else [sales_amount], type any)


**Dashboard**:

![image](https://github.com/user-attachments/assets/b54aa09d-6948-4470-a3d9-40e43ec6a3bd)


**Key Insights**:

Total Revenue: ₹984.87M

Total Sales Quantity: 2M units

Total Profit Margin: ₹24.7M

Top Customer: Electronics with a revenue of ₹413M

Top Zone: Central with 68.6% of total revenue

Top Product Type: Blank category with ₹469M revenue

Significant Revenue Drop: Observed a decline in revenue towards the end of 2020

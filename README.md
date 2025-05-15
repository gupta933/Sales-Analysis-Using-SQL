# 🧾 Sales Analysis using SQL

## 📁 Project Overview
This project showcases data analysis using SQL on a simulated sales dataset from a retail superstore. It aims to derive business insights by querying a PostgreSQL database named `superstore_db`. The analysis covers order behavior, customer spending, sales performance across regions, and product-based insights.

---

## 🛠 Technologies Used
- PostgreSQL
- SQL
- pgAdmin (optional)
- Excel (for data import)
- Git / GitHub

---

## 🧮 Database Structure
**Database Name**: `superstore_db`  
**Table Used**: `orders`

### Table Schema:
| Column Name     | Data Type     |
|-----------------|----------------|
| row_id          | SERIAL PRIMARY KEY |
| order_id        | VARCHAR        |
| order_date      | DATE           |
| ship_date       | DATE           |
| ship_mode       | VARCHAR        |
| customer_id     | VARCHAR        |
| customer_name   | VARCHAR        |
| segment         | VARCHAR        |
| country         | VARCHAR        |
| city            | VARCHAR        |
| state           | VARCHAR        |
| postal_code     | VARCHAR        |
| region          | VARCHAR        |
| product_id      | VARCHAR        |
| category        | VARCHAR        |
| sub_category    | VARCHAR        |
| product_name    | TEXT           |
| sales           | NUMERIC        |
| quantity        | INT            |
| discount        | NUMERIC        |
| profit          | NUMERIC        |

---

## 🔍 Key SQL Queries & Results

### 1. Total Orders
```sql
SELECT COUNT(order_id) AS total_orders FROM orders;

Unique Customers
sql
Copy
Edit
SELECT DISTINCT(customer_name) FROM orders;
📊 Result: 5 customers (Edward, Alice, Bob, Charlie, Diana)

3. Time Range of Orders
sql
Copy
Edit
SELECT MIN(order_date), MAX(order_date) FROM orders;
📆 Result: From 2022-01-01 to 2035-09-09

4. Most Ordered City
sql
Copy
Edit
SELECT city, COUNT(quantity) AS total_order
FROM orders
GROUP BY city
ORDER BY total_order DESC
LIMIT 1;
🏙️ Result: New York City — 1028 orders

5. Overall Sales and Profit
sql
Copy
Edit
SELECT SUM(sales) AS total_sales, SUM(profit) AS total_profit FROM orders;
6. Average Profit
sql
Copy
Edit
SELECT AVG(profit) FROM orders;
7. Most Profitable Category
sql
Copy
Edit
SELECT category, SUM(profit) AS total_profit
FROM orders
GROUP BY category
ORDER BY total_profit DESC
LIMIT 1;
🏆 Result: Office Supplies – ₹43,292.38

8. Highest Discounted Sub-Category
sql
Copy
Edit
SELECT sub_category, AVG(discount) AS avg_discount
FROM orders
GROUP BY sub_category
ORDER BY avg_discount DESC
LIMIT 1;
🪑 Result: Chairs – 15.4% average discount

9. Customer with Most Orders
sql
Copy
Edit
SELECT customer_name, COUNT(*) AS total_orders
FROM orders
GROUP BY customer_name
ORDER BY total_orders DESC
LIMIT 1;
🧍 Result: Edward – 1029 orders

10. Highest Spending Customer
sql
Copy
Edit
SELECT customer_name, SUM(sales) AS total_spend
FROM orders
GROUP BY customer_name
ORDER BY total_spend DESC
LIMIT 1;
💰 Result: Edward – ₹266,832.78

📈 Key Insights (Business Takeaways)
🏙️ New York City has the highest number of orders (1028).

🧍‍💼 Home Office is the segment with the most orders (1689).

📦 Top Sold Products: Office Chair, Phone Model X, Binder Set, Storage Box.

🏆 East Region has the highest profit per sale (10.07%).

💼 West Region has the highest overall sales and profit.



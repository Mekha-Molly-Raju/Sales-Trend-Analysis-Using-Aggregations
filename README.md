# Sales-Trend-Analysis-Using-Aggregations
Import online sales data into mysql 

sql queries are;

ALTER TABLE online_sales_data
CHANGE Transaction ID transaction_id INT;

ALTER TABLE online_sales_data
CHANGE Date order_date DATE;

ALTER TABLE online_sales_data
CHANGE Total Revenue total_revenue DECIMAL(10,2);

SELECT 
    EXTRACT(YEAR FROM order_date) AS year,
    EXTRACT(MONTH FROM order_date) AS month,
    SUM(total_revenue) AS total_revenue,
    COUNT(DISTINCT transaction_id) AS total_volume
FROM 
    online_sales_data
WHERE 
    order_date BETWEEN '2024-01-01' AND '2024-12-31'
GROUP BY 
    EXTRACT(YEAR FROM order_date), EXTRACT(MONTH FROM order_date)
ORDER BY 
    year ASC, month ASC
LIMIT 12;

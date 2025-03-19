

## Steps 

#### Step 1: Create S3 Table Buckets (pyiceberg-blog-bucket)
![image](https://github.com/user-attachments/assets/14a01d58-89ee-4bb5-8750-b853460b370d)


#### Step 2: create Name space 

![image](https://github.com/user-attachments/assets/17fe7751-fcde-4455-ad99-447cb9da4e9c)

#### Step 3: Create tables in S3 Table using Athena 
```
--Use the following statement to create a table in your S3 Table bucket.
CREATE TABLE `s3tablescatalog`.daily_sales (
sale_date date, 
product_category string, 
sales_amount double)
PARTITIONED BY (month(sale_date))
TBLPROPERTIES ('table_type' = 'iceberg')

/*
Next steps 1) Use the following SQL statement to insert data to your table.
INSERT INTO daily_sales
VALUES
(DATE '2024-01-15', 'Laptop', 900.00),
(DATE '2024-01-15', 'Monitor', 250.00),
(DATE '2024-01-16', 'Laptop', 1350.00),
(DATE '2024-02-01', 'Monitor', 300.00),
(DATE '2024-02-01', 'Keyboard', 60.00),
(DATE '2024-02-02', 'Mouse', 25.00),
(DATE '2024-02-02', 'Laptop', 1050.00),
(DATE '2024-02-03', 'Laptop', 1200.00),
(DATE '2024-02-03', 'Monitor', 375.00);

2) Use the following SQL statement to run a sample analytics query.
SELECT 
product_category,
COUNT(*) as units_sold,
SUM(sales_amount) as total_revenue,
AVG(sales_amount) as average_price
FROM daily_sales
WHERE sale_date BETWEEN DATE '2024-02-01' and DATE '2024-02-29'
GROUP BY product_category
ORDER BY total_revenue DESC;
*/
```

#### Step 4: Use Jupyter notebook to Query the Data with Pyiceberg and DuckDB and Trino 



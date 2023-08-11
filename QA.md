What are your risk areas? Identify and describe them.



QA Process:
Describe your QA process and include the SQL queries used to execute it.
1. to check whether primary key is actually unique and there are no duplicate values

select distinct productSKU from sales_by_sku

2. to check whether each product_SKU has been assigned unique product name

SELECT name, COUNT(*)
FROM products
GROUP BY name
HAVING COUNT(*) > 1;


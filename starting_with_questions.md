Answer the following questions and provide the SQL queries used to find the answer.

    
**Question 1: Which cities and countries have the highest level of transaction revenues on the site?**


SQL Queries:
```WITH CTE AS (
SELECT
allsn.country, allsn.city,
SUM(CASE
WHEN revenue IS NULL THEN (unit_price * units_sold)
ELSE revenue
END) AS rev_cal
FROM all_sessions AS allsn
JOIN analytics USING (full_visitor_id, visit_id)
WHERE units_sold IS NOT NULL
GROUP BY allsn.country, allsn.city
)
SELECT
country, city,
rev_cal
FROM CTE
WHERE rev_cal IS NOT NULL
ORDER BY rev_cal DESC
limit 5;```



Answer:
country				city		rev_cal
United States	United States	6891689998
United States	Sunnyvale		6603809992
United States	Chicago			2944940000
United States	Mountain View	2657360000
United States	Seattle			1905000000





**Question 2: What is the average number of products ordered from visitors in each city and country?**


SQL Queries:
```select distinct alls.country, alls.city, avg (sr.total_ordered)
from all_sessions as alls
join products as pd ON pd."productSKU" = alls."productSKU"
join sales_report as sr on pd."productSKU" = sr."productSKU"
group by alls.country, alls.city
order by avg (sr.total_ordered) DESC```




Answer: average number of products was returned





**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**


SQL Queries:
```with cte as (SELECT
country,city,
v2_product_category,
COUNT(v2_product_category) AS category_count,
RANK() OVER (PARTITION BY country ORDER BY COUNT(v2_product_category) DESC) AS
category_rank
FROM all_sessions
GROUP BY country, city, v2_product_category
ORDER BY country DESC, category_rank)

select * from CTE 
where category_rank = 1```




Answer:In most of the countries the top most selling product category is "Home/Shop by Brand/YouTube/"





**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**


SQL Queries:
```WITH ProductSalesByCountry AS (
SELECT
CASE
WHEN country = 'not set' THEN 'Unknown Country'
ELSE country
END AS country_group,
v2_product_category,
v2_product_name,
SUM(a.units_sold) AS total_units_sold
FROM all_sessions AS sessions
JOIN analytics AS a ON sessions.full_visitor_id = a.full_visitor_id
AND sessions.visit_id = a.visit_id
WHERE country <> 'not set' AND a.units_sold IS NOT NULL
GROUP BY country_group, v2_product_category, v2_product_name
),
RankedProductsByCountry AS (
SELECT
ps.*,
RANK() OVER (PARTITION BY ps.country_group ORDER BY ps.total_units_sold DESC) AS
product_rank
FROM ProductSalesByCountry ps
)
SELECT
country_group AS country,
v2_product_category,
v2_product_name,
total_units_sold,
product_rank
FROM RankedProductsByCountry
WHERE product_rank = 1
ORDER BY country_group, total_units_sold DESC;```



Answer:top selling product in each country was obtained





**Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries:
```WITH CTE AS (
SELECT
allsn.country,
SUM(CASE
WHEN revenue IS NULL THEN (unit_price * units_sold)
ELSE revenue
END) AS rev_cal
FROM all_sessions AS allsn
JOIN analytics USING (full_visitor_id, visit_id)
WHERE units_sold IS NOT NULL
GROUP BY allsn.country
)
SELECT
country,
rev_cal
FROM CTE
WHERE rev_cal IS NOT NULL
ORDER BY rev_cal DESC;```


Answer: Revenue generated from each country was returned with highest being from United States








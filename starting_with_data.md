 Question 1: What is the total number of  visitors from united states

```SQL Queries:
with cte as 
	(select distinct full_visitor_id, country
	from all_sessions
	where country = 'United States')

select count(*)
from cte```

Answer: 8118



Question 2: Find out those products whose present stock levels are less than the total quantity being ordered

SQL Queries:
select *
from products as p join sales_by_sku as s
on p."productSKU" = s."productSKU"
where p.stock_level < s.total_ordered

Answer:
"Android Infant Short Sleeve Tee Pewter"
" Youth Baseball Raglan Heather/Black"



Question 3: What is total footfall on the website during month of june in year 2017


SQL Queries:
with CTE as (
	select *
from analytics
where date between '2017-06-01' and '2017-06-30')

select sum(visit_number)
from CTE

Answer: 2927604





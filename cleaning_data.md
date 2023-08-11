What issues will you address by cleaning the data?
1. Fixing datatypes of columns
2. Removing duplicate records
3. Removing redundant, empty,irrelevant  columns
4. Scaling down large values in columns and normalising data
5. Cleaning structural issues
6. Handling missing values and data



Queries:
Below, provide the SQL queries you used to clean your data.

Fixing the datatypes of columns in each table using alter table 
query to fix datatypes

query to  find any duplicate row
```select distinct * from all_sessions```

checking for redundant columns

query to find if column contains any value or is empty
```select product_refund_amount  from all_sessions
where product_refund_amount is not null```

finding redundant columns and removing them
```select item_quantity from all_sessions
where item_quantity is not null;

ALTER TABLE all_sessions
DROP COLUMN item_quantity;

select item_revenue from all_sessions
where item_revenue is not null```

ALTER TABLE all_sessions
DROP COLUMN item_revenue

select search_keyword from all_sessions
where search_keyword is not null

ALTER TABLE all_sessions
DROP COLUMN search_keyword


--removing empty irrelevant columns
```ALTER TABLE all_sessions
DROP COLUMN product_refund_amount ```

-- explore unique values for columns
select  distinct full_visitor_id
from all_sessions


-- update product_price 
UPDATE all_sessions product_price to scale down values
SET "product_price" = "product_price"/1000000

-- cleaning structural issues: replacing 'not set' with null 
UPDATE all_sessions
SET product_variant = null
WHERE product_variant = '(not set)'

UPDATE all_sessions
SET currency_code = null
WHERE currency_code = ' '

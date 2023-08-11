# Final-Project-Transforming-and-Analyzing-Data-with-SQL

## Project/Goals
The goal of this project is to combine and practice implementing SQL skills which includes 

1. Loading data into a database
2. Extracting data from a SQL database
3. Cleaning, transforming and analyzing data
4. Developing and implementing a QA process to validate transformed data against raw data

## Process
### Step 1 loading CSV files into database
CSV files were imported into tables created in SQL database
### Step 2 Cleaning and transforming data
The data was cleaned and transformed following several actions which included fixing datatypes, removing irrelevant, redundant and duplicate data
cleaning several structural  issues, cleaning and handling missing values, looking for outliers and normalizing and scaling down values
### Step 3 Analysing the data
Queries were performed on the data to analyse it and obtain insights about the various business indices like total revenue, products ordered or left 
in stock as well as the popularity of products across different geographical locations and  also check and analyse website data from the given business
organisation
### Step 4 Implementing the QA process and spotting any QA errors
Risk areas were identified and SQL queries were executed to validate the data and check for quality assurance errors like checking for blank or null values, checking for duplicate values and ensuring the data is consistent with our expectations.

## Results
This database provides online sales data as well as maintains the information regarding it's products like number ordered, stock level etc. It gives 
analytical data about the website e.g footfall, time and length of each visit by each visitor,  how many pages were viewed, number of transactions etc.
By analyzing this data, one can get information about the various business indices like total revenue, total products ordered or left in stock as well as 
the popularity of products by different locations in which this business has presence. By querying this data we can find the countries and cities in which
business is doing good and countries where customer based has to be increased.

Also, we can find out which product category is popular in different locations and what are the most popular products across all locations as well as within 
each location e.g one of the insights was that highest levels of transaction revenue was from USA. Also in most of the countries the most popular category of products was "Home/Shop by Brand/YouTube/"

We can also find products whose present stock levels are less than the total quantity being ordered and ensure proper actions. Also, the footfall on website 
during particular month and year can be found out and comparative analysis across the years can be done. Similarly, the statistics of visitors from different locations can be found out.

## Challenges 
Loading the data was the biggest challenge as it kept giving loading errors because if we set up these datatypes the correct way straight away, then while 
loading the csv files, the datatypes do not match in many cases because they are not clean yet

Cleaning of data was very time consuming and exhaustive– fixing datatypes, lots of missing values, structural issues, redundant and empty columns etc 

Understanding and making sense of data. Identifying relation between tables

To decide what to do about missing values, some of the datatypes could not be changed to right datatype e.g time in all_sessions table cannot be changed to timestamp

Trying to use camelcase column name created lot of errors until it was resolved

Time itself was also a big challenge in this project



## Future Goals

To use materialised views instead of altering tables and retaining the original data

Give more time in understanding and eliminating missing values

Make more elaborate documentation and presentation

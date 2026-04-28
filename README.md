/*
Name: Eyerusalem Debero
Category/Vendor of Choice: Tequila

Project:
Iowa Liquor Database SWOT Analysis

Purpose:
This project analyzes tequila sales data using SQL queries.
The goal is to identify strengths, weaknesses, opportunities,
and threats related to tequila sales performance.

What I am learning in this project:
- SELECT statements
- Filtering and sorting data
- Aggregate functions
- GROUP BY and HAVING
- JOINS
- Subqueries
- Business analysis using SQL
*/

USE iowa_liquor_sales;


-- ============================================================
-- SELECT, FILTERING & SORTING
-- ============================================================

-- Q1. Create a list of all transactions for your chosen
-- [Category/Vendor] that took place in the last quarter of 2014,
-- sorted by the total sale amount from highest to lowest.
-- (Strength: Identifying high-volume peak periods).

SELECT *
FROM sales
WHERE category_name = 'TEQUILA'
	AND date BETWEEN '2014-10-01' AND '2014-12-31'
	ORDER BY total DESC;

-- Total rows: 16240
/*
What I am doing:
-- Notes:
-- I filtered the dataset to include only TEQUILA sales during Q4 (Oct–Dec) 2014.
-- I sorted the results by total revenue in descending order to highlight the highest-value transactions first.
-- This analysis helps identify peak sales activity and the most profitable transactions during the highest-performing period.*/

-- Q2. Which transactions for your [Category/Vendor] had a bottle quantity greater than 12? 
-- Display the date, store number, item description, and total amount. 
-- (Strength: Identifying bulk buyers or wholesale-style transactions). 

SELECT * FROM sales LIMIT 5;

-- First i check your table

SELECT date, store, item_description, bottles_sold, total
FROM sales
WHERE category_name = 'TEQUILA'
	AND bottles_sold > 12
	ORDER BY bottles_sold DESC;

-- Notes:
-- I filtered TEQUILA transactions where more than 12 bottles were sold.
-- This helps identify bulk buyers and high-volume purchasing behavior.
-- Sorting by bottles_sold shows the largest bulk transactions first.
-- This analysis helps understand wholesale-style demand patterns.

-- Q3. Find all products in the products_table whose item_description contains a specific 
-- keyword (e.g., 'Limited', 'Spiced'). What categories do they belong to? 
-- (Opportunity: Identifying niche product variants).

SELECT item_description, category_name
FROM products
WHERE item_description LIKE '%Spiced%';

-- Total rows 131

SELECT item_description, category_name
FROM products
WHERE item_description LIKE '%Limited%'
-- Total rows 6

-- Notes:
-- I used LIKE to search for products containing "Spiced" and "Limited".
-- "Spiced" returned 131 products (common flavored items).
-- "Limited" returned 6 products (rare/exclusive items).
-- This helps identify niche product types and compare common vs specialty products.
-- I also checked categories to see where these products belong.

-- Q4. What is the total sales revenue and the average bottle price (btl_price) for
-- your chosen [Category/Vendor]? 
-- (Strength/Baseline: Establishing the financial footprint).

SELECT 
    SUM(total) AS total_revenue,
    AVG(btl_price::numeric) AS average_bottle_price
FROM sales
WHERE category_name = 'TEQUILA';

-- T
-- Notes:
-- I calculated total revenue using SUM(total).
-- I calculated average bottle price using AVG(btl_price).
-- I converted btl_price to numeric because it was stored as a money type.
-- This gives overall revenue performance and pricing insight for tequila sales.

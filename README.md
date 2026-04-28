# Capstone_1
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

SELECT date,
       store,
       item_description,
       bottles_sold,
       total
FROM sales
WHERE category_name = 'TEQUILA'
AND date BETWEEN '2014-10-01' AND '2014-12-31'
ORDER BY total DESC;

/*
What I am doing:
-- Notes:
-- I filtered the dataset to include only TEQUILA sales during Q4 (Oct–Dec) 2014.
-- I sorted the results by total revenue in descending order to highlight the highest-value transactions first.
-- This analysis helps identify peak sales activity and the most profitable transactions during the highest-performing period.*/

-- Q2. Which transactions for your [Category/Vendor] had a bottle quantity greater than 12? 
-- Display the date, store number, item description, and total amount. 
-- (Strength: Identifying bulk buyers or wholesale-style transactions).

SELECT date,
       store,
       item_description,
       bottles_sold,
       total
FROM sales
WHERE category_name = 'TEQUILA'
AND bottles_sold > 12
ORDER BY bottles_sold DESC;

-- Notes:
-- I filtered TEQUILA transactions where more than 12 bottles were sold.
-- This helps identify bulk buyers and high-volume purchasing behavior.
-- Sorting by bottles_sold shows the largest bulk transactions first.
-- This analysis helps understand wholesale-style demand patterns.

Result
At the end of Step 1, my project is fully set up, connected to GitHub, and ready for SQL analysis work.

# SQL50ByLeetcode
Solutions for the 50 SQL questions by leetcode 

Log : 23rd september Saturday, One solved 4 remaining. 
5 problems/ day 
starting 23 september saturday. 
within 10 days I aim to wrap most of SQL50. 
So by the 3rd of October I'll be having a strong prowess in SQL Problem solving


Log : 24th spetember Sunday, 

Remember, atleast is greater than or equal to. 
Using as while assigning aliases increases performance 
#Easy but worth it 

select customer_id , count(customer_id) as count_no_trans from visits where ( visit_id not in(select visit_id from Transactions))group by customer_id ;
Solved 11 SQL Problems from SQL50. But forogt to commit the log and lost everything. 

Log : 25th September Monday, 

Database gorup019 : Assignment (009 joins)
Display module names for “PG-DAC” course.
Solution : select modules.name from course_modules inner join modules where course_modules.moduleID=modules.ID group by modules.name;

This one is valid too, but does not group by the records and has multiple entries in the column. Think on this 

select course_modules.moduleID, modules.name from course_modules inner join modules where course_modules.moduleID=modules.ID;

Assignment 009 (Joins)

Display studentID who have more than 2 phone numbers.
select studentID, count(studentID) from student_qualifications group by studentID;

Leetcode SQL50 
Average selling price (Aggregate functions) 
Looking at the result table we write the basic select statement
SELECT product_id, ____ as average_price FROM ___

AS average_price should be rounded to 2 decimal places
SELECT p.product_id, round(_____,2) as average_price

Now as evident from Explanation given, the two - price and units, required to calculate average_price are from different tables hence we need to join these tables (as product_id is common in these two tables we join on product_id)
-> update for the new test case
I have used LEFT JOIN in place of INNER JOIN, to include all the product_ids in the Prices table even if it in not present in the UnitsSold table.
SELECT p.product_id, round(_____,2) as average_price
FROM Prices p LEFT JOIN UnitsSold u
ON p.product_id = u.product_id

-> update for the new test case
Now as there can be null value for the average_price (as we are left joining tables) to handle these null values (and replace null with a 0 in result table) we can use IFNULL() function as follows
SELECT p.product_id, IFNULL(round(_____,2),0) as average_price

Now to calculate average_price, we need to add price x units of all the products (of that particulat product_id) and then divide it by the sum of all its units
This is formulated as:SUM(p.price*u.units)/SUM(u.units)
using SUM() function

For the calculation of average_price we first need to determine the price per unit based on the purchase date
Hence, modifying JOIN staement by adding the following condition
u.purchase_date BETWEEN p.Start_date and p.end_date

Now finally to have one product_id only once in the result table and calculate average_price for each product we: Group by product_id

Thus the final code becomes
SELECT p.product_id, IFNULL(round(SUM(p.price*u.units)/sum(u.units),2),0) as average_price
FROM Prices p LEFT JOIN UnitsSold u
ON p.product_id = u.product_id AND u.purchase_date BETWEEN p.Start_date and p.end_date
GROUP BY p.product_id
------------------------------------------------

Project Employees I : Ask Saleel sir about this question.

My solution : 
select p.project_id , round(sum(u.experience_years)/count(project_id) ),2) from Project p inner join Employee e  on p.employee_id=e.employee_id group by project_id;
Incomplete. Needs some brainstroming, almost there



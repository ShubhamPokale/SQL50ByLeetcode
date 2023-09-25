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



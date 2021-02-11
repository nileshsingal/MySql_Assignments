# MySql_Assignments
/* MYSQL QUESTIONS */

1.List all columns of salespeople table.
ans. Select * from salespeople;
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------
2.list all customers with a rating of 100.
ans.select * from customer where rating=100;
------------------------------------------------------------------------------------------------------------------------------------------------------------------------
3.find all records in the customer table with null values in city column.
ans.select * from customer where city='null'; ::displays empty set.
----------------------------------------------------------------------------------------------------------------------------------------------------------------------
4. Find the largest order taken by each salesperson on each date.
ans. select a.onum,max(a.amt),a.odate,a.cnum,b.snum from orders a,customer b where a.cnum=b.cnum group by b,snum,a.odate;
----------------------------------------------------------------------------------------------------------------------------------------------------------------------
5. Arrange the Orders table by descending customer number.
ans. select * from orders order by cnum desc;
------------------------------------------------------------------------------------------------------------------------------------------------------------------------
6. Find which salespeople currently have orders in the Orders table.
ans.select a.onum,a.amt,a.odate,a.cnum,b.snum,b.sname from orders a,customer b where a.cnum=b.cnum group by b.snum,a.odate;
   select a.onum,a.amt,a.odate,a.cnum,b.snum from orders a,customer b where a.cnum=b.cnum group by b.snum;
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------
7. List names of all customers matched with the salespeople serving them.
ans. select a.sname,a.city,b.cname from salespeople a,customer b where a.snum=b.snum;
------------------------------------------------------------------------------------------------------------------------------------------------------------------------
8. Find the names and numbers of all salespeople who had more than one customer.
ans.select a.snum,b.sname,count(*) as cust_count from customer a, salespeople b where a.snum=b.snum group by a.snum;
------------------------------------------------------------------------------------------------------------------------------------------------------------------------
9. Count the orders of each of the salespeople and output the results in descending order.
ans: select b.snum,c.sname,count(*) as order_count from orders a,customer b,salespeople c where a.cnum=b.snum and b.snum=c.snum group by snum;
----------------------------------------------------------------------------------------------------------------------------------------------------------------------  
10. List the Customer table if and only if one or more of the customers in the Customer table are
located in San Jose.
ans: select * from customer where (select count(*) from customer where city='san jose')>1;
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------
11. Match salespeople to customers according to what city they lived in.
ans. select a.sname,b.cname,b.city from salespeople a, customer b where a.snum=b.snum and a.city=b.city;
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------
12. Find the largest order taken by each salesperson.
ans: select a.sname,a.snum,b.onum,b.amt from salespeople a,orders b,customer c where a.snum=c.snum and c.cnum=b.cnum group by sname;
---------------------------------------------------------------------------------------------------------------------------------------------------------------
13. Find customers in San Jose who have a rating above 200.
ans. select * from customer where rating>=200 and city='san jose';
--------------------------------------------------------------------------------------------------------------------------------------------------------------------
14. List the names and commissions of all salespeople in London.
ans.select distinct sname,comm,city from salespeople where city='london';
---------------------------------------------------------------------------------------------------------------------------------------------------------------------
15. List all the orders of salesperson Motika from the Orders table.
ans. select a.sname,b.onum,b.amt from salespeople a,orders b,customer c where a.snum=c.snum and c.cnum=b.cnum and sname='motika';
---------------------------------------------------------------------------------------------------------------------------------------------------------------------
16. Find all customers with orders on October 3.
ans.select * from orders where odate='1996-03-10'; 
----------------------------------------------------------------------------------------------------------------------------------------------------------------------
17. Give the sums of the amounts from the Orders table, grouped by date, eliminating all those
dates where the SUM was not at least 2000.00 above the MAX amount.
ans: select odate,sum(amt) from orders group by odate;
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------
18. Select all orders that had amounts that were greater than at least one of the orders from
October 6.
ans: select * from orders where amt>(amt(odate='1996-06-10' order by cnum;-----------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------
19. Write a query that uses the EXISTS operator to extract all salespeople who have customers
with a rating of 300.
ans. select sname,snum from salespeople where exists(select rating from customer where rating=100);
------------------------------------------------------------------------------------------------------------------------------------------------------------------------
20. Find all pairs of customers having the same rating.
ans: select * from rating order by rating;
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------
21. Find all customers whose CNUM is 1000 above the SNUM of Serres.
ans: select a.cnum,a.cname,b.snum,b.sname from customer a,salespeople b where b.snum+1000=a.cnum;
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------
22. Give the salespeople�s commissions as percentages instead of decimal numbers.
ans. select sname,comm*100 as comm from salespeople;
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------
23. Find the largest order taken by each salesperson on each date, eliminating those MAX orders
which are less than $3000.00 in value.
ans: select b.sname,c.odate,c.onum,c.amt from customer a,salespeople b,orders c where a.snum=b.snum and a.cnum=b.cnum and amt>=3000;
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------
24. List the largest orders for October 3, for each salesperson.
ans. select b.sname,c.odate,c.onum,c.amt from customer a,salespeople b,orders c where a.snum=b.snum and a.cnum=b.cnum and c.odate='1996-03-10' order by c.amt desc;
------------------------------------------------------------------------------------------------------------------------------------------------------------------------- 
25. Find all customers located in cities where Serres (SNUM 1002) has customers.
ans: select a.snum,a.sname,b.cname,b.city from salespeople a,customer b where a.snum=b.snum and b.snum=1002;
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------
26. Select all customers with a rating above 200.00.
ans: select * from customer where rating>200;
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------
27. Count the number of salespeople currently listing orders in the Orders table.
ans: select a.sname,c.onum from salespeople a, customer b,orders c where a.snum=b.snum and b.cnum=c.cnum group by a.sname;
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------
28. Write a query that produces all customers serviced by salespeople with a commission above
    12%. Output the customer�s name and the salesperson�s rate of commission.
ans: select a.cname,b.sname,b.comm from customer a,salespeople b where a.snum=b.snum and b.comm>'0.12';
--------------------------------------------------------------------------------------------------------------------------------------------------------------------- 
29. Find salespeople who have multiple customers.
ans:  select a.sname,b.cname from salespeople a,customer b where a.snum=b.snum limit 4;
------------------------------------------------------------------------------------------------------------------------------------------------------------------
30. Find salespeople with customers located in their city.
ans: select a.sname,a.city,b.cname from salespeople a,customer b where a.city=b.city;
---------------------------------------------------------------------------------------------------------------------------------------------------------------------
31. Find all salespeople whose name starts with �P� and the fourth character is �l�.
ans: select * from salespeople where sname like 'p__l';
------------------------------------------------------------------------------------------------------------------------------------------------------------------------
32. Write a query that uses a subquery to obtain all orders for the customer named Cisneros.
Assume you do not know his customer number.
ans: select a.cname,b.onum from customer a, orders b where a.cnum=b.cnum and a.cname='cisneros' order by a.cname;
----------------------------------------------------------------------------------------------------------------------------------------------------------------------- 
33. Find the largest orders for Serres and Rifkin.
ans: select a.sname,max(c.amt) as amt from salespeople a,customer b,orders c where a.snum=b.snum and b.cnum=c.cnum and sname='serres' or sname='rifkin' group by a.snum;
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------
34. Extract the Salespeople table in the following order : SNUM, SNAME, COMMISSION, CITY.
ans: select snum,sname,comm,city from salespeople:
------------------------------------------------------------------------------------------------------------------------------------------------------------------------
35. Select all customers whose names fall in between �A� and �G� alphabetical range.
ans: select a.sname,b.cname from salespeople a, customer b where sname and cname like 'a%g';
----------------------------------------------------------------------------------------------------------------------------------------------------------------------
36. Select all the possible combinations of customers that you can assign.
ans:- select a.cname,b.cname from customer a,customer b where a.snum=b.snum;
-------------------------------------------------------------------------------------------------------------------------------------------------------------------
37. Select all orders that are greater than the average for October 4.
ans:select * from orders where amt>(select avg(amt) from orders where odate='1996-04-10');
--------------------------------------------------------------------------------------------------------------------------------------------------------------------
38. Write a select command using a corelated subquery that selects the names and numbers of all
customers with ratings equal to the maximum for their city.
ans: select cnum,cname,rating from customer where rating>=(select max(rating) from customer); 
--------------------------------------------------------------------------------------------------------------------------------------------------------------------
39. Write a query that totals the orders for each day and places the results in descending order.
ans: selectsum(amt) as amt,odate from orders group by odate order by amt desc;
---------------------------------------------------------------------------------------------------------------------------------------------------------------------
40. Write a select command that produces the rating followed by the name of each customer in
San Jose.
ans: select cname,city,rating from customer where city='san jose';
----------------------------------------------------------------------------------------------------------------------------------------------------------------------
41. Find all orders with amounts smaller than any amount for a customer in San Jose.
ans: select a.cname,b.onum,b.amt from customer a,orders b where amt<(a.cname where city='sanjose') order by cname; 
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------
42. Find all orders with above average amounts for their customers.
ans: select a.cname,b.amt from customer a,orders b where a.cnum=b.cnum and amt>(select avg(amt) as amt from orders)group by cname;
------------------------------------------------------------------------------------------------------------------------------------------------------------------------
43. Write a query that selects the highest rating in each city.
ans: select city,max(rating) as rating from customer group by city;

44. Write a query that calculates the amount of the salesperson�s commission on each order by a
customer with a rating above 100.00.
ans: select a.amt,a.cnum,b.rating,b.snum,c.sname,c.comm,a.amt*c.comm from orders a,customer b,salespeople c where a.cnum=b.cnum and b.snum=c.snum and b.rating>100;

45. Count the customers with ratings above San Jose�s average.
ans: select * from customer where rating>(select avg(rating) from customer where city='san jose';

46. Write a query that produces all pairs of salespeople with themselves as well as duplicate rows
with the order reversed.
ans: select a.sname,b.sname from salespeople a,salespeople b where a.snum=b.snum;
------------------------------------------------------------------------------------------------------------------------------------------------------------------------- 
47. Find all salespeople that are located in either Barcelona or London.
ans: select * from salespeople where city='barcelona' or 'london';
------------------------------------------------------------------------------------------------------------------------------------------
48. Find all salespeople with only one customer.
ans: select a.sname,a.snum from salespeople a,(select snu,count(*) as cust_count from customer group b snum having cust_count=1) b where a.snum=b.snum;
---------------------------------------------------------------------------------------------------------------------------------------------------------- 
49. Write a query that joins the Customer table to itself to find all pairs of customers served by a
single salesperson.
ans: select a.cname,b.cname,c.sname from customer a,customer b,salespeople c where a.snum=b.snum and a.snum=c.snum;
-------------------------------------------------------------------------------------------------------------------------------------------------------------
50. Write a query that will give you all orders for more than $1000.00
q:- select * from orders where amt>1000;
-----------------------------------------------------------------------------------------------------------------
51. Write a query that lists each order number followed by the name of the customer who made
that order.
q:- select a.onum,b.cname from orders a,customer b where a.cnum=b.cnum;
-----------------------------------------------------------------------------------------------------------------
52. Write 2 queries that select all salespeople (by name and number) who have customers in their
cities who they do not service, one using a join and one a corelated subquery. Which solution
is more elegant?
q:- select a.sname,a.snum,b.city from orders a left outer join customer b on a.snum=b.snum;
------------------------------------------------------------------------------------------------------------------
53. Write a query that selects all customers whose ratings are equal to or greater than ANY (in the
SQL sense) of Serres�?
q:- select a.sname,b.rating from salespeople a,customer b where a.snum=b.snum;
    select * from customers where rating>=200;
-------------------------------------------------------------------------------------------------------------------
54. Write 2 queries that will produce all orders taken on October 3 or October 4.
q:- select * from orders where odate='1996-03-10' or odate='1996-04-10';
    select * from orders from odate='1996-03-10'; select * from orders where odate='1996-04-10';
-------------------------------------------------------------------------------------------------------------------
55. Write a query that produces all pairs of orders by a given customer. Name that customer and
eliminate duplicates.
q:- select a.cname,b.onum from customer a,orders b where a.cnum=b.cnum;
-------------------------------------------------------------------------------------------------------------------
56. Find only those customers whose ratings are higher than every customer in Rome.
q:- select * from customer where rating>(select max(rating) from customer where city='Rome');
-------------------------------------------------------------------------------------------------------------------
57. Write a query on the Customers table whose output will exclude all customers with a rating <=
100.00, unless they are located in Rome.
ans:- select * from customer where (rating<=100 and city='Rome') or rating>100;
---------------------------------------------------------------------------------------------------------------------
58. Find all rows from the Customers table for which the salesperson number is 1001.
q:- select * from customer where snum=1001;
--------------------------------------------------------------------------------------------------------------------
59. Find the total amount in Orders for each salesperson for whom this total is greater than the
amount of the largest order in the table.
ans:- select * from customers where rating>200;
-------------------------------------------------------------------------------------------------------------------------
60. Write a query that selects all orders save those with zeroes or NULLs in the amount field.
ans:- select * from orders;
--------------------------------------------------------------------------------------------------------------------------------
61. Produce all combinations of salespeople and customer names such that the former precedes
the latter alphabetically, and the latter has a rating of less than 200.
ans:- select a.sname,b.cname,b.rating from salespeople a,customer b where a.snum=b.snum and b.rating>200;
---------------------------------------------------------------------------------------------------------------------------------------------
62. List all Salespeople�s names and the Commission they have earned.
ans:- select a.sname,sum(a.comm*c.amt) as commision from sales people a,customer b,orders c where a.snum=b.snum and b.cnum=c.cnum group ny a.comm;
---------------------------------------------------------------------------------------------------------------------------------------------------------
63. Write a query that produces the names and cities of all customers with the same rating as
Hoffman. Write the query using Hoffman�s CNUM rather than his rating, so that it would still be
usable if his rating changed.
ans:- select cname,city from customer where rating=(select rating from customer where cnum='2001');
-------------------------------------------------------------------------------------------------------------------------------------------------------------
64. Find all salespeople for whom there are customers that follow them in alphabetical order.
ans:- select a.sname,b.cname from salespeople a,customer b where a.snum=b.snum order by a.sname limit 2;
------------------------------------------------------------------------------------------------------------------------------------------------------------------
65. Write a query that produces the names and ratings of all customers of all who have above
average orders.
ans:- select a.cname,b.amt from customer a,orders b where a.cnum=b.cnum and amt>(select avg(amt) as amt from orders)group by cname;
----------------------------------------------------------------------------------------------------------------------------------------------------------------
66. Find the SUM of all purchases from the Orders table.
ans:- select sum(amt) from orders;
----------------------------------------------------------------------------------------------------------------------------------------------------------------- 
67. Write a SELECT command that produces the order number, amount and date for all rows in
the order table.
ans:- select onum,amt,odate from orders;
-------------------------------------------------------------------------------------------------------------------------------------------------------------------
68. Count the number of nonNULL rating fields in the Customers table (including repeats).
ans:- select count(distinct rating) from customer;
--------------------------------------------------------------------------------------------------------------------------------------------------------------------
69. Write a query that gives the names of both the salesperson and the customer for each order
after the order number.
ans:- select a.cname,b.sname,c.onum from customer a,salespeople b,orders c where a.snum=b.snum and a.cnum=c.cnum;
--------------------------------------------------------------------------------------------------------------------------------------------------------------------
70. List the commissions of all salespeople servicing customers in London.
ans:- select a.sname,a.comm,b.city.b.cname from salespeople a,customer b where a.snum=b.snum and b.city='London';
---------------------------------------------------------------------------------------------------------------------------------------------------------------------
71. Write a query using ANY or ALL that will find all salespeople who have no customers located in
their city.
ans:- select a.sname,a.city,b.cname,b.city as cus_city from salespeople a,customer b where a.snum=b.snum and a.city!=b.city;
--------------------------------------------------------------------------------------------------------------------------------------------------------------------
72. Write a query using the EXISTS operator that selects all salespeople with customers located in
their cities who are not assigned to them.
ans:- select a.sname,a.city,b.cname,b.city as cus_city from salespeople a,customer b where a.snum=b.snum and a.city!=b.city;
---------------------------------------------------------------------------------------------------------------------------------------------------------------------
73. Write a query that selects all customers serviced by Peel or Motika. (Hint : The SNUM field
relates the two tables to one another.)
ans:- select a.sname,b.cname from salespeople a,customer b where a.snum=b.snum and (a.sname='Peel' or a.sname='Motika');
---------------------------------------------------------------------------------------------------------------------------------------------------------------------
74. Count the number of salespeople registering orders for each day. (If a salesperson has more
than one order on a given day, he or she should be counted only once.)
ans:- select b.sname,c.onum,c.odate,count(distinct b.sname) from customer a,salespeople b,orders c where a.snum=b.snum and a.cnum=c.cnum group by c.odate;
----------------------------------------------------------------------------------------------------------------------------------------------------------------------
75. Find all orders attributed to salespeople in London.
ans:- select b.sname,b.city,c.onum from customer a,salespeople b,orders c where a.snum=b.snum and a.cnum=c.cnum and b.city='London';
----------------------------------------------------------------------------------------------------------------------------------------------------------------------
76. Find all orders by customers not located in the same cities as their salespeople.
ans:- select a.sname,a.city,b.cname,b.city as cus_city from salespeople a,customer b where a.snum=b.snum and a.city!=b.city;
----------------------------------------------------------------------------------------------------------------------------------------------------------------------
77. Find all salespeople who have customers with more than one current order.
ans:- select e.sname,d.count_cus from salespeople e,(select count(c.onum) as count_cus from salespeople a,customer b,orders c where a.snum=b.snum and b.cnum=c.cnum group by a.sname) d where e.sname=d.sname and count_cus>1;
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
78. Write a query that extracts from the Customers table every customer assigned to a
salesperson who currently has at least one other customer (besides the customer being
selected) with orders in the Orders table.
ans:- select e.sname,d.count_cus from salespeople e,(select count(c.onum) as count_cus from salespeople a,customer b,orders c where a.snum=b.snum and b.cnum=c.cnum group by a.sname) d where e.sname=d.sname and count_cus>1;
79. Write a query that selects all customers whose names begin with �C�.
ans:- select * from customer where cname like 'c%';
--------------------------------------------------------------------------------------------------------------------------------------------------------------------
80. Write a query on the Customers table that will find the highest rating in each city. Put the output
in this form : for the city (city) the highest rating is : (rating).
ans:- select city, max(rating) from customer group by city;
----------------------------------------------------------------------------------------------------------------------------------------------------------------------
81. Write a query that will produce the SNUM values of all salespeople with orders currently in the
Orders table (without any repeats).
ans:- select b.snum,b.sname,c.onum from customer a,salespeople b,orders c where a.snum=b.snum and a.cnum=c.cnum group by b.snum;
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------
82. Write a query that lists customers in descending order of rating. Output the rating field first,
followed by the customer�s names and numbers.
ans:- select rating,cname,cnum from customer order by rating desc;
---------------------------------------------------------------------------------------------------------------------------------------------------------------------
83. Find the average commission for salespeople in London.
ans:- select city,avg(comm) from salespeople where city='London' group by city;
---------------------------------------------------------------------------------------------------------------------------------------------------------------------
84. Find all orders credited to the same salesperson who services Hoffman (CNUM 2001).
ans:- select a.cname,b.sname,c.onum from customer a,salespeople b,orders c where a.snum=b.snum and a.cnum=c.cnum and a.cnum='2001';
----------------------------------------------------------------------------------------------------------------------------------------------------------------------
85. Find all salespeople whose commission is in between 0.10 and 0.12 (both inclusive).
ans:- select * from salespeople where comm between '0.10' and '0.12';
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------
86. Write a query that will give you the names and cities of all salespeople in London with a
commission above 0.10.
ans:- select sname,city,comm from salespeople where (city='London' and comm>'0.10');
----------------------------------------------------------------------------------------------------------------------------------------------------------------------
87. What will be the output from the following query?
SELECT * FROM ORDERS
where (amt < 1000 OR NOT (odate = 10/03/1996 AND cnum >
2003));
ans:- table 
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------
88. Write a query that selects each customer�s smallest order.
ans:- select a.cnum,a.cname,min(b.amt) from customer a,orders b where a.cnum=b.cnum group by a.cname order by min(b.amt);
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------
89. Write a query that selects the first customer in alphabetical order whose name begins with G.
ans:- select * from customer where cname like 'g%' orde by cname;
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------
90. Write a query that counts the number of different nonNULL city values in the Customers table.
ans:- select count(distinct city) from customer;
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------
91. Find the average amount from the Orders table.
ans:- select avg(amt) from orders;
------------------------------------------------------------------------------------------------------------------------------------------------------------------------
92. What would be the output from the following query?
SELECT * FROM ORDERS
WHERE NOT (odate = 10/03/96 OR snum > 1006) AND amt >=
1500);
ans:- syntax error near ')'
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------
93. Find all customers who are not located in San Jose and whose rating is above 200.
ans:- select * from customer where (city!='San Jose' and rating>200);
------------------------------------------------------------------------------------------------------------------------------------------------------------------------
94. Give a simpler way to write this query :
SELECT snum, sname city, comm FROM salespeople
WHERE (comm > + 0.12 OR comm < 0.14);
ans:- select * from salespeople where (comm>0.12 or comm<0.14);
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------
95. Evaluate the following query :
SELECT * FROM orders
WHERE NOT ((odate = 10/03/96 AND snum > 1002) OR amt > 2000.00);
ans:- unknown snum column in where clause.
----------------------------------------------------------------------------------------------------------------------------------------------------------------------
96. Which salespersons attend to customers not in the city they have been assigned to?
ans:- select a.sname,a.city,b.cname,b.city as cus_city from salespeople a,customer b where a.snum=b.snum and a.city!=b.city;
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------
97. Which salespeople get commission greater than 0.11 are serving customers rated less than
250?
ans:- select a.sname,a.comm,b.cname,b.rating from salespeople a,customer b where a.snum=b.snum and (a.comm>0.12 and b.rating<250);
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------
98. Which salespeople have been assigned to the same city but get different commission
percentages?
ans:- select *,comm*100 from salespeople where city='London';
--------------------------------------------------------------------------------------------------------------------------------------------------------------------
99. Which salesperson has earned the most by way of commission?
ans:- select a.cname,b.sname,b.comm,sum(c.amt)*b.comm as k from customer a,salespeople b,orders c where a.snum=b.snum and a.cnum=c.cnum group by b.sname order by k desc;
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
100.Does the customer who has placed the maximum number of orders have the maximum rating?
ans:- select a.rating,b.onum,count(*) as orders_count from customer a,orders b where a.cnum=b.cnum group by a.cnum order by a.rating desc;
--------------------------------------------------------------------------------------------------------------------------------------------------
101.Has the customer who has spent the largest amount of money been given the highest rating?
ans:- select a.rating,a.cnum,b.onum,b.amt from customer a,orders b where a.cnum=b.cnum order by b.amt desc;
---------------------------------------------------------------------------------------------------------------------------------------------------
102.List all customers in descending order of customer rating.
ans:- select * from customer order by desc;
--------------------------------------------------------------------------------------------------------------------------------------------------
103.On which days has Hoffman placed orders?
ans:- select a.cname,b.onum,b.odate from customer a,orders b where a.cnum=b.cnum and a.cname='Hoffman';
---------------------------------------------------------------------------------------------------------------------------------------------------
104.Do all salespeople have different commissions?
ans:- select * from salespeople;
-------------------------------------------------------------------------------------------------------------------------------------------------------
105.Which salespeople have no orders between 10/03/1996 and 10/05/1996?
ans:- select b.sname,c.odate from customer a,salespeople b,orders c where a.snum=b.snum and a.cnum=c.cnum and odate not between '1996-03-10' and '1996-05-10';
------------------------------------------------------------------------------------------------------------------------------------------------------------------
106.How many salespersons have succeeded in getting orders?
ans:- select b.sname,c.onum,c.odate from customer a,salespeople b,orders c where a.snum=b.snum and a.cnum=c.cnum;
-----------------------------------------------------------------------------------------------------------------------------------------------------------------
107.How many customers have placed orders?
ans:- select a.cname,a.cnum,b.onum,b.odate,count(*) as cust_count from customer a,orders b where a.cnum=b.cnum group by cname;
      select count(distinct cnum)from orders; 
------------------------------------------------------------------------------------------------------------------------------------------------------------------
108.On which date has each salesperson booked an order of maximum value?
ans:- select b.sname,c.odate,c.onum,max(c.amt) from customer a,salespeople b,orders c where a.snum=b.snum and a.cnum=c.cnum group by b.sname;
--------------------------------------------------------------------------------------------------------------------------------------------------------------------
109.Who is the most successful salesperson?
ans:- select b.snum,c.sname,sum(a.amt) as totalsalesbySP from orders a,customer b,salespeople c where a.cnum=b.cnum and b.snum=c.snum group by b.snum order by 
      totasalesbySP desc;
---------------------------------------------------------------------------------------------------------------------------------------------------------------------
110.Who is the worst customer with respect to the company?
ans:- select a.cnum,b.cname,sum(a.amt) as totalspend from orders a,cutomer b where a.cnum=b.cnum group by a.cnum order by totalspend limit 1;
---------------------------------------------------------------------------------------------------------------------------------------------------------------------
111.Are all customers not having placed orders greater than 200 totally been serviced by
salespersons Peel or Serres?
ans:- select a.cnum,b.sname,c.amt from customer a,salespeople b,orders c where a.snum=b.snum and a.cnum=c.cnum and amt>200 limit 5;
---------------------------------------------------------------------------------------------------------------------------------------------------------------------
112.Which customers have the same rating?
ans:- select * from customer order by rating;
---------------------------------------------------------------------------------------------------------------------------------------------------------------------
113.Find all orders greater than the average for October 4th.
ans:- select odate,avg(amt) from orders where odate!='1996-04-10' group by odate;
--------------------------------------------------------------------------------------------------------------------------------------------------------------------
114.Which customers have above average orders?
ans:- select * from orders where amt> (select avg(amt)from oreders);
--------------------------------------------------------------------------------------------------------------------------------------------------------------------
115.List all customers with ratings above San Jose�s average.
ans:- select cnum,rating from customer where rating>(select avg(rating) from customer where city='sanjose');
--------------------------------------------------------------------------------------------------------------------------------------------------------------------
116.Select the total amount in orders for each salesperson for whom the total is greater than the
amount of the largest order in the table.
ans:- select b.sname,c.onum,sum(c.amt) from customer a,salespeople b,orders c where a.snum=b.snum and a.cnum=c.cnum group by b.sname order by sum(c.amt) limit 1;
--------------------------------------------------------------------------------------------------------------------------------------------------------------------
117.Give names and numbers of all salespersons who have more than one customer.
ans:- select sname,snum from salespeople where snum in(select snum from customer group by snum having count(snum)>1);
---------------------------------------------------------------------------------------------------------------------------------------------------------------------
118.Select all salespersons by name and number who have customers in their city whom they
don�t service.
ans:- select a.sname,a.city,b.cname,b.city as cus_city from salespeople a,customer b where a.snum=b.snum and a.city!=b.city;
---------------------------------------------------------------------------------------------------------------------------------------------------------------------
119.Which customers� rating should be lowered?
ans:- select a.cnum,b.cname,b.rating,sum(a.amt) as totalspend from orders a,customer b where a.cnum=b.cnum group by cnum order by totalspend;
---------------------------------------------------------------------------------------------------------------------------------------------------------------------
120.Is there a case for assigning a salesperson to Berlin?
ans:- select a.sname,b.city from salespeople a,customer b where a.snum=b.snum;
----------------------------------------------------------------------------------------------------------------------------------------------------------------------
121.Is there any evidence linking the performance of a salesperson to the commission that he or
she is being paid?
ans:- select b.snum,c.sname,sum(a.amt) as totalsalesbySP,sum(amt)*c.comm from orders a,customer b,salespeople c where a.cnum=b.cnum and b.snum=c.snum group by b.snum
      oredr by totalsalesbySP desc;
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------
122.Does the total amount in orders by customer in Rome and London exceed the commission
paid to salespersons in London and New York by more than 5 times?
ans:- select (select sum(a.amt*c.comm) as totalsales from orders a,customer b,salespeople c where a.cnum=b.cnum and b.snum=c.snum and (c.city='London' or c.city='New York'))
      as x,(select sum(a.amt) from orders a,customer b where a.cnum=b.cnum and (b.city='Rome' or b.city='London')) as y;
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
123.Which is the date, order number, amt and city for each salesperson (by name) for the
maximum order he has obtained?
ans:- select odate,onum,amt,city from orders where amt=(select max(amt)from orders);
----------------------------------------------------------------------------------------------------------------------------------------------------------------------
124.Which salesperson(s) should be fired?
ans:- select a.cname,b.sname from customer a,salespeople b,orders c where a.sname=b.sname and a.cnum=c.cnum;
--------------------------------------------------------------------------------------------------------------------------------------------------------------------
125.What is the total income for the company?
ans:- select sum(amt) from orders;
